
2026-07-20  10:15pm

Tags: [[Customization]], [[Productivity]]

---
# Zen Browser Configurations


## 1 - Settings

### Look and Feel

Check:
- Sidebar and top toolbar
- Move new tab button

Uncheck:
- Show new tab button
- Enable glance

Zen URL Bar - Always floating

### Keyboard Shortcuts

Backward workspace: alt + shift + a
Foward workspace: alt + shift + s

### Search

1. Navigate to 'additional search engines'
2. Add search engine
	- Name: Youtube
	- URL: https://www.youtube.com/results?search_query=%s
	- Keyword: @yt

### Downloads

- Check 'ask where to save files before downloading'

### Installed Mods

- Ghost tabs
- No top sites
- Better find bar
- Zen context menu
- Transparent zen (i dont use it but recommended)

### Turn on Sync

- To connect the browser with my other boots (Windows 11 and CachyOS)
- Go to manage sync; check the workspaces box


## 2 - Customize Timer for Unloading Tabs

Enter url:
```
about:config
```

Search and change to 180000 (3 minutes):
```
browser.tabs.min_inactive_duration_before_unload
```

