2025-09-14  18:43

Tags: [[Coding]] [[Terminal]] [[Customization]]

---

# Terminal Commands

A list of bash commands I commonly use. This is a note to look back to when I need to use them again.


---


Guide to reinstall older packages when the dependencies need an older one:
https://green.cloud/docs/how-to-downgrade-a-package-via-apt-get/#:~:text=Estimated%20reading:%203%20minutes%201386,one%2C%20you%20are%20in%20luck.
```bash
apt-cache policy package-name
sudo apt-get install package-name=package-version-number
```


**See current swappiness value:**
```bash
cat /proc/sys/vm/swappiness
```

Temporarily set new swap value:
```bash
sudo sysctl vm.swappiness=10
```


**Check shell version:**
```bash
gnome-shell --version
```

Remove mounted disks on dock:
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
```

Edit the battery alert script:
```bash
nano ~/battery_alert.sh
```

Run the battery alert script:
```bash
nohup ~/battery_alert.sh &
```

Copy a directory to multiple directories:
```bash
for dir in destination_dir1 destination_dir2 destination_dir3; do cp -r source_directory/* "$dir"; done
```


**Change sudo password:**
```bash
sudo passwd
```
then follow instructions


**Check system processes:**
```bash
htop
btop
sudo powertop
```


---
### System Cleaning

**One-liner Cleaner:**
```bash
sudo apt autoremove && sudo apt clean && sudo journalctl --vacuum-size=100M && rm -rf ~/.cache/thumbnails/*
```

Clean unneeded packages:
```bash
sudo apt autoremove
```

Clean cache: 
```bash
sudo apt-get clean
```

Clean system journal logs:
```bash
journalctl --disk-usage
sudo journalctl --vacuum-time=3d
```

Clean thumbnail:  
```bash
rm -rf ~/.cache/thumbnails/*
```

---
### Change terminal's color scheme based on wallpaper

1. Install everything needed
```bash
sudo apt update && sudo apt install python3-pip
```

```bash
sudo pip3 install pywal
```

2. Change terminal's color
```bash
wal -i ~/path/to/your/wallpaper.png
```

3. Automate it on startup
```bash
nano ~/.bashrc
```

```bash
[[ -f "$HOME/.cache/wal/sequences" ]] && cat "$HOME/.cache/wal/sequences"
```

```bash
source ~/.bashrc
```

---
### Video editing


**Change video format to mp4:**
```bash
ffmpeg -i input.webm -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -c:v libx264 -c:a aac output.mp4
```


**Merge videos:**
1. Create a text file listing the videos
```bash
file 'video1.webm'
file 'video2.webm'
```

2. Run the merge command. Change the output file name as needed

a. Merge + convert to mp4
```bash
ffmpeg -f concat -safe 0 -i videos.txt
-vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k output.mp4
```

b. Merge only
```bash
ffmpeg -f concat -safe 0 -i videos.txt -c copy output.mp4
```


**Cut video by time:**
a. video
```bash
ffmpeg -ss 00:00:00 -to 00:00:30 -i input.mp4 -c copy output.mp4
```

b. audio
```bash
ffmpeg -ss 00:00:00 -to 00:01:30 -i input.mp3 -acodec copy output.mp3
```


**Increase audio volume:**
```bash
ffmpeg -i input.mp3 -af "volume=1.5" output.mp3
```


**Mass convert webm to mp4**:

libx264 w 4 threads
```bash
for f in *.mp4; do
  output="${f%.mp4}_compressed.mp4"
  
  # Skip if output already exists
  if [ -f "$output" ]; then
    echo "Skipping $f (already compressed)"
    continue
  fi
  
  nice -n 19 ffmpeg -i "$f" -threads 4 \
    -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
    -c:v libx264 \
    -crf 23 \
    -preset slow \
    -c:a aac \
    -b:a 128k \
    -movflags +faststart \
    -pix_fmt yuv420p \
    -y \
    "$output"
done
```

libx265 w 8 threads
```bash
for f in *.mp4; do
  output="[c]${f%.mp4}-h265.mp4"
  
  if [ -f "$output" ]; then
    echo "Skipping $f (already compressed)"
    continue
  fi
  
  nice -n 19 ffmpeg -i "$f" -threads 8 \
    -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
    -c:v libx265 \
    -crf 28 \
    -preset medium \
    -c:a aac \
    -b:a 128k \
    -movflags +faststart \
    -pix_fmt yuv420p \
    -y \
    "$output"
done
```

```bash
#!/bin/bash

# Enable case-insensitive globbing to catch .MP4, .Mkv, etc.
shopt -s nocaseglob

# Loop through all common video formats
for f in *.{mp4,mkv,webm,mpeg,mpg,mov,avi,flv}; do
  # Check if the file exists (prevents errors if a format is missing)
  [ -e "$f" ] || continue

  # Create output name: original_name_h265.mp4
  output="[c]${f%.*}_h265.mp4"
  
  if [ -f "$output" ]; then
    echo "Skipping $f (already compressed)"
    continue
  fi
  
  echo "Processing: $f"
  
  # -threads 8: Keeps your Ryzen 5700U from overheating
  # -tag:v hvc1: Essential for H.265 to play on Apple devices/standard players
  nice -n 19 ffmpeg -i "$f" \
    -threads 8 \
    -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
    -c:v libx265 \
    -crf 28 \
    -preset medium \
    -tag:v hvc1 \
    -c:a aac \
    -b:a 128k \
    -movflags +faststart \
    -pix_fmt yuv420p \
    -y \
    "$output"
done

# Turn off case-insensitive globbing
shopt -u nocaseglob

```

**Run a script unattended**
```bash
tmux new -s convert
# then run your loop script inside

tmux attach -t convert
# run the existing tmux session

tmux kill-session -t convert
# kill the tmux session
```

---
### Install a downloaded local deb file

```bash
sudo dpkg -i ./filename
```

```bash
sudo apt install -f
```

---
### Search and install an app over internet

```bash
apt search app-name
```

```bash
sudo apt install chosen-app-name
```

---
### Uninstall an apt app

```bash
sudo apt remove --purge AppName && sudo apt autoremove
```

---
### Edit nautilus' bookmarks

```bash
nano ~/.config/gtk-3.0/bookmarks
```

---
### When printer cannot print

```bash
# List all printers
lpstat -p -d 
# Check CUPS status
systemctl status cups 
# See if printer is detected 
lpinfo -v
```

```bash
# Restart the printing service 
sudo systemctl restart cups 
# Check if it's running 
systemctl status cups
```

```bash
system-config-printer
```

1. Remove printer
2. Readd printer
3. Test print

---
### When Nautilus gets bugged again

```bash
killall -9 gvfsd gvfsd-fuse
```

---
### If the suspend command acts up because of Super Productivity

1. Paste this in the terminal
```bash
sudo systemctl disable systemd-suspend.service
sudo systemctl reset-failed
```

2. Reboot the device
3. Check if it's working normally again. If not, refer [here](https://claude.ai/share/11a5ee70-ca70-4450-9b3f-df420e2d0bd7)

---
### Database Server

Check status of Database Engine:
```bash
systemctl status mssql-server --no-pager
```

Stop the Database Engine:
```bash
sudo systemctl stop mssql-server
```

Start the Database Engine:
```bash
sudo systemctl start mssql-server
```

Restart the Database Engine:
```bash
sudo systemctl restart mssql-server
```

Login as user_admin on SQL Server:
```bash
sqlcmd -S 127.0.0.1 -U admin_user -No
```
SecureAdmin123!

---
### Artificially increase brightness level
*This feature is only for X11 users, not Wayland.*

1. Check your monitor name (first word right next to `connected`)
```bash
xrandr | grep " connected"
```
2. Increase at your own discretion (1.2 ,1.5, etc)
```bash
xrandr --output <YOUR_MONITOR_NAME> --brightness 1.2
```

**Mine**
```bash
xrandr --output eDP --brightness 1.3
```

**Revert back to normal**
```bash
xrandr --output eDP --brightness 1
```

---
### Uninstall a PWA (Progressive Web App)

1. Type `brave://apps` or whatever browser you installed it from, like `chrome://apps`
2. Remove it from there

---
### Firewall

```bash
# 1. (Optional) Set defaults: deny incoming, allow outgoing
sudo ufw default deny incoming
sudo ufw default allow outgoing

# 2. IMPORTANT: Allow SSH to avoid locking yourself out
sudo ufw allow ssh

# 3. Turn on the firewall
sudo ufw enable

# 4. Verify the status
sudo ufw status verbose
```

- **Allow Specific Ports:** If you are running a web server, allow traffic on ports 80 (HTTP) and 443 (HTTPS):
```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

- **Disable Firewall:** If needed, you can stop it using `sudo ufw disable`.

---
### Wayland / Xorg

Check what you're using:
```bash
echo $XDG_SESSION_TYPE
```

**Use xorg on login:**

1. Go to config
```bash
sudo nano /etc/gdm3/custom.conf
```

2. Uncomment this line
```bash
# Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false
```


**Use wayland again:**

1. Comment out this line
```bash
WaylandEnable=false
```


---

### Clear laptop fan noise with TLP

```bash
sudo apt install tlp tlp-rdw
sudo systemctl enable tlp --now
```

Configure tlp based on your laptop's specs using AI.

```bash
sudo apt install linux-tools-common linux-tools-generic
```

```bash
cpupower frequency-info
sudo cpupower frequency-set -g powersave
```

Check TLP is running balance power

```bash
cat /sys/devices/system/cpu/cpu*/cpufreq/energy_performance_preference
```

if not on balance power, run this:
```bash
echo balance_power | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/energy_performance_preference
sudo sed -i 's/CPU_ENERGY_PERF_POLICY_ON_AC=balance_performance/CPU_ENERGY_PERF_POLICY_ON_AC=balance_power/' /etc/tlp.conf
sudo systemctl restart tlp
```


---

### Hide cursor using shortcut (x11 only; wayland uses gnome extension)

```bash
sudo apt install unclutter-xfixes
```

```bash
nano ~/toggle_cursor.sh
```

```bash
#!/bin/bash
if pgrep -x "unclutter" > /dev/null
then
    pkill -x unclutter
