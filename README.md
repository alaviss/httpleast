# httpleast

[![Test Matrix](https://github.com/disruptek/httpleast/workflows/CI/badge.svg)](https://github.com/disruptek/httpleast/actions?query=workflow%3ACI)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/disruptek/httpleast?style=flat)](https://github.com/disruptek/httpleast/releases/latest)
![Minimum supported Nim version](https://img.shields.io/badge/nim-1.5.1%2B-informational?style=flat&logo=nim)
[![License](https://img.shields.io/github/license/disruptek/httpleast?style=flat)](#license)
[![Matrix](https://img.shields.io/badge/chat-on%20matrix-brightgreen)](https://matrix.to/#/#disruptek:matrix.org)

'twas beauty that killed the beast

## Defines

Most importantly,

- `--define:leastThreads=N` set number of threads to `N`.

And then,

- `--define:leastQueue=none`

This uses the specified number of threads, each running their own server and
creating and dispatching client continuations in a thread-local eventqueue.

- `--define:leastQueue=loony`

This uses a single thread accepting clients and setting up a continuation for
each one; the continuation is pushed into a `LoonyQueue` that is serviced by
the specified number of threads. Each thread runs as many continuations as
remain in the running state, competing to receive new continuations from the
queue.

- `--define:leastRecycle=true` reduces continuation allocs.

When using Loony, recycle completed continuations via a multi-threaded queue;
when using no queue, recycle completed continuations with a thread-local stack.

Also...

- `--define:leastPort=8080` listen on port 8080.
- `--define:leastAddress="127.1"` listen on given interface.
- `--define:leastDebug=true` adds extra event queue debugging.
- `--define:leastKeepAlive=false` turns off connection reuse.

## License
MIT
