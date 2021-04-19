# BetterDiscord-Animated-Status

* [Installation](#Installation)
* [Usage](#Usage)
* [Settings](#Settings)
	* [Timeout](#Timeout)
	* [The Editor](#The-Editor)
	* [Emojis](#Emojis)
		* [Regular Emoji](#Regular-Emoji)
		* [Nitro Emoji](#Nitro-Emoji)
	* [Custom JavasSript](#Custom-JavaScript)

## Installation
Install using the very convenient [BetterDiscord installer](https://github.com/BetterDiscord/Installer/releases/latest) \
Download [animated-status.plugin.js](/animated-status.plugin.js?raw=true) into the following directory \
Mac: `~/Library/Preferences/BetterDiscord`\
Windows: `%appdata%\BetterDiscord\plugins`\
Linux: `~/.config/BetterDiscord/plugins`

## Usage
Open Discord, go to Settings\>Plugins, enable AnimatedStatus and click on Settings.\
Enter the required information into the input fields and click the `save` button.
Clicking `done` without saving will discard your settings.

## Settings
<img src="Screenshots/Settings.png">

### Timeout
The value specifies the length of each animation step in milliseconds.
Example: With a timeout of 2000, the following animation would take 4 seconds to complete, as 2 keyframes last 2 seconds each.
```
abc
def
```
To prevent the discord server from being spammed with requests, the minimum allowed timeout is hardcoded to be 2.9 seconds. \
Logically, the animation timeout should be at least `2900`, at best `10000` milliseconds (10 seconds) for the animation to look smooth on other clients. \
In the mobile app, the status isn't updated consistently, i.e. the list of server members is updated based on the users actions in the app. Don't be surprised, if the animation doesn't appear smooth, or skips frames. \
^ According to [@pintoso](https://github.com/pintoso)

### The Editor
In the latest version, the decision was made to remove the raw editor from the plugin. It was merely an unstable textual interface to the JSON config file. \
**You can still use the RAW-Mode**, by editing Clicking `Open Plugins Folder` inside the settings editing `AnimatedStatus.config.json`. This is at your own risk, you might break stuff.
Due to a request, the editor will not remove empty cells anymore. You can use empty cells to unset your status.

### Emojis
#### Regular Emoji
Use an emoji selector (Windows: <kbd>Win</kbd>+<kbd>.</kbd>). \
Alternatively, use [a unicode table](https://unicode.org/emoji/charts/full-emoji-list.html) and copy the emoji you'd like to have as your status. \
The `emoji_name` field **may not contain whitespace**. Otherwise, the discord server will silently ignore your status request. \
Due to uncertainties nitro emoji names, the plugin does currently not automatically remove whitespace.

#### Nitro Emoji
- Open a discord Chat, type `\`.
<img src="Screenshots/nitro0.png">
- Select the emoji you want to include in your status using the emoji picker.
<img src="Screenshots/nitro1.png">
- Notice that the message changed to `<:emojiname:emojiid>`. The values inside the brackets (emojiname and emojiid) are the values required for the status.
<img src="Screenshots/nitro2.png">
- Edit the settings accordingly
<img src="Screenshots/nitro3.png">

### Custom JavaScript
Have the current time as your status:
```
eval let fmt=t=>(t<10?'0':'')+t;let d=new Date();`${fmt(d.getHours())}:${fmt(d.getMinutes())}:${fmt(d.getSeconds())}`;
```
Have the current time with the corresponding clock symbol as your current status
```
eval let fmt=t=>(t<10?'0':'')+t;let d=new Date();`${fmt(d.getHours())}:${fmt(d.getMinutes())}:${fmt(d.getSeconds())}`;", "eval ['🕛','🕐','🕑','🕒','🕓','🕔','🕕','🕖','🕗','🕘','🕙','🕚'][((new Date()).getHours()%12)];
```