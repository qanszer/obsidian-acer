
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


---
## 2 - Hidden Config

Enter url:
```
about:config
```

**Search and change to 180000 (3 minutes):**
```
browser.tabs.min_inactive_duration_before_unload
```

**Disable show sidebar on hover:**
```
zen.view.compact.show-sidebar-and-toolbar-on-hover
```

**Full screen only within browser window**
```
full-screen-api.ignore-widgets
```


---
## 3 - Extensions

### Performance

1. Auto Tab Discard
2. Zen Tab Unloader
### Privacy

1. uBlock Origin
2. Authenticator
### Styling

1. Stylus
2. Zen Internet
3. SocialFocus
4. Dark Reader
5. Tampermonkey
6. Gnome Shell Integration

### Snippets

**Tampermonkey Script**
Used to override ctrl+s shortcut for all websites to open zen's sidebar always

Create new script and paste this
```js
// ==UserScript==
// @name         Global Ctrl+S Browser Override
// @namespace    http://tampermonkey.net
// @version      1.1
// @description  Force native browser "Save As" behavior on all websites
// @author       You
// @match        *://*/*
// @run-at       document-start
// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    window.addEventListener('keydown', function(e) {
        // Check if Ctrl + S (or Cmd + S on Mac) is pressed
        if ((e.ctrlKey || e.metaKey) && e.code === 'KeyS') {
            // Stop the website from intercepting the event
            e.stopPropagation(); 
        }
    }, true); // True catches the event on the way down before the site can react
})();
```

**Stylus Styles**

```css
www.youtube.com

.ytSpecIconBadgeShapeStyleOverlay .ytSpecIconBadgeShapeIcon,
.yt-spec-icon-badge-shape,
.yt-spec-profile-page-header-information-view-model-shape__profile-page-header-title,
.yt-spec-icon-badge-shape--style-overlay .yt-spec-icon-badge-shape__icon,
.yt-badge-shape--promoted,
yt-icon.ytd-logo {
    color: white !important;
}


ytd-topbar-logo-renderer [fill^="#FF0"],
ytd-guide-entry-renderer [fill*="F00"],
ytd-guide-entry-renderer [fill="red"],
.ytSpecIconShapeHost [fill="#f03"],
#icon.yt-live-chat-viewer-engagement-message-renderer [fill*="F00"],
.ytp-cued-thumbnail-overlay:hover .ytp-large-play-button-bg,
ytd-compact-link-renderer [fill="#CC0000"],
ytd-badge-supported-renderer [fill="#CC0000"] {
    fill: white !important;
}

ytd-topbar-logo-renderer [fill="white"],
ytd-guide-entry-renderer [fill="#FAFAFA"],
ytd-guide-entry-renderer [fill="#FFFFFF"],
.ytSpecIconShapeHost [fill*="#fff"],
#icon.yt-live-chat-viewer-engagement-message-renderer [fill="#FFFFFF"],
.ytp-cued-thumbnail-overlay:hover [d*="M 45"],
ytd-compact-link-renderer [fill="#FFF"],
ytd-badge-supported-renderer [fill="#FFF"] {
    fill: #3f4c61 !important;
}
```

```css
https://www.messenger.com/e2ee/t/7564190246963460

div::selection {
    color: white !important;
    background-color: #e3a3b6 !important;
}
```

```css
messenger.com

div[data-testid="incoming_group"] div[role="row"] div[style*="background-color"],
div[data-testid="outgoing_group"] div[role="row"] div[style*="background-color"],
div[class*="html-div"] > div[style*="background-image"], 
div[role="row"] [dir="auto"]
{
    background-image: none !important;
    background-color: transparent !important; /* Set your desired speech bubble color here */
    border-radius: 18px !important;       /* Hardcodes a true physical rounding constraint */
    mask: none !important;                /* Destroys the overlapping clipping masks entirely */
    -webkit-mask: none !important; 
}

html, body, p, span, div, a, li, h1, h2, h3, h4, h5, h6, 
b, strong, i, em, small, code, pre, td, th, label, input, textarea {
    color: white !important; /* Dark Reader's default off-white text color */
    border-color: transparent !important; /* Optional: Soft dark borders to match */
}

html:root, 
body[class], 
div[class], 
main[id],
header, footer, nav, section, article, aside, table, tr, td, th, ul, ol, li {
    background-color: transparent !important;
    background-image: none !important;
}

::selection {
    background-color: #3a4558 !important;
    color: white !important;
}
```

