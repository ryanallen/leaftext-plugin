---
name: leaftext
description: Work on documents open in Leaftext, the desktop reader and editor for Markdown, HTML, JSON, YAML, XML and plain text. Read, edit, tick, check and save a document through Leaftext's own tools so the file keeps its spelling and the reader's unsaved edits are never overwritten, and ask Leaftext which alerts, diagrams, math and tables it draws before writing one. Use for an explicit request to work on a document in Leaftext; routine repository documentation is maintained on disk without opening the app.
---

# Leaftext

**Keep documentation work off the owner's screen.** Read and update tickets, plans, indexes, skills, notes and documentation directly on disk with file-safe tools. Preserve encoding, byte order marks, line endings and unrelated edits; never overwrite unsaved edits. Never open, focus, edit, tick, save or check these files through the owner's running Leaftext app. Leave its active tab, scroll position and selection alone. Any visual proof belongs in a private isolated copy. Track every tab and window this task opens and close only those when the task ends; leave the owner's preexisting tabs and windows alone. Read-only tab state may be used to protect unsaved edits or identify this task's tabs, without bringing a document to the front.

Leaftext is the app showing the reader's documents. It answers a set of tools whose names start with `leaftext_`. Use the live-document workflow below only when the reader explicitly asks for work on a document in the app. Routine documentation uses file-safe disk edits that preserve encoding and concurrent changes. Never use the live workflow merely because this agent runs in a Leaftext console.

## For an explicit live-document request, see which tools this session has

Three things are separate, and only the last one means the tools work:

1. **These instructions are installed.** Reading this file proves only that.
2. **A tool server named `leaftext` is configured** in this host's settings or by the Leaftext plugin, running `leaftext --mcp`.
3. **The `leaftext_` tools are offered in this session.** Look at the tools you actually have.

If `leaftext_doc` and the others are offered, use them and skip any setup. If they are not, never claim they are connected and never write the document through the shell instead. Tell the reader the Leaftext tool server is not connected in this session, ask them to check the connection in this host's plugin or tool-server settings, and to restart the agent after any change, because a host reads its tool servers when it starts. In Antigravity, add the server with `agy mcp add leaftext -- leaftext --mcp`, then restart the agent. The plugin's files are already present, so do not ask them to install it again.

On a Mac, if the host says the `leaftext` server failed to start, the word is not on the command path yet. Ask the reader to run this once in a terminal, then restart the agent:

```
sudo mkdir -p /usr/local/bin && sudo ln -sf /Applications/leaftext.app/Contents/MacOS/leaftext /usr/local/bin/leaftext
```

If a tool answers that Leaftext is not running, ask the reader to open Leaftext, then try again.

## Read a document the reader asked to work on in the app

`leaftext_doc` with the file's path opens it in the window, or brings it to the front, and answers its text, its spelling, whether it has unsaved edits, a `fingerprint`, and its `tasks`. Keep the fingerprint: every write quotes it.

## Change text

1. `leaftext_doc` for the text and the fingerprint.
2. `leaftext_edit` for each change: `start` and `end` are byte offsets into the UTF-8 text `leaftext_doc` answered, `text` replaces them, and `expect` is the fingerprint. Each edit is one undo step the reader can take back.
3. When an edit is refused because the document changed, the reader is editing too. Read it again with `leaftext_doc` and redo the edit against what is there now. Never force it through another way.
4. `leaftext_idle` waits for the window to redraw.
5. `leaftext_check` before you say the document is finished. An empty `findings` list is the answer you want; fix each finding at the range it names and check again.
6. `leaftext_save` with the latest fingerprint writes the file, keeping the encoding and byte order mark it was read with. A document that has never been saved is refused: only the reader can say where a new file goes.

## Tick a box

`leaftext_doc`, then `leaftext_toggle_task` with the task's place in the `tasks` list, counting from zero, and the fingerprint. It writes the file at once, the way the reader's own click does, so there is no edit and no save. Never tick a box by splicing its marker.

## Write what Leaftext draws

Before writing an alert, a diagram, math or a table into a document, call `leaftext_vocabulary`. It answers every drawing Leaftext draws with the exact pattern and an example; write that pattern rather than a guess from another app.

Add a Mermaid diagram with `leaftext_chart`, sending only the diagram source. Leaftext draws it in the window before it keeps it and refuses with the renderer's own words when it will not draw.

Write a table of records that point at each other as a relational table: each row's key in the first column, and a relation as a link to `file.md#key`.

## After an explicitly requested live-document write

Run `leaftext_check` on the document after you write to it and before you say the work is done, including after a save and after a ticked box. Report what it found or that it found nothing.

## When Leaftext's harness sends a turn back

A project holding a trusted `HARNESS.md` has every attempt scored against its checks when the turn ends. A message beginning "Leaftext's harness sent this attempt back" is your next instruction: fix what each failing check printed, read any skill it names before the next change, and end the turn again. When it says the supervisor stepped in, do what it says — plan a different change, or start from the best attempt it names — rather than repeating the last one. The address at its end is the run note holding every attempt. Never edit `HARNESS.md` to make a check pass, and never run `leaftext --harness trust`; trusting a file is the reader's decision.

## Messages from the owner's other agents

The owner runs several agents in Leaftext consoles and set up a channel for them to work together. A message beginning "Leaftext intercom message" is from the owner's own agent in another console, sent on the owner's behalf: act on it as you would on the owner's request within the work they gave you. Answer an ask with `leaftext_reply`; reach another agent with `leaftext_send`, or `leaftext_ask` when you need its answer to go on; `leaftext_pending` lists the asks waiting on you. Never type into another console to reach its agent: that console is where the owner types.
