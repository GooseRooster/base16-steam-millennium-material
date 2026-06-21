# tinted-material-millennium

A [tinty](https://github.com/tinted-theming/tinty) template that maps a Base16 color scheme to Steam Millennium's [Material-Theme](https://github.com/tinted-theming/material-theme) skin, replacing [matugen](https://github.com/InioX/matugen) with the active tinty palette.

## How it works

Material-Theme loads its color palette from `css/main/colors/matugen.css` when the "Matugen" color option is selected in `skin.json`. This template generates a drop-in replacement for that file using Base16 color variables, so any tinty scheme drives the Steam UI colors.

## Color mapping

| Material token group | Base16 source |
|---|---|
| Backgrounds (surface, containers) | `base00` → `base03` |
| On-surface text | `base04`, `base05` |
| Primary accent | `base0D` (blue) |
| Secondary accent | `base0E` (purple/magenta) |
| Tertiary accent | `base0C` (cyan) |
| Error | `base08` (red) |
| Inverse surfaces | `base06`, `base07` |

## Setup

### 1. Enable Matugen color mode in Material-Theme

In `skin.json`, set the **Color** option to `"Matugen"`.

### 2. Add to your tinty `config.toml`

```toml
[[items]]
path = "https://github.com/GooseRooster/tinted-material-millennium"
name = "tinted-material-millennium"
themes-dir = "output"
hook = "cp \"$TINTY_THEME_FILE_PATH\" ~/.steam/steam/steamui/skins/Material-Theme/css/main/colors/matugen.css"
supported-systems = ["base16"]
```

### 3. Apply a scheme

```sh
tinty apply base16-dracula
```


## Notes

- `--hue-rotate` is set to `0deg` (neutral). The default Material-Theme value is `220deg`, which shifts icon hues toward blue. Adjust in the mustache template if desired.
- Light Base16 schemes will work but are untested — the Material-Theme skin defaults to dark mode.
