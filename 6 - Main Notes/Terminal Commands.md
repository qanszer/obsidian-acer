
2025-09-14  18:43

Tags: [[Coding]] [[Terminal]] [[Customization]]

---

# Terminal Commands


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


Install using .deb package:
first do `sudo apt update && sudo apt upgrade`
then `sudo apt install build-essential`
go to directory of the deb file like `cd Downloads/`
`sudo dpkg -i filename`
if there were dependency issues, run `sudo apt-get install -f`


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


====

Clean unneeded packages:
sudo apt autoremove

Clean cache:  
sudo apt-get clean

Clean system journal logs:
journalctl --disk-usage
sudo journalctl --vacuum-time=3d

Clean thumbnail:  
rm -rf ~/.cache/thumbnails/*

Current remotes:
name - gdrive
type - drive

Rclone gdrive:
nano ~/.config/systemd/user/rclone-gdrive.service

====

Change terminal color based on wallpaper:
wal -i ~/pic_location

Automate pywal:
Add this line to your "nano ~/.bashrc" or "nano ~/.zshrc":
[[ -f "$HOME/.cache/wal/sequences" ]] && cat "$HOME/.cache/wal/sequences"

Reload terminal:
source ~/.bashrc

Copy a directory to multiple directories:
for dir in destination_dir1 destination_dir2 destination_dir3; do cp -r source_directory/* "$dir"; done

Change sudo password:
sudo passwd
then follow instructions


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

```
ffmpeg -f concat -safe 0 -i videos.txt -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k merged_output.mp4
```

**Cut video by time:**
```
ffmpeg -ss 00:00:00 -i input.mp4 -t 00:00:30 -c copy output.mp4
```


---

# References

chatgpt
claude
