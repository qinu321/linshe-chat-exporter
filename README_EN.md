# LinShe · Chat Exporter

[中文](./README.md)

A chat log exporter designed for [LinShe](https://github.com/icecranberry/galgame-with-comfyUI), exporting private/group chat logs into Obsidian-compatible markdown format.

It automatically converts chat text into the dialogue-style code used by [Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian), so your chat logs display with beautiful speech bubbles in Obsidian — just like they do inside LinShe!


## Installation

Download the zip package from Releases and unzip it:

1. Copy `chatbox.css` into your Obsidian `CSS snippets` folder (Settings → Appearance → CSS snippets → click the folder icon).

   Typically this is `your-vault/.obsidian/snippets`

   Then enable `chatbox` in Settings → Appearance → CSS snippets.

2. - Place `linshe-chat-exporter.html` somewhere convenient and fixed. Open it with Chrome/Edge, bookmark it, and use the bookmark next time.

   - Or use the [online link](https://qinu321.github.io/linshe-chat-exporter/) directly — whichever you prefer.


## Privacy & Security

**Completely safe and reliable!** Your chat logs stay completely private!

1. All operations run locally on your machine. Only your settings and the last message ID from batch exports are saved locally.
2. Text formatting only happens during export — no chat content is ever inspected or stored.
3. The entire tool is a single HTML file made of CSS + JS. The code is clean and inspectable. You can review it yourself anytime.
4. If you're worried but don't want to read the code, save the HTML file to your local drive, disconnect from the internet, and open it with Chrome/Edge.

This tool never needs an internet connection — it only talks to your local LinShe API.


## Features

Make sure LinShe is running, then open `linshe-chat-exporter.html` with Chrome/Edge.

Or use the [online link](https://qinu321.github.io/linshe-chat-exporter/).

Once connected, your private chat contacts will appear in the sidebar.

Click on a character to select their conversations. You can manually pick which ones to export, or auto-export everything.

![Sidebar showing chat contact list with conversation selection](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/sidebar-contacts-selection.jpg)

**Copy Selected** is the lightest option — it downloads selected images, formats the text, and copies everything to your clipboard for easy editing.

![Copy selected feature: downloads images and formats text to clipboard](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/copy-selected-messages.jpg)

Chat logs can be browsed page by page with ease, and you can **search and filter** messages, matching content/ID/date/character name:

```
AND (space): keyword1 keyword2
OR: +keyword1  +keyword2
Exclude: -keyword1
```

Click **Context** to jump directly to the original chat in LinShe.

![Search filter and context jump back to original chat](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/search-filter-context-jump.jpg)

Batch export splits files by date. You can set the maximum KB size per markdown file — when exceeded, the file is automatically split further.

`Exported to ID: XXXX` remembers the last message ID from the batch, making it easy to export only new content next time. You can also manually edit the ID to re-export. Click the label text before the ID to jump directly to that chat message in LinShe.


## Settings

### Export Folders

I strongly recommend **visiting Settings** before your first export.

Set up the three export folders (markdown, images, stickers) properly.

![Settings page: configure export folders for md, images, and stickers](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-export-folders.jpg)

This enables the exporter's **deduplication** feature, preventing redundant downloads during incremental exports.

It also makes batch exports of large volumes much faster and more stable!

### Image URL Prefix

If your Obsidian vault uses an external image library, you can set an image URL prefix in the settings.

![Settings page: image URL prefix configuration](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-image-url-prefix.jpg)

If you're using local images, leave this blank.

### Export Styles

Choose from 7 speech bubble styles. The default is LinShe's native style.

(About 90% faithful to the original — pretty close!)

![Seven speech bubble style options, defaulting to LinShe's native style](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-bubble-styles.jpg)

### Markdown Template Settings

Supports variable substitution — you can build complex templates.

Batch export supports the previous file name variable:

For example, write `previous:: [[{{previousFileName}}]]` in your template, and every exported markdown file will be linked together — great for breadcrumb plugins or Dataview navigation.

![Markdown template settings: variable substitution and previous file name linking](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-md-template.jpg)

### Export Avatars

Since avatars only need to be exported once, this option is placed at the bottom of Settings.

![Settings page: avatar export options](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/settings-export-avatar.jpg)


## Preview in Obsidian

The dialogue-style display is powered by my [Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian) CSS theme.

Regular users don't need to worry about the code format — the exporter handles all the conversion automatically.

### Light Theme

Example output generated with the default template.

![Chat logs displayed in Obsidian with light theme](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/light-theme-preview.jpg)

### Dark Theme

![Chat logs displayed in Obsidian with dark theme](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/dark-theme-preview.jpg)

### Group Chat Names & Stickers

![Group chat names and stickers displayed in Obsidian](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/group-chat-stickers.jpg)

### Italic & Bold Enhancements

Text wrapped in `（）` (parentheses for action descriptions) is automatically italicized. If `！` or `？` appears more than twice in a row, it's bolded. A little polish ✨

![Action descriptions in parentheses with italic formatting](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/italic-formatting-example-1.jpg)

![Exclamation/question marks bolded when used more than twice](https://raw.githubusercontent.com/qinu321/linshe-chat-exporter/main/images/italic-formatting-example-2.jpg)

### More Details

If you're interested, check out [Chatbox](https://github.com/qinu321/Chatbox-for-Obsidian) for a full explanation. It also includes a generator that makes editing dialogue-style code a breeze!


## Export Tips

In my testing, batch-exporting 14,000+ messages with 1,000+ images (compressed to AVIF) took about 2 minutes — pretty fast!

Note that image deduplication checks by filename only. Even if you regenerate a character's portrait in LinShe, the old image won't be replaced during re-export since the filename is the same. Manually replace if needed.

Markdown deduplication checks both filename and file size. If both match, the file is skipped. If the filename matches but the size differs, a serial number is appended before exporting.


---

## Acknowledgements

Huge thanks to Bing Le, the creator of LinShe, for developing such a fun AI chat application!

My obsession with LinShe is what sparked the idea for this exporter.

And a big thank you to Big D for the code development! It burned through a lot of tokens and we fixed many bugs, but it actually works!

Note: Only the chat exporter was written by DeepSeek. The `chatbox.css` and its generator were hand-crafted by me.