# redis-clone notes

Cross-conversation handoff file for the vertical-slice workflow (one slice = one
conversation). A new conversation starts cold, so this file is the project's entire
memory: current state, decisions, code conventions, gotchas, deferred work. Read it
first; keep it current.

## Current state

- Last completed: **nothing yet — project just initialized** (CLAUDE.md and this file
  exist; no source code, no Makefile).
- Next up: **Slice 1 - a TCP server that accepts one connection and replies `+PONG\r\n`
  to anything it receives** (verify with `redis-cli -p <port> ping` or
  `echo PING | nc localhost <port>`). This forces the first lap through: sockets
  (`socket`/`bind`/`listen`/`accept`), `read`/`write`, a `main()`, and a Makefile —
  one thin end-to-end path from client to response.

## Decisions made so far

- Learning project in C: hand-rolled everything, C standard library + POSIX only.
- Build via a hand-written Makefile (to be created in slice 1), warnings on
  (`-Wall -Wextra`).
- Layout: source in `src/`, binary/objects in `build/`.
- Kieran types every line; Claude explains and reviews only (see CLAUDE.md).

## Conventions in play

- (none yet — slice 1 will establish naming, formatting, and error-handling style;
  record them here when it does)

## Gotchas / deferred TODOs

- (none yet)

## Roadmap sketch (loose, re-plan freely)

1. TCP server replying +PONG to one connection  ← next
2. Parse real RESP protocol (the `*1\r\n$4\r\nPING\r\n` framing) instead of assuming
3. Handle multiple commands per connection (loop, partial reads)
4. SET / GET with a hand-rolled hash table
5. Multiple concurrent clients (event loop with poll/epoll/kqueue — this is the big
   low-level payoff)
6. DEL / EXISTS / KEYS, then expiry (TTL)
7. Persistence, replication, ... (distant)
