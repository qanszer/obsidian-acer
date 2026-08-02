
2026-02-09  05:02 am

Tags: [[Tracking]], [[Customization]], [[Productivity]]

---
# All Installed Software

This is a list of all of my installed software in case my laptop breaks/gets stolen and I need to install them again.

# Linux (Ubuntu 22.04 LTS)

### Apps

- Tweaks
- Cisco packet tracer
- Gparted live iso file
- Localsend
- Super productivity
- Obsidian
- Brave browser
- Foliate
- Visual studio code
- Git
- VLC
- Only office
- Picard
- Signal
- Gromit-mpx
- Pulse audio
- Extensions
- Grub customizer
- Htop
- Elegant-mojave-window Grub theme
- Balena etcher
- Themes: Nordic polar and Nordic darker (v40)
- Rmpc
- Shotwell
- Tlp
- Zen browser
- Handbrake
- Kamoso
- Anydesk
- Blanket
- Aqloss
- Flathub

### Gnome Extensions

- Blur my shell
- Color picker
- Dash to dock
- Rounded window corners
- Tiling shell
- Places status indicator
- User themes
- Workspace indicator

### Scripts

#### CUSTOM KEYBOARD SHORTCUTS

| Name            | Command                                        | Shortcut                  | Script                                    |
| --------------- | ---------------------------------------------- | ------------------------- | ----------------------------------------- |
| Shutdown system | gnome-session-quit --power-off                 | shift + super + backspace |                                           |
| Restart system  | reboot                                         | super + backspace         |                                           |
| Suspend system  | bash -c "systemctl suspend -i"                 | shift + super + s         |                                           |
| Toggle cursor   | /home/YOURUSERNAME/.local/bin/toggle_cursor.sh | alt + c                   | [toggle_cursor.sh]([[Terminal Commands]]) |
| Gromit draw     | gromit-mpx --toggle                            | f12                       |                                           |


#### GENERAL

`theme.sh`:

```bash
#!/bin/bash

MODE=$1

if [ "$MODE" = "dark" ]; then
    # Dark mode settings
    gsettings set org.gnome.desktop.interface gtk-theme 'Nordic-bluish-accent-v40'
    gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
    gsettings set org.gnome.shell.extensions.user-theme name 'Nordic-bluish-accent-v40'
    gsettings set org.gnome.desktop.wm.preferences theme 'Nordic-bluish-accent-v40'
    gsettings set org.gnome.desktop.background picture-uri "file:///home/steven/Media/pictures/theme/night.png"
    gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/steven/Media/pictures/theme/night.png"
    gsettings set org.gnome.desktop.screensaver picture-uri "file:///home/steven/Media/pictures/theme/night.png"
    gsettings set org.gnome.desktop.interface icon-theme 'Yaru-blue-dark'
    neofetch
    wal -i ~/Media/pictures/wallpapers/nord-shapes.png

elif [ "$MODE" = "light" ]; then
    # Light mode settings
    gsettings set org.gnome.desktop.interface gtk-theme 'Nordic-Polar-v40'
    gsettings set org.gnome.desktop.interface color-scheme 'prefer-light'
    gsettings set org.gnome.shell.extensions.user-theme name 'Nordic-Polar-v40'
    gsettings set org.gnome.desktop.wm.preferences theme 'Nordic-Polar-v40'
    gsettings set org.gnome.desktop.background picture-uri "file:///home/steven/Media/pictures/theme/day.jpg"
    gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/steven/Media/pictures/theme/day.jpg"
    gsettings set org.gnome.desktop.screensaver picture-uri "file:///home/steven/Media/pictures/theme/day.jpg"
    gsettings set org.gnome.desktop.interface icon-theme 'Yaru-blue-dark'
    neofetch
    wal -i ~/Media/pictures/wallpapers/snow-mountain-v4.jpg

elif [ "$MODE" = "neon" ]; then
    # Dark mode settings
    gsettings set org.gnome.desktop.interface gtk-theme 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
    gsettings set org.gnome.shell.extensions.user-theme name 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.wm.preferences theme 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.background picture-uri "file:///home/steven/Media/pictures/theme/cnight.png"
    gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/steven/Media/pictures/theme/cnight.png"
    gsettings set org.gnome.desktop.screensaver picture-uri "file:///home/steven/Media/pictures/theme/cnight.png"
    gsettings set org.gnome.desktop.interface icon-theme 'Yaru-blue-dark'
    neofetch
    wal -i ~/Media/pictures/theme/cnight.png

elif [ "$MODE" = "nord" ]; then
    # Dark mode settings
    gsettings set org.gnome.desktop.interface gtk-theme 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
    gsettings set org.gnome.shell.extensions.user-theme name 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.wm.preferences theme 'Nordic-darker-v40'
    gsettings set org.gnome.desktop.background picture-uri "file:///home/steven/Media/pictures/theme/nord.png"
    gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/steven/Media/pictures/theme/nord.png"
    gsettings set org.gnome.desktop.screensaver picture-uri "file:///home/steven/Media/pictures/theme/nord.png"
    gsettings set org.gnome.desktop.interface icon-theme 'Yaru-blue-dark'
    neofetch
    wal -i ~/Media/pictures/theme/nord.png

else
    echo "Usage: $0 {light|dark|neon|nord}"
    exit 1

fi
```


