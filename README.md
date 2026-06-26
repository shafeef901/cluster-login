# clogin

Simple Interactive CLI cluster login selector.

## Setup

```bash
cp clusters.conf.example clusters.conf
# Edit clusters.conf with your clusters
chmod +x clogin
```

## Usage

```bash
./clogin
```

Navigate with arrow keys (or j/k), press Enter to connect, q to quit.

## tmux by default

Connections are wrapped in a persistent remote `tmux` session so they survive
network drops — reconnecting just reattaches. To detach without killing the
session, press `Ctrl-b` then `d`.

**Each connection gets its own session.** On connect, `clogin` attaches to the
first session with no client attached; if there isn't one, it creates a fresh,
uniquely-named session (`vega`, `vega-2`, `vega-3`, …). So:

- Opening a second terminal gives you a second, independent session — not a
  mirror of the first.
- Reconnecting after a network drop reattaches to the session you left (it no
  longer has a client) instead of spawning yet another one.

Override with environment variables:

```bash
CLOGIN_TMUX=0 ./clogin              # disable tmux wrapping for this run
CLOGIN_TMUX_SESSION=main ./clogin   # force ONE fixed shared session — every
                                    # connection mirrors the same terminal
```

## Config

`clusters.conf` format (one per line):

```
name|ssh command
```

Override config location with `CLOGIN_CONF` env var.

## Install

Symlink to somewhere on your PATH:

```bash
ln -s "$(pwd)/clogin" ~/.local/bin/clogin
```
