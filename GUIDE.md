# Dependencies

| Program Name | 	Role        |	Package Name |
| ------------ | ------------ | ------------ |
| Meson        | Build System |	meson        |
| Ninja        | Build System | ninja        |

# Listed Stuff

# 1. Programs

## Compositor
- Wayfire

```
git clone https://github.com/WayfireWM/wf-install
cd wf-install
./install.sh --prefix /opt/wayfire --stream master
```

## Wayfire Plugins
- Pixdecor

```
git clone https://github.com/soreau/pixdecor.git
cd pixdecor
PKG_CONFIG_PATH=/opt/wayfire/lib/pkgconfig meson setup build --prefix=/opt/wayfire
ninja -C build
ninja -C build install
```

## Components
| Role                    | Program Name | Description             | Package Name |
| ----------------------- | ------------ | ----------------------- | ------------ |
| Bar                     | Ironbar      | A GTK+ bar for wlroots  | ironbar      |
| Left Widgets            | EWW          | Widget Framework        |              |
| Notification            | Mako         | Notification            | mako         |
| App Launcher            | ULauncher    | App Launcher            | ulauncher    |
| Screenshot with Preview | Grimshot-pv  | Screenshot with Preview |              |
| Audio Visualizer        | Xava         | Audio Visualizer        | xava         |
| Screenshot Editor       | Swappy       | Screenshot and Editor   | swappy       |

## Fonts
- Caskaydia Cove Nerd Font

## Window Themes
- TokyoNight-Dark

Install command:

```
git clone https://github.com/Fausto-Korpsvart/Tokyo-Night-GTK-Theme
./install.sh -d ~/.local/share/themes -c dark -l --tweaks black
```

## Icons
- Tela-circle-icon-theme (Option 1)
- Aretha-Dark-Icons (Option 2)

## Shell
- Fish

## Shell Tools
| Program  | Role                      |
| -------- | ------------------------- |
| Starship | Prompt                    |
| Catnip   | Fetch                     |
| SwayOSD  | OSD for Volume, Caps Lock |

## Utilities
- Lite XL: Text Editor

# 2. Dependencies

## 2.1. Arch Linux Packages
1. Install GNOME Desktop
2. Install these: `sudo pacman -S freetype2 glm libdrm libevdev libgl libinput libjpeg libpng libxkbcommon libxml2 pixman wayland-protocols wlroots meson cmake doctest doxygen nlohmann-json libnotify base-devel pkg-config autoconf gobject-introspection gtk-layer-shell scour libdbusmenu-gtk3 gtkmm3 glib2-devel`

That is:

| Program                              | Function                              | Package               |
| ------------------------------------ | ------------------------------------- | --------------------- |
| Freetype 2                           | Font Rendering Engine and Library     | freetype              |
| GLM                                  | C++ Mathematical Library for Graphics | gml                   |
| DRM Library                          |                                       | libdrm                |
| Event Device Library                 |                                       | libevdev              |
| OpenGL Library                       |                                       | libglvnd              |
| Input Library                        |                                       | libinput              |
| JPEG Library                         |                                       | libjpeg               |
| PNG Library                          |                                       | libpng                |
| X Keyboard Common Library            |                                       | libxkbcommon          |
| XML2 Library                         |                                       | libxml2               |
| Doctest                              | C++ Testing Framework                 | doctest               |
| Doxygen                              |                                       | doxygen               |
| JSON C++ / JSON Library by N Lohmann |                                       | json-c++              |
| Notify Library                       |                                       | libnotify             |
| Base Development Files               |                                       | base-devel            |
| pkg-config                           |                                       | pkg-config            |
| GNU Autoconf                         |                                       | autoconf              |
| GObject Introspection                |                                       | gobject-introspection |
| GTK Layer Shell                      |                                       | gtk-layer-shell       |
| Scour                                | SVG Optimizer                         | python3-scour         |
| GTK3 D-Bus Menu Library              |                                       | libdbusmenu-gtk3      |
| GTKMM (GTK--) 3                      | C++ API for GTK+ 3                    | gtkmm                 |
| GLib 2 Development Files             |                                       | glib-devel            |

Note: Not sure if we need `-devel` versions of these packages, since Arch Linux bundles both into one package.

## 2.2. Wayfire Manual Install

This is needed to get the `wayfire.pc` `pkg-config` file.

```
git clone https://github.com/WayfireWM/wf-install
cd wf-install
./install.sh --prefix /opt/wayfire --stream master
```

## 2.3. Install Pixdecor

```
git clone https://github.com/soreau/pixdecor.git
cd pixdecor
PKG_CONFIG_PATH=/opt/wayfire/lib/pkgconfig meson setup build --prefix=/opt/wayfire
ninja -C build
ninja -C build install
```

## 2.4. Customization
Edit:
- `.config/wayfire.ini`
- `.config/wf-shell.ini`

## 2.5. To follow focus and set transparency for inactive windows

This is actually included in the setup, so no need to redo it.

1. Create `~/.config/environment.d/environment.conf`
2. Add `WAYFIRE_SOCKET=/tmp/wayfire-wayland-1.socket` to it.
3. From https://github.com/WayfireWM/pywayfire/tree/main/scripts, copy `inactive-alpha.py` an `wayfire_socket.py` somewhere, like `~/.config/ipc-scripts/*.py`
4. Add the following lines to `~/.config/wayfire.ini`:
```
plugins = ipc ipc-rules follow-focus
[autostart] launcher = ~/.config/ipc-scripts/inactive-alpha.py 
```

---

# From Source

# 1. Programs