`apply-scheduled-theme.sh`:

```bash
#!/bin/bash
LIGHT_MODE_START_HOUR=6
NORD_MODE_START_HOUR=18

currentHour=$(date +%H)

if [ "$currentHour" -ge "$LIGHT_MODE_START_HOUR" ] && [ "$currentHour" -lt "$NORD_MODE_START_HOUR" ]; then
    ~/theme.sh light
else
    ~/theme.sh nord
fi
```


`theme@.service`:

```bash
[Unit]
Description=Apply %i theme

[Service]
Type=oneshot
ExecStart=%h/theme.sh %i
```


`theme-login.service`:

```bash
[Unit]
Description=Apply correct theme on login

[Service]
Type=oneshot
ExecStart=%h/.local/bin/apply-scheduled-theme.sh

[Install]
WantedBy=default.target
```


`theme-light.timer`:

```bash
[Unit]
Description=Trigger light theme at 06:00

[Timer]
OnCalendar=*-*-* 06:00:00
Persistent=true
Unit=theme@light.service

[Install]
WantedBy=timers.target
```


`theme-nord.timer`:

```bash
[Unit]
Description=Trigger nord theme at 18:00

[Timer]
OnCalendar=*-*-* 18:00:00
Persistent=true
Unit=theme@nord.service

[Install]
WantedBy=timers.target
```

```bash
chmod +x ~/.local/bin/apply-scheduled-theme.sh
chmod +x ~/theme.sh

systemctl --user daemon-reload
systemctl --user enable --now theme-light.timer
systemctl --user enable --now theme-nord.timer
systemctl --user enable --now theme-login.service

loginctl enable-linger steven
```


`battery-alert.sh`:

