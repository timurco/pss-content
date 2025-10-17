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

2. Done! Song is now available in the app.


## TODO

Parse all the songs from: [Sarkarverse](https://sarkarverse.org/wiki/List_of_songs_of_Prabhat_Samgiita)