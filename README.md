# goose-firejail

0. Don't ever ever ever sent to remote AI any personal data.
1. Don't ever ever run any MCP's unprotected (it may `rm -rf` your `/home` theoretically).

So.

### Install `goose`

```bash
yay -S goose-desktop
```

or

```bash
yay -S codename-goose # cli-only version, `-bin' exists as well
```

### Using firejail

CLI version:

```bash
#!/bin/bash
export HTTP_PROXY=http://127.0.0.1:9099
export http_proxy=http://127.0.0.1:9099
export HTTPS_PROXY=http://127.0.0.1:9099
export https_proxy=http://127.0.0.1:9099
export SOCKS_PROXY=socks5://127.0.0.1:9099
export socks_proxy=socks5://127.0.0.1:9099
export NO_PROXY=localhost,127.0.0.1
export no_proxy=localhost,127.0.0.1

mkdir -p $HOME/shit/goose
cd $HOME/shit/goose
firejail --noprofile \
  --whitelist=$HOME/.config/goose \
  --whitelist=$HOME/.local/share/goose \
  --whitelist=$HOME/shit/goose \
  --whitelist=$HOME/.config/Goose  \
  --whitelist=$HOME/.local/share/uv \
  --whitelist=$HOME/.cache/uv \
  --whitelist=$HOME/.local/share/pnpm \
  --whitelist=$HOME/.librewolf goose "$@"
```

```bash
#!/bin/bash
export HTTP_PROXY=http://127.0.0.1:9099
export http_proxy=http://127.0.0.1:9099
export HTTPS_PROXY=http://127.0.0.1:9099
export https_proxy=http://127.0.0.1:9099
export SOCKS_PROXY=socks5://127.0.0.1:9099
export socks_proxy=socks5://127.0.0.1:9099
export NO_PROXY=localhost,127.0.0.1
export no_proxy=localhost,127.0.0.1

mkdir -p $HOME/shit/goose
cd $HOME/shit/goose
firejail --noprofile \
  --whitelist=$HOME/.config/goose \
  --whitelist=$HOME/.local/share/goose \
  --whitelist=$HOME/shit/goose \
  --whitelist=$HOME/.config/Goose  \
  --whitelist=$HOME/.local/share/uv \
  --whitelist=$HOME/.cache/uv \
  --whitelist=$HOME/.local/share/pnpm \
  --whitelist=$HOME/.librewolf goose-desktop --proxy-server="socks5://127.0.0.1:9099" "$@"

```

### Add `.goosehints`

```bash
echo 'Before attempting to run any command write a small Markdown explanation of it, like "Now I will run `some_command`, this command will do such task" - USE MARKDOWN TO MARK CRUCIAL PARTS OF EXPLANATION.' >> ~/.config/goose/.goosehints
```

### Manual Mode

CLI:

```
$ goose configure

┌   goose-configure
│
◇  What would you like to configure?
│  Goose Settings
│
◇  What setting would you like to configure?
│  Goose Mode
│
◇  Which Goose mode would you like to configure?
│  Smart Approve Mode
│
└  Set to Smart Approve Mode - modifications require approval

```

GUI:

Bottom-right corner -> button with small circles -> "Smart"

Each time it asks press "Allow Once".

### config file

```
GOOSE_PROVIDER: openai
OPENAI_HOST: https://text.pollinations.ai
OPENAI_BASE_PATH:
OPENAI_CUSTOM_HEADERS: private=true
GOOSE_MODE: smart_approve
GOOSE_MODEL: openai-large
```