else
    # --timeout 0 hides it instantly without waiting for inactivity
    unclutter --timeout 0 &
fi
```

- Open your GNOME **Settings** application.
- Navigate to **Keyboard** -> **Keyboard Shortcuts** -> **View and Customise Shortcuts**.
- Scroll down and select **Custom Shortcuts**, then click the **+** (Add Shortcut) button.
- Fill out the fields:
    - **Name**: Toggle Mouse Cursor
    - **Command**: `/home/YOUR_USERNAME/toggle_cursor.sh` _(Replace `YOUR_USERNAME` with your actual Linux username)_
    - **Shortcut**: Press your desired key combination (e.g., `Alt` + `C`).
- Click **Add**.


---

### Create a custom GNOME 42 image popup extension

I did this for an easily accessible schedule popup.

1. **Create the Directory**
Open your terminal and create the required local extension folder:
```bash
mkdir -p ~/.local/share/gnome-shell/extensions/image-popup@yourname.local
cd ~/.local/share/gnome-shell/extensions/image-popup@yourname.local
```

2. **Create `metadata.json`**
Create a file named `metadata.json` to register the extension with GNOME 42:
```json
{
  "name": "Image Popup Extension",
  "description": "Pops up a custom image when clicked",
  "uuid": "image-popup@yourname.local",
  "shell-version": [ "42" ]
}
```

3. **Create `extension.js`**
Create a file named `extension.js` with the following system code. _(Ensure you update the `/path/to/your/image.png` placeholder to your real file path)._
```javascript
const Gio = imports.gi.Gio;
const St = imports.gi.St;
const PanelMenu = imports.ui.panelMenu;
const Main = imports.ui.main;

