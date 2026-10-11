# SVG Themer

A utility for Omnis Studio 12 that transforms an SVG file into an icon compatible with Omnis dynamic coloring. Unlike the built-in tool, this library lets you choose which original colors to keep or remove, select a preview color, and export the result.

## Features

- Detects simple `fill` and `stroke` colors and lets you choose which declarations to remove.
- Provides independent options for making `fill` and `stroke` dynamic through `var(--om-tint-color)`.
- Exports the transformed SVG. The preview color is not embedded in the file.

## Requirements

- Omnis Studio 12.0 (compatibility with version 11.2 may be possible).

## Limitations

The transformation handles simple `fill="…"` and `stroke="…"` declarations. Support for CSS, classes, gradients, and other complex SVG coloring methods is not documented here.