```bash
#!/bin/bash

HIGH_THRESHOLD=80  # Alert to unplug
LOW_THRESHOLD=30   # Alert to plug in
ALERT_SOUND="/usr/share/sounds/freedesktop/stereo/alarm-clock-elapsed.oga"

# Flags to prevent repeated alerts
high_alert_sent=false
low_alert_sent=false

while true; do
    battery_info=$(upower -i $(upower -e | grep BAT))
    battery_level=$(echo "$battery_info" | grep percentage | awk '{print $2}' | tr -d '%')
    status=$(echo "$battery_info" | grep state | awk '{print $2}')

    # --- Alert to unplug at high threshold ---
    if [ "$status" = "charging" ] && [ "$battery_level" -ge "$HIGH_THRESHOLD" ]; then
        if [ "$high_alert_sent" = false ]; then
            notify-send "🔋 Battery Alert" "Battery is at ${battery_level}%. Please unplug to protect battery health."
            paplay "$ALERT_SOUND"
            high_alert_sent=true
        fi
    else
        # Reset the high alert flag once it goes below the threshold
        if [ "$battery_level" -lt "$HIGH_THRESHOLD" ]; then
            high_alert_sent=false
        fi
    fi

    # --- Alert to plug in at low threshold ---
    if [ "$status" = "discharging" ] && [ "$battery_level" -le "$LOW_THRESHOLD" ]; then
        if [ "$low_alert_sent" = false ]; then
            notify-send "⚠️ Battery Low" "Battery is at ${battery_level}%. Please plug in your charger."
            paplay "$ALERT_SOUND"
            low_alert_sent=true
        fi
    else
        # Reset the low alert flag once it goes above the threshold
        if [ "$battery_level" -gt "$LOW_THRESHOLD" ]; then
            low_alert_sent=false
        fi
    fi

    sleep 60
done
#!/bin/bash

THRESHOLD=80
ALERT_SOUND="/usr/share/sounds/freedesktop/stereo/alarm-clock-elapsed.oga"

while true; do
    # Get battery percentage as an integer
    battery_level=$(upower -i $(upower -e | grep BAT) | grep percentage | awk '{print $2}' | tr -d '%')
    
    # Get charging status
    status=$(upower -i $(upower -e | grep BAT) | grep state | awk '{print $2}')
    
    if [ "$status" = "charging" ] && [ "$battery_level" -ge "$THRESHOLD" ]; then
        notify-send "🔋 Battery Alert" "Battery level is ${battery_level}%. Please unplug to preserve battery health."
        paplay "$ALERT_SOUND"
    fi
    
    sleep 60
done
```


`water-reminder.sh`:

```bash
#!/usr/bin/env bash
# water_reminder.sh — sends a desktop notification every 2 hours, aligned to clock hours

DISPLAY="${DISPLAY:-:0}"
DBUS_SESSION_BUS_ADDRESS="${DBUS_SESSION_BUS_ADDRESS:-unix:path=/run/user/$(id -u)/bus}"

export DISPLAY
export DBUS_SESSION_BUS_ADDRESS

TITLE="Hydration reminder"
BODY="Drink water"
ICON="dialog-information"

while true; do
    # Get current minute and second
    MINUTE=$(date +%-M)
    SECOND=$(date +%-S)

    # Calculate seconds until next even 2-hour mark (0,2,4,...,22)
    HOUR=$(date +%-H)
    HOURS_UNTIL_NEXT=$(( 2 - (HOUR % 2) ))
    if [ "$HOURS_UNTIL_NEXT" -eq 2 ] && [ "$MINUTE" -eq 0 ] && [ "$SECOND" -eq 0 ]; then
        HOURS_UNTIL_NEXT=0
    fi

    SECONDS_UNTIL_NEXT=$(( (HOURS_UNTIL_NEXT * 3600) - (MINUTE * 60) - SECOND ))

    if [ "$SECONDS_UNTIL_NEXT" -le 0 ]; then
        SECONDS_UNTIL_NEXT=$(( 7200 - (MINUTE * 60) - SECOND ))
    fi

    sleep "$SECONDS_UNTIL_NEXT"

    notify-send --urgency=normal --icon="$ICON" "$TITLE" "$BODY"
done
```


`water-reminder.service`:

```bash
[Unit]
Description=Water Drink Reminder
After=graphical-session.target
PartOf=graphical-session.target

[Service]
Type=simple
ExecStart=%h/.local/bin/water_reminder.sh
Restart=on-failure
RestartSec=5
Environment=DISPLAY=:0

[Install]
WantedBy=graphical-session.target
```





---

# Windows 11

### Apps

- Brave browser
- Discord
- Flow launcher
- Git
- Minibin
- Office setup
- Only office
- Propresenter 6
- Visual studio
- Visual studio code
- Wind hawk

### Fonts (for pp6)

- Analogist
- Bebas kai
- DM serif text
- Fugaz one
- Goldman
- Orbitron
- Racing sans one
- Goudy titling w05 bold
- Gyahegi
- IM fell english
- Jet brains mono
- La obrige
- Redland
- Salih kizilkaya sk zweig

### Drivers (Acer Aspire 3 15)

- Airplane mode
- APP Base
- Audio console
- Realtek
- Bluetooth MTK
- Chipset AMD
- DES driver
- Fingerprint
- LAN realtek
- Wireless LAN MTK
