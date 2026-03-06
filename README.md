# i3Aero [![Build](https://github.com/oleksandr-antonenko/AeroSpace/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/oleksandr-antonenko/AeroSpace/actions/workflows/build.yml)

<img src="./resources/Assets.xcassets/AppIcon.appiconset/icon.png" width="40%" align="right">

**i3Aero** is a fork of [AeroSpace](https://github.com/nikitabobko/AeroSpace) that adds **i3-style auto-tiling** (spiral/dwindle layout) and a **master-stack** command to the macOS tiling window manager.

## Features

### Auto-tiling (spiral/dwindle layout)

Automatically alternates between horizontal and vertical splits based on the focused window's dimensions — just like [i3's autotiling](https://github.com/nwg-piotr/autotiling).

```toml
# ~/.aerospace.toml
auto-tile = true
```

When a window is wider than it is tall, the next window splits horizontally. When taller than wide, it splits vertically. This creates a natural spiral layout as you open more windows.

### Master-stack command

Arranges windows in a master-stack layout: the focused window takes 70% of the screen width, and the remaining windows are spiral-tiled on the right.

```toml
# Make focused window the master
alt-enter = 'master-stack'

# Cycle through windows as master
alt-space = 'master-stack --cycle'
```

| Flag | Description |
|------|-------------|
| `--cycle` | Rotate the next window (by window ID order) into the master position |
| `--workspace <workspace>` | Target a specific workspace |

## Installation

Download the latest release from [Releases](https://github.com/oleksandr-antonenko/AeroSpace/releases), unzip, and move `AeroSpace.app` to `/Applications`.

After launch, grant accessibility permissions in **System Settings > Privacy & Security > Accessibility**.

### Build from source

```bash
git clone https://github.com/oleksandr-antonenko/AeroSpace.git
cd AeroSpace
./build-release.sh --codesign-identity -
./install-from-sources.sh --dont-rebuild
```

## Example config

```toml
# ~/.aerospace.toml
after-login-command = []
after-startup-command = []
start-at-login = true

enable-normalization-flatten-containers = true
enable-normalization-opposite-orientation-for-nested-containers = true

# Enable i3-style spiral auto-tiling
auto-tile = true

[gaps]
inner.horizontal = 10
inner.vertical = 10
outer.left = 10
outer.bottom = 10
outer.top = 10
outer.right = 10

[mode.main.binding]
alt-enter = 'master-stack'
alt-space = 'master-stack --cycle'

alt-h = 'focus left'
alt-j = 'focus down'
alt-k = 'focus up'
alt-l = 'focus right'

alt-shift-h = 'move left'
alt-shift-j = 'move down'
alt-shift-k = 'move up'
alt-shift-l = 'move right'

alt-1 = 'workspace 1'
alt-2 = 'workspace 2'
alt-3 = 'workspace 3'

alt-shift-1 = 'move-node-to-workspace 1'
alt-shift-2 = 'move-node-to-workspace 2'
alt-shift-3 = 'move-node-to-workspace 3'
```

## Upstream

Based on [nikitabobko/AeroSpace](https://github.com/nikitabobko/AeroSpace). Full documentation for the base features:

- [AeroSpace Guide](https://nikitabobko.github.io/AeroSpace/guide)
- [AeroSpace Commands](https://nikitabobko.github.io/AeroSpace/commands)
- [AeroSpace Goodies](https://nikitabobko.github.io/AeroSpace/goodies)

Videos:
- [YouTube 91 sec Demo](https://www.youtube.com/watch?v=UOl7ErqWbrk)
- [YouTube Guide by Josean Martinez](https://www.youtube.com/watch?v=-FoWClVHG5g)

## macOS compatibility table

|                                                                                | macOS 13 (Ventura) | macOS 14 (Sonoma) | macOS 15 (Sequoia) | macOS 26 (Tahoe) |
| ------------------------------------------------------------------------------ | ------------------ | ----------------- | ------------------ | ---------------- |
| Binary runs on ...                                                             | +                  | +                 | +                  | +                |
| Debug build from sources supported on ...                                      |                    | +                 | +                  | +                |
| Release build from sources supported on ... (Requires Xcode 26+)              |                    |                   | +                  | +                |

## Related projects

- [nikitabobko/AeroSpace](https://github.com/nikitabobko/AeroSpace) (upstream)
- [Amethyst](https://github.com/ianyh/Amethyst)
- [yabai](https://github.com/koekeishiya/yabai)
- [nwg-piotr/autotiling](https://github.com/nwg-piotr/autotiling) (i3 autotiling inspiration)
