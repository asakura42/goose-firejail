# goose-firejail

0. Don't ever ever ever sent to remote AI any personal data.
1. Don't ever run any MCP's unprotected (it may `rm -rf` your `/home` theoretically).

So.

### Using firejail

```bash
firejail --noprofile --whitelist=$HOME/shit/goose --whitelist=$HOME/.config/goose --whitelist=$HOME/.local/share/goose --whitelist=$HOME/.config/Goose  --whitelist=$HOME/.local/share/uv --whitelist=$HOME/.cache/uv --whitelist=$HOME/.local/share/pnpm goose-desktop
```

```bash
firejail --noprofile --whitelist=$HOME/shit/goose  --whitelist=$HOME/.config/goose --whitelist=$HOME/.local/share/goose --whitelist=$HOME/.config/Goose  --whitelist=$HOME/.local/share/uv --whitelist=$HOME/.cache/uv --whitelist=$HOME/.local/share/pnpm goose-desktop
```

### Add `.goosehints`

```bash
echo 'Before attempting to run any command write a small Markdown explanation of it, like "Now I will run `some_command`, this command will do such task" - USE MARKDOWN TO MARK CRUCIAL PARTS OF EXPLANATION.' >> ~/.config/goose/.goosehints
```

### Manual Mode

CLI:

```
$ goose configure

This will update your existing config file
  if you prefer, you can edit it directly at /home/net/.config/goose/config.yaml

┌   goose-configure
│
◇  What would you like to configure?
│  Goose Settings
│
◇  What setting would you like to configure?
│  Goose Mode
│
◇  Which Goose mode would you like to configure?
│  Approve Mode
│
└  Set to Approve Mode - all tools and modifications require approval
```

GUI:

Bottom-right corner -> button with small circles -> "Manual"

Each time press "Allow Once".
