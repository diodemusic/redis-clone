# redis-clone

A Redis clone written in C from scratch, as a vehicle for learning C and low-level
programming (sockets, memory management, data structures, event loops, protocols).

## How to work with me

1. I write and understand every line of code myself. Do not write code for me. If I do
   not understand something we will learn it together until I do, and only then will I
   type it myself. You explain and review; you do not produce the code. This includes
   the Makefile and any scripts — if it ends up in the project, I typed it.

2. I work in vertical slices: one thin end-to-end feature at a time, that compiles clean
   and demonstrably works against a real client (`redis-cli` or `nc`) before moving on.
   No half-finished horizontal layers.

3. One slice = one conversation. Each slice is built in its own fresh chat. Because a new
   conversation starts with no memory of the previous one, `NOTES.md` is the ONLY thing
   that carries state between slices. So:
   - At the START of a conversation, read `NOTES.md` first to learn the current slice,
     the decisions made, the code conventions in play, and any deferred TODOs.
   - When a slice is complete AND I confirm it is verified against a real client, YOU do
     the bookkeeping before we stop: update `NOTES.md` (mark the slice DONE; record key
     decisions, naming conventions, gotchas, and anything the next conversation needs;
     set "Next up"), then tell me plainly that the conversation is complete and ready to
     be closed so I can open a fresh one for the next slice.
   - Never start a second slice in the same conversation. Finish, bookkeep, hand off.

## Orientation (so you don't break the project)

- `NOTES.md` is the cross-conversation handoff file. Treat it as the project's memory.
- Source code lives in `src/`. Built artifacts and the binary go in `build/` and are
  never committed knowledge — only `NOTES.md` is.
- This is a learning project: prefer hand-rolled over libraries. Standard C library and
  POSIX (sockets, etc.) only — no external dependencies unless a slice explicitly
  decides otherwise and records why in `NOTES.md`.
- Compile with warnings on (`-Wall -Wextra`) and treat warnings as things to understand,
  not silence.
