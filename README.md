# Text Normalizer

A lightweight web tool for cleaning up messy text formatting, primarily designed for normalizing Claude Code responses that come with excessive indentation and wrapped continuation lines.

## What it does

Paste text like this:

```
Your retain is set to days: 1 with mode: motion - this means Frigate only keeps segments
  where motion was actually detected. If there was no motion during those hours, the segments
  get cleaned up even though the day hasn't passed yet. Try changing mode: motion to mode: all
   on alerts retain and see if recordings stick around longer.

  Also worth checking - open your record stream URL directly in VLC
  (rtsp://root:xxxxx@192.168.1.115/axis-media/media.amp?) to make sure it's actually working.
  That trailing ? with no parameters looks a bit odd, your camera might not be sending the
  record stream properly.
```

Get clean output:

```
Your retain is set to days: 1 with mode: motion - this means Frigate only keeps segments where motion was actually detected. If there was no motion during those hours, the segments get cleaned up even though the day hasn't passed yet. Try changing mode: motion to mode: all on alerts retain and see if recordings stick around longer.

Also worth checking - open your record stream URL directly in VLC (rtsp://root:xxxxx@192.168.1.115/axis-media/media.amp?) to make sure it's actually working. That trailing ? with no parameters looks a bit odd, your camera might not be sending the record stream properly.
```

- Strips common leading indentation
- Joins wrapped continuation lines back into paragraphs
- Collapses excessive whitespace into single spaces
- Preserves paragraph breaks
- Auto-normalizes on paste

## Run

```bash
docker run -d -p 3677:3677 eduard256/text-normalizer:latest
```

Then open `http://localhost:3677` in your browser.

## Keyboard shortcuts

- `Ctrl+Enter` -- normalize
- `Ctrl+Shift+C` -- copy output

## Build from source

```bash
git clone https://github.com/eduard256/text-normalizer.git
cd text-normalizer
docker build -t text-normalizer .
docker run -d -p 3677:3677 text-normalizer
```
