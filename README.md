# Songs Content (MDX Format)

This directory contains all Prabhat Samgiita songs in MDX format for easy editing.

## Quick Start

### Adding a new song

Create a new file `XXXX.mdx` (e.g., `0693.mdx`):

```mdx
---
id: 693
date: 1982-10-16
language: bengali
audio: https://app.psbot.eu/play_audio/693/
---

## Original

Your original text here
Line 1
Line 2

Empty lines between stanzas are preserved

## English

Your English translation here

## Russian

Your Russian translation here
```

### Building songs.json

After adding/editing MDX files, run:

```bash
npm run mdx:build
```

This will convert all MDX files to `data/songs.json`.

## File Format

### Frontmatter (metadata)

**Note**: The song ID is automatically extracted from the filename (e.g., `0692.mdx` → ID 692), so you don't need to specify it in frontmatter.

```yaml
---
date: 1982-10-15     # Optional: Composition date (YYYY-MM-DD)
language: bengali    # Optional: bengali|sanskrit|english|hindi (auto-detected if omitted)
audio: https://...   # Optional: Audio URL
---
```

### Sections

Use markdown headers (`##`) to define sections:

- `## Original` - Original text in Bengali/Sanskrit (required)
- `## English` - English translation (optional)
- `## Russian` - Russian translation (optional)

### Text Formatting

- **Paragraph breaks**: Just leave empty lines between stanzas
- **Line breaks**: Single line breaks are preserved
- **Whitespace**: Leading/trailing whitespace is automatically trimmed

Example:

```mdx
## Original

Stanza 1 line 1
Stanza 1 line 2

Stanza 2 line 1
Stanza 2 line 2
```

This will be converted to JSON with proper `\n` newlines between lines and `\n\n` between stanzas.

## Workflow

### 1. Start from JSON (first time)

If you already have `data/songs.json`, export to MDX:

```bash
npm run mdx:export
```

This creates MDX files from existing JSON (skips existing files).

To overwrite existing MDX files:

```bash
npm run mdx:export:force
```

### 2. Edit MDX files

Just edit the `.mdx` files in your text editor. No special tools needed!

### 3. Build JSON

Convert MDX files back to JSON:

```bash
npm run mdx:build
```

This is automatically run during `npm run build`.

### 4. Development

During development:

```bash
npm run dev
```

**Note**: Changes to MDX files require running `npm run mdx:build` to update `data/songs.json` before they appear in the app.

## Tips

1. **File naming**: Use 4-digit numbers with leading zeros: `0001.mdx`, `0692.mdx`, etc.

2. **Copy & Paste**: Just paste text from ChatGPT or any source directly into MDX sections. The script automatically:
   - Normalizes whitespace
   - Preserves paragraph structure
   - Removes extra blank lines

3. **Quick Add**: Create a new `.mdx` file, paste content, run `npm run mdx:build`. Done!

4. **Version Control**: MDX files are much easier to read and diff in Git compared to JSON.

5. **Batch Editing**: Use VS Code's multi-file search/replace to edit multiple songs at once.

## Scripts Reference

| Command | Description |
|---------|-------------|
| `npm run mdx:build` | Convert all MDX → JSON |
| `npm run mdx:export` | Convert JSON → MDX (skip existing) |
| `npm run mdx:export:force` | Convert JSON → MDX (overwrite all) |
| `python3 scripts/mdx_to_json.py` | Direct MDX → JSON conversion |
| `python3 scripts/json_to_mdx.py` | Direct JSON → MDX conversion |

## Example: Adding Song #693

1. Create `content/songs/0693.mdx`:

```mdx
---
date: 1982-10-16
language: bengali
---

## Original

[Paste original text here]

## English

[Paste English translation here]

## Russian

[Paste Russian translation here]
```

**Note**: No need to specify `id: 693` - it's automatically extracted from filename `0693.mdx`!

2. Build JSON:

```bash
npm run mdx:build
```

3. Done! Song is now available in the app.
