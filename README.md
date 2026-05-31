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

Each cluster gets a session named after it (e.g. `vega`). Override with
environment variables:

```bash
CLOGIN_TMUX=0 ./clogin              # disable tmux wrapping for this run
CLOGIN_TMUX_SESSION=main ./clogin   # use a fixed session name instead
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
