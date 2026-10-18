# skhd-config

skhd-zig hotkeys for yabai on macOS, with shared modules and separate stack/BSP profiles.

- `skhdrc` loads app, script and service bindings from `modules/shared/`, plus navigation, manipulation and layout bindings through `modules/active`.
- `modules/active` is a relative symlink to `stack` by default. Hyper+T/P call Fish `yp stack` / `yp bsp` to apply the yabai profile, swap the link and reload skhd.
- Stack: Hyper+J/K cycles windows, Hyper+Space focuses the recent window, Shift+Alt+J/K reorders the stack. BSP uses Hyper+H/J/K/L for directional focus and Shift+Alt+H/J/K/L to swap windows.
- Right Shift launches apps: A Ghostty, G Chrome, V Vivaldi, F Finder and D Discord.

Requires [skhd-zig](https://github.com/jackielii/skhd.zig) with Accessibility access, [yabai](https://github.com/aharoJ/yabai), jq and Fish. The external Fish helpers `yp` and `_swap_skhd_profile` handle profile switching; Hyper+Q calls `yr` to restart both services. Those helpers live in [the Fish config](https://github.com/aharoJ/config/tree/main/fish/internal/yabai). Hyper+G also needs the local script `~/.scripts/ghostty_toggle_blur.py` and Python 3.

Back up your current config, then run from this repo:

```sh
mkdir -p ~/.config/skhd
cp skhdrc ~/.config/skhd/
cp -R modules ~/.config/skhd/
```

The service reads `~/.config/skhd/skhdrc`. With skhd already running, `skhd -r` reloads it. Keep `modules/active` as a symlink when copying or changing profiles.

Numbered backups are available as tags `v0.3.0` and `v0.4.0`; `v0.5.0` marks this configuration. Older versions are single-file configs with their original bindings and dependencies.

MIT. See [LICENSE](LICENSE).