## 1.1. Scripts

### 1.1.1. Widgets
| Program               | Function                                                                |
| --------------------- | ----------------------------------------------------------------------- |
| `cava-internal`       | Music Visualizer Widget                                                 |
| `conky.sh`            | Widgets                                                                 |
| `date.sh`             | Date for Widget                                                         |
| `thunar.sh`           | Open `/home/bluebyt`, Downloads and `/mnt/media` in Thunar with delays  |
| `updates-notifier.sh` | Run `checkupdates` (alias) and notifies if there are any updates.       |
| `volume-pop.sh:`      | Monitors volume changes on a loop and makes sound if there is a change. |
| `xavaRestart.sh`      | Restarts xava if it is dead.                                            |

### 1.1.2. Wallpapers
| Program              | Function                |
| -------------------- | ----------------------- |
| `wallpaper_set.sh`   | Set Wallpapers          |
| `wallpapers_loop.sh` | Loop Wallpapers         |
| `kill_wallpaper.sh`  | Stop Looping Wallpapers |

### 1.1.3. In Hyprland Config
| Program                  | Function                     |
| ------------------------ | ---------------------------- |
| `cleanup_after_start.sh` | Unsets some workspaces       |
| `portal.sh`              | Restarts XDG Desktop Portals |

## 1.2. Binaries
| Program     | Function                        |
| ----------- | ------------------------------- |
| swww        | Simple Wayland Wallpaper Widget |
| swww-daemon | SWWW Daemon                     |

# 2. Configs

## 2.1. Compositor
- Wayfire: Main Compositor
- Hyprland, and Hyprpaper: Alternate Compositor

## 2.2. Programs
| Program     | Function                                                     |
| ----------- | ------------------------------------------------------------ |
| Catnip      | Used to show system information, has 3 fox wallpaper configs |
| Conky       | Has Edashich and grummimosa themes.                          |  
| EWW         | Widgets                                                      |
| Fish        | Shell, listed below in detail                                |
| Foot        | Terminal                                                     |
| IPC Scripts | A lot of scripts to manage Wayfire, MPV and ChatGPT systems  |
| Ironbar     | Status Bar                                                   |
| Kitty       | Terminal                                                     |
| Lite XL     | Text Editor                                                  |
| Mako        | Notification Daemon                                          |
| MPD         | Music Player Daemon                                          |
| MPV         | Media Player                                                 |
| NCMPCPP     | Music Player                                                 |
| PipeWire    | Sound Driver                                                 |
| PulseAudio  | Sound Driver (Legacy)                                        |
| Scripts     | Plenty of Scripts to manage when to start apps               |
| Starship    | Shell Prompt                                                 |
| ULauncher   | App Launcher                                                 |
| Waybar      | Status Bar                                                   |
| wlogout     | Logout menu                                                  |
| Xava        | Music Visualizer                                             |
| Zed         | Text Editor                                                  |             
| Zellij      | Terminal Workspace Manager (like `tmux`)                     |

## 2.3. Other (unlisted files in ~/.config)
| File                | What it does                |
| ------------------- | --------------------------- |
| chromium-flags.conf | Make Chrome prefer Wayland  |
| startship.toml      | Starship config             |
| wf-shell.ini        | wf-shell                    |

# 3. Shell Aliases

## 3.1. Generic Aliases
| Command   | Alias                                               |
| --------- | --------------------------------------------------- |
| c         | clear                                               |
| n         | nitch                                               |
| fox       | catnip -c ~/.config/catnip/config_fox.toml          |
| fox2      | catnip -c ~/.config/catnip/config_fox2.toml         |
| fox3      | catnip -c ~/.config/catnip/config_fox3.toml         |
| icat      | kitten icat                                         |
| cat       | catnip                                              |
| ls        | exa --icons -a                                      |
| ll        | exa --icons -ahl                                    |
| exa1      | exa --tree --level=1                                |
| exa2      | exa --tree --level=2                                |
| exa3      | exa --tree --level=3                                |
| work      | $HOME/.bin/cleanup_after_start.sh                   |
| pipe      | $HOME/Active/color-scripts/color-scripts/./pipes2   |
| play      | ncmpcpp                                             |
| la        | exa -a --color=always --group-directories-first     |

* Note: `cleanup_after_start.sh` is in .config/hypr..

## 3.2. Pacman Aliases
| Command   | Alias                                               | Description |
| --------- | --------------------------------------| ----------- |
| pacmandir | vpacman -Ql | To retrieve a list of the files installed by a package |
| pacmanR   | pacman -Rs | To remove a package and its dependencies | 
| pacmanQ   | pacman -Qs | To search for already installed packages |
| pacmanQi  | pacman -Qi | To display information about locally installed packages |
| unlock    | sudo rm /var/lib/pacman/db.lck | Remove pacman lock |
| cleanup   | sudo pacman -Rns (pacman -Qtdq) | Remove orphaned packages |
| clean     | sudo pacman -Sc | Remove old packages from cache |
| extract   | for i in *.rar; do unrar x -o+ "$i"; end |  |

## 4. Shell Configuration
```
catnip
export LS_COLORS="*.ini=31:*.ttf=36:*.toml=35"

set -x PATH $PATH ~/.bin
set -x PATH $PATH ~/.local/bin
set -x PATH $PATH ~/.local/bin/eww
set -x PATH $PATH ~/.local/bin/go/bin/
set -x PATH $PATH ~/.cargo/bin

set -x STARSHIP_CONFIG ~/.config/starship/starship.toml

starship init fish | source
zoxide init fish | source
fzf --fish | source
```