let _indicator;

function init() {}

function enable() {
    _indicator = new PanelMenu.Button(0.0, 'Image Popup Indicator', false);

    let panelIcon = new St.Icon({
        gicon: new Gio.ThemedIcon({ name: 'image-x-generic-symbolic' }),
        style_class: 'system-status-icon'
    });
    _indicator.add_child(panelIcon);

    let box = new St.BoxLayout({ vertical: true });
    let imagePath = '/path/to/your/image.png'; 
    let file = Gio.File.new_for_path(imagePath);
    let gicon = new Gio.FileIcon({ file: file });

    let imageWrapper = new St.Bin({
        width: 720,
        height: 758,
        x_align: St.Align.MIDDLE,
        y_align: St.Align.MIDDLE
    });

    let popupImage = new St.Icon({
        gicon: gicon,
        icon_size: 758
    });

    imageWrapper.set_child(popupImage);
    box.add_child(imageWrapper);
    _indicator.menu.box.add_child(box);

    Main.panel.addToStatusArea('image-popup-indicator', _indicator, 0, 'left');
}

function disable() {
    if (_indicator) {
        _indicator.destroy();
        _indicator = null;
    }
}
```

4. Activate the Extension
Reload your desktop environment to register your newly created local files:
- **X11 Display**: Press `Alt + F2`, type `r`, and press `Enter`.
- **Wayland Display**: Log out of your Linux session and log back in.

Open the **Extensions** app (or run `gnome-extensions enable image-popup@yourname.local`) to activate it.


---

### Create own screen recorder using ffmpeg

```bash
sudo apt update && sudo apt install ffmpeg notify-osd
```

```bash
nano ~/toggle_record.sh
```

```bash
#!/bin/bash
PID=$(pgrep -f "ffmpeg -f x11grab")

if [ -n "$PID" ]; then
    kill -2 $PID
    notify-send "Screen Recorder" "Recording saved to Screencasts folder."
else
    # Automatically detects your active resolution (e.g., 1366x768, 2560x1440)
    RESOLUTION=$(xdpyinfo | grep dimensions | awk '{print $2}')
    
    notify-send "Screen Recorder" "Recording started..."
    
    # Uses the detected resolution and system DISPLAY variable dynamically
    ffmpeg -f x11grab -video_size "$RESOLUTION" -i "$DISPLAY" -c:v libx264 -pix_fmt yuv420p 
    ~/Screencasts/recording_$(date +%Y%m%d_%H%M%S).mp4 & # Change to correct file path
fi
```

```bash
chmod +x ~/toggle_record.sh
```

**Set Up Shortcut Key**

1. Open your Ubuntu **Settings** app and head to **Keyboard** -> **Keyboard Shortcuts** -> **View and Customise Shortcuts**.
2. Scroll to the bottom edge, choose **Custom Shortcuts**, and hit the **+** (Add) button.
3. Apply the parameters below exactly:
    - **Name:** `MP4 Recorder`
    - **Command:** `/home/steven/toggle_record.sh`
    - **Shortcut:** Set it to your desired custom keys (for example: `Alt + R` or `Super + R`).
4. Click **Add**.


---

# References

1. Chatgpt
2. Claude
3. Google