---
date: '2026-10-14'
draft: false
title: 'Trello Obsidian Research Sync'
categories: ['Productivity']
---

## Introduction
I keep track of my research topics on a Trello board, and I write the actual research in [Obsidian](https://obsidian.md/).<br/>
For a while this worked fine, but the two kept drifting apart. I would add a card to Trello and forget to open a note for it, or finish a topic in Obsidian and leave the card sitting on the board for weeks. Renaming something meant renaming it twice.<br/>
So I wrote a small Obsidian plugin that keeps the board and the vault in sync for me. In this article I go over what it does and how it works.

## The Idea
Every card on the board gets a matching note in the vault, named `<Card Name> Research Document.md`, and a folder for images and other files under `Assets/<Card Name>`.<br/>
After that, the vault decides the state of things. If I move a note into the archive folder, the card gets archived on Trello. If I rename the note, the card gets renamed. I almost never have to open Trello except to add new topics.

## Setup
The plugin is built with esbuild:

```shell
npm install
npm run build
```

This produces `main.js`. To install it, I copy `main.js`, `manifest.json` and `styles.css` into `<vault>/.obsidian/plugins/trello-research-sync/` and enable it under Community Plugins.

The settings tab asks for five things:

* Trello API key
* Trello API token
* The ID of the board to sync
* The folder where active notes go (blank means the vault root)
* The archive folder (`Archive` by default)

The key and token come from Trello's developer page. The board ID is the short string in the board's URL.

## Creating Notes From Cards
The sync runs when Obsidian finishes loading, again every 30 seconds, and whenever I run the "Sync Trello Cards as Research Documents" command.<br/>
Each run pulls every card on the board, including archived ones, with a single request:

```typescript
const url = `https://api.trello.com/1/boards/${boardId}/cards?key=${apiKey}&token=${apiToken}&fields=name,closed&filter=all`;
```

For every open card, the plugin checks whether a note already exists in either the active folder or the archive folder. If it exists in neither, it creates an empty one.<br/>
Card names can contain characters that aren't allowed in file names, like `/` or `?`. Those get stripped out, and in that case the plugin writes the original card name into the new note so it isn't lost:

```typescript
const wasModified = sanitizedCardName !== card.name;
const initialContent = wasModified ? `# ${sanitizedCardName}\n\n${card.name}\n` : '';
```

The asset folder is handled the same way. If a card doesn't have one yet, it gets created, and this also fills in folders for older notes that were made before I added this feature.

## Archiving
This is the part I use the most. When I'm done with a topic, I right click the note and pick "Archive File". The plugin moves the note into the archive folder, moves its asset folder along with it, and closes the card on Trello. "Unarchive File" does the opposite and reopens the card.

Dragging the note into the archive folder by hand does the same thing. The plugin listens for vault rename events and checks whether the file only changed folders:

```typescript
const isMoveOnly = oldDir !== newDir && oldRawFileName === file.name.replace(/\.md$/, '');
```

If the note moved from the active folder to the archive folder and the card is still open, the card is closed, and the other way around.

I also move files outside of Obsidian sometimes, with the file explorer or a sync tool, and Obsidian doesn't always report those as renames. To cover that, every sync also checks where each note actually is and fixes the card if it doesn't match:

```typescript
if (isFileInArchive && !isFileInActive && !card.closed) {
    card.closed = true;
    await this.updateCardClosedStatus(card.id, true);
    ...
}

if (isFileInActive && !isFileInArchive && card.closed) {
    card.closed = false;
    await this.updateCardClosedStatus(card.id, false);
    ...
}
```

One thing to be aware of is that the vault wins here. If I archive a card from inside Trello while its note is still in the active folder, the next sync will reopen it. That's on purpose, since I wanted one place that decides, but it can be confusing the first time it happens.

## Renaming and Deleting
Renaming a note renames the card. The plugin strips the ` Research Document` suffix from the new file name, sends the rest to Trello as the card's new name, and renames the asset folder to match.

Deleting a note archives the card instead of deleting it. Archived cards can be restored from Trello, while a deleted card is gone for good, and I didn't want a stray delete in Obsidian to lose anything on the board.

## The Dashboard
There's a ribbon icon and an "Open Dashboard View" command that open a panel in the right sidebar. It shows:

* How many notes are active and how many are archived, with word counts for each
* A bar showing the ratio of active to archived notes
* Two lists, active and archived, with the word count next to each note. Clicking a name opens the note.

This is the top of the dashboard on my vault right now:

![trelloDashboard](/img/trello_dashboard.png)

It refreshes after every sync, rename and delete, so it stays current without me clicking anything. Mostly I use it to see which topics have barely been started. A note with 40 words in it next to one with 4,000 makes that pretty clear.

## Limitations
It's a personal tool and it shows in a few places:

* Only one board is supported.
* Card descriptions, checklists, labels and due dates are ignored. The plugin only cares about the name and whether the card is archived.
* The API key and token are saved in plain text in the plugin's `data.json` inside the vault, and they're sent as URL query parameters, which is how Trello's API works. If your vault is synced somewhere or shared, keep that in mind.
* Polling every 30 seconds is simple but not very efficient. Trello has webhooks, but they need a publicly reachable endpoint, which doesn't really fit a desktop app.

None of these have bothered me enough to fix yet. The plugin does the job I wrote it for, which was to stop keeping two lists by hand.
