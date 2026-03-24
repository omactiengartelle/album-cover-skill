# AI Album Cover Generator

Generate stunning album cover art from a text description using AI. Powered by the Neta talesofai API — get back a direct image URL in seconds.

---

## Install

**Via npx skills:**
```bash
npx skills add omactiengartelle/album-cover-skill
```

**Via ClawHub:**
```bash
clawhub install album-cover-skill
```

---

## Usage

```bash
# Basic — uses the built-in default prompt
node albumcover.js

# Custom prompt
node albumcover.js "dark synthwave aesthetic, neon purple cityscape, retro 80s vibes"

# Square cover (default)
node albumcover.js "jazz trio, warm tones, vintage vinyl feel" --size square

# Portrait format
node albumcover.js "epic orchestral album, stormy sky, dramatic" --size portrait

# With a reference image UUID
node albumcover.js "same style but winter theme" --ref abc123-uuid-here

# Pass token explicitly
node albumcover.js "lo-fi beats cover art" --token YOUR_TOKEN_HERE
```

---

## Options

| Flag | Values | Default | Description |
|------|--------|---------|-------------|
| `--size` | `square`, `portrait`, `landscape`, `tall` | `square` | Output image dimensions |
| `--style` | `anime`, `cinematic`, `realistic` | `cinematic` | Visual style (informational) |
| `--ref` | `<picture_uuid>` | — | Reference image UUID for style inheritance |
| `--token` | `<token>` | — | Override token resolution |

### Size dimensions

| Size | Width | Height |
|------|-------|--------|
| `square` | 1024 | 1024 |
| `portrait` | 832 | 1216 |
| `landscape` | 1216 | 832 |
| `tall` | 704 | 1408 |

---

## Token Setup

The script resolves your API token in this order:

1. `--token` CLI flag
2. `NETA_TOKEN` environment variable
3. `~/.openclaw/workspace/.env` — line matching `NETA_TOKEN=...`
4. `~/developer/clawhouse/.env` — line matching `NETA_TOKEN=...`

**Recommended setup:**
```bash
echo "NETA_TOKEN=your_token_here" >> ~/.openclaw/workspace/.env
```

Or export it in your shell profile:
```bash
export NETA_TOKEN=your_token_here
```

---

## Output

The script prints a single direct image URL to stdout on success, making it easy to pipe into other tools:

```bash
node albumcover.js "cyberpunk album cover, rain, neon" | pbcopy   # copy URL
node albumcover.js "jazz" | xargs curl -o cover.jpg               # download
```

---

## Default Prompt

When no prompt is provided, the script uses:

> professional album cover art, dramatic lighting, bold composition, music album aesthetic, high contrast, visually striking, suitable for streaming platforms

---

Built with Claude Code · Powered by Neta
