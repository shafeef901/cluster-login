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
