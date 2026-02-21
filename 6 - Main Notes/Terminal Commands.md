
2025-09-14  18:43

Tags: [[Coding]] [[Terminal]] [[Customization]]

---

# Terminal Commands

A list of bash commands I commonly use. This is a note to look back to when I need to use them again.


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


Guide to reinstall older packages when the dependencies need an older one:
https://green.cloud/docs/how-to-downgrade-a-package-via-apt-get/#:~:text=Estimated%20reading:%203%20minutes%201386,one%2C%20you%20are%20in%20luck.
```bash
apt-cache policy package-name
sudo apt-get install package-name=package-version-number
```


See current swappiness value:
cat /proc/sys/vm/swappiness

Temporarily set new swap value:
sudo sysctl vm.swappiness=10


Check shell version:
gnome-shell --version

Remove mounted disks on dock:
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false

Edit the battery alert script:
nano ~/battery_alert.sh

Run the battery alert script:
nohup ~/battery_alert.sh &

Copy a directory to multiple directories:
for dir in destination_dir1 destination_dir2 destination_dir3; do cp -r source_directory/* "$dir"; done

Change sudo password:
sudo passwd
then follow instructions


---

### System Cleaning

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

**One-liner Cleaner:**
```bash
sudo apt autoremove && sudo apt-get clean && sudo journalctl --vacuum-time=3d && rm -rf ~/.cache/thumbnails/*
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
```
ffmpeg -i input.webm -c:v libx264 -c:a aac output.mp4
```


**Merge videos:**
1. Create a text file listing the videos
```
file 'video1.webm'
file 'video2.webm'
```

2. Run the merge command. Change the output file name as needed

Merge + convert to mp4
```
ffmpeg -f concat -safe 0 -i videos.txt -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k output.mp4
```

Merge only
```
ffmpeg -f concat -safe 0 -i videos.txt -c copy output.mp4

```


**Cut video by time:**
```
ffmpeg -ss 00:00:00 -i input.mp4 -t 00:00:30 -c copy output.mp4
```


**Mass convert webm to mp4**:
```
for f in *.webm; do ffmpeg -i "$f" -c:v libx264 -c:a aac "${f%.webm}.mp4"; done

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

# References

chatgpt
claude
google