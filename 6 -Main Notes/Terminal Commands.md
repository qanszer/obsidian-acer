
2025-09-14  18:43

Tags: [[Coding]] [[Terminal]] [[Customization]]

---

# Terminal Commands


Check shell version:
gnome-shell --version

Remove mounted disks on dock:
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false

Edit the battery alert script:
nano ~/battery_alert.sh

Run the battery alert script:
nohup ~/battery_alert.sh &

Check Ubuntu version:
lsb_release -a

Know shell version:
gnome-shell --version

====

Clean unneeded packages:
sudo apt autoremove

Clean cache:  
sudo apt-get clean

Clean system journal logs:
journalctl --disk-usage
sudo journalctl --vacuum-time=3d

Clean snaps:
sudo bash clean_snap.sh
du -h /var/lib/snapd/snaps

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

  


---

# References

chatgpt
