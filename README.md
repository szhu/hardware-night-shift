# Hardware Night Shift

Night Shift for macOS external displays that works with Color Filters (like Grayscale).

## Why?

On macOS external displays, Night Shift doesn't work when Color Filters are active. When you enable Grayscale or other color filters, Night Shift becomes useless because it applies before the filter -- you will always only see gray!

iOS and macOS built-in displays get this right: When you turn on Night Shift and Color Filters, you get a warm grayscale.

This tool replicates that behavior for external displays by using [BetterDisplay](https://github.com/waydabber/BetterDisplay)'s hardware RGB gain controls, so our makeshift Night Shift applies _after_ Color Filters.

## Requirements

- [BetterDisplay](https://github.com/waydabber/BetterDisplay)
- A keyboard shortcut app to trigger the three apps, like one of these:
  - [Spark](https://www.shadowlab.org/softwares/spark.php)
  - [BetterTouchTool](https://folivora.ai/)
  - [Quicksilver](https://qsapp.com/)
  - [Supercharge](https://sindresorhus.com/supercharge)

## Usage

Set up three keyboard shortcuts (similar to volume controls):

- **Night Shift 1.app**: Toggle on/off (remembers last warmth level)
- **Night Shift 2.app**: Decrease warmth
- **Night Shift 3.app**: Increase warmth

There are 16 warmth levels, just like macOS volume controls.

## How it works

Each app is a bash script that:

1. Reads/writes warmth state using macOS `defaults` system
2. Converts warmth level to RGB hardware gains
3. Applies via BetterDisplay URL scheme

All three scripts share the same logic, differing only in their final action (toggle/decrease/increase).