```css
everything (readest) (need to install stylus shadowroots from tampermonkey)

/* :root {
    --color-base-100: transparent !important;
    --scroll-bg-color: transparent !important;
}

.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page *,
.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page.reader-page,
#background#background#background#background#background#background,
#shadow-root#shadow-root#shadow-root#shadow-root#shadow-root#shadow-root *,
:host(foliate-paginator) .internal-shadow-class,
:host(foliate-paginator) #background#background#background#background#background,
:host(foliate-paginator) *,
foliate-paginator::part(filter),
foliate-paginator iframe
{
    background: transparent !important;
    background-color: transparent !important;
} */


/* =======================================================
   1. YOUR WORKING SIDEBAR & GLOBAL LAYOUT DEFS
   ======================================================= */
:root {
    --color-base-100: transparent !important;
    --scroll-bg-color: transparent !important;
    --theme-bg-color: transparent !important;
}

.reader-page,
.reader-page *,
.reader-page .reader-page {
    background: transparent !important;
    background-color: transparent !important;
}

/* =======================================================
   2. PIERCE THE SHADOW PARTS (Foliate Layout Framework)
   ======================================================= */
foliate-paginator::part(filter),
foliate-paginator::part(container) {
    background: transparent !important;
    background-color: transparent !important;
}

/* Clear the host element backgrounds via the shadow userscript hook */
:host(foliate-paginator) #background,
:host(foliate-paginator) #top,
:host(foliate-paginator) #container {
    background: transparent !important;
    background-color: transparent !important;
}

/* =======================================================
   3. THE MAIN CONTENT BRICK WALL: TARGET THE DEEP IFRAME BODY
   ======================================================= */
/* Force absolute transparency directly on the iframe element wrapper */
foliate-paginator iframe {
    background: transparent !important;
    background-color: transparent !important;
}

/* Force global transparency on ANY element inside the nested document frame */
iframe html, 
iframe body, 
iframe #document,
foliate-paginator iframe * {
    background: transparent !important;
    background-color: transparent !important;
    color: inherit; /* Keeps your text visible over the transparent layers */
}
```

```css
theodinproject.com

div
{
    background-color: transparent !important;
    background-image: none !important;
    box-shadow: none !important;
    scrollbar-color: transparent transparent !important;
    color: white !important;
}

:root,[dir=ltr] {
    color: white !important;
}
```

```css
https://novelphoenix.com/novel/

img, label {
    display: none;
}

video {
    display: none !important;
}

::selection {
    color: white;
    background-color: #3a4558;
}

main,
main *,
article,
article *,
li.nav-item.nav-search,
li.nav-item.nav-search *,
button,
button *,
a,
a *,
select,
select *,
div.clearfix.chapternav.skiptranslate * {
    background-color: transparent !important;
    background-image: none !important;
    box-shadow: none !important;
}

* {
    color: #f6f6f6 !important;
}
```

```css
https://novelfire.net/

img, label {
    display: none;
}

video {
    display: none !important;
}
```

```css
https://www.google.com/search

div[data-mcpr] {
    margin-top: 15px !important;
}

div#m-x-content
{
    padding-left: 30px !important;
    padding-top: 15px !important;
}

html:root, 
body[class], 
div[class], 
main[id],
header, footer, nav, section, article, aside, table, tr, td, th, ul, ol, li {
    background-color: transparent !important;
    background-image: none !important;
}

html, body, p, span, div, a, li, h1, h1.panel-title.panel-title.panel-title.panel-title.panel-title.panel-title, h2, h3, h4, h5, h6, 
b, strong, i, em, small, code, pre, td, th, label, input, textarea, button, svg {
    color: white !important; /* Dark Reader's default off-white text color */
}

#docs-menubar * {
    color: white !important;
}

#docs-editor-container {
    background-color: transparent !important;
    
}

div:has(> div#searchform#searchform),
div#searchform#searchform *
{
    backdrop-filter: blur(3px) !important;
    -webkit-backdrop-filter: blur(10px) !important;
    background-color: transparent !important;
}
```
