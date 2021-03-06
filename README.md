# BitBar Xbox Feed Plugin [![Build Status](https://travis-ci.org/kodie/bitbar-xboxfeed.svg?branch=master)](https://travis-ci.org/kodie/bitbar-xboxfeed)
A plugin for [BitBar](https://github.com/matryer/bitbar) that shows your [Xbox Live](https://live.xbox.com) friend's recent activity.

![](/screenshot.png?raw=true)

## Requirements
* [Node.js](https://nodejs.org)
* [npm](https://npmjs.com)

## Installation

### via [BitBar CLI](https://github.com/kodie/bitbar-cli)
```
bitbar install Games/xboxfeed.10m.js
```

### Manually
```
bitbar://openPlugin?title=Xbox%20Feed&src=https://raw.githubusercontent.com/kodie/bitbar-xboxfeed/master/xboxfeed.10m.js
```

## Setup
1. After installing the plugin, click on the Xbox icon in your menu bar and select "Run Installation".
2. Go to https://xboxapi.com and create a free account.
3. Connect your Xbox Live account to your newly created Xbox API account and you should receive an API key.
4. Open `~/.bitbarrc` in your favorite text editor (create the file if it doesn't exist already).
5. Insert the following and save:
```
[xboxfeed]
apiKey=YOUR API KEY HERE
```

Refresh the plugin and enjoy!

## Settings
Along with your apiKey, other settings can be defined in your `~/.bitbarrc` file:

* `apiKey` - Your Xbox API Key
	* Default: (Blank)
	* Example: `apiKey=c9ff119073ea2567730fb42e3a4fe805`
	* **Required**

* `color` - Text color
  * Default: `false` (System default)
  * Example 1: `color=green`
  * Example 2: `color=#5dc21e`
  * Setting to false will use the system default
  * Color names or HEX values can be used

* `font` - Text font
  * Default: `false` (System default)
  * Example: `font=Georgia`
  * Setting to false will use the system default

* `size` - Text size
  * Default: `false` (System default)
  * Example: `size=24`
  * Setting to false will use the system default

* `length` - Number of characters before the text is truncated
  * Default: `false`
  * Example: `length=70`
  * Setting to false will disable truncating

* `limit` - Max number of recent activity notifications to show
  * Default: `25`
  * Example: `limit=50`

* `imgSize` - User image size in pixels
  * Default: `18`
  * Example: `imgSize=50`
  * Setting to false will disable user images display
  * Can be any number from 1-50

* `cachePath` - Directory path to store user images cache
  * Default: `/tmp/xboxfeed`
  * Example: `cachePath=/some/other/folder`
  * Setting to false will disable user image caching (and will slow down the plugin)
  * Plugin will attempt to create the folder if it doesn't already exist

* `cacheExpire` - Number of milliseconds before a user image should be re-downloaded
  * Default: `86400000` (24 hours)
  * Example: `cacheExpire=604800000`

## Troubleshooting
### Could not connect to API
The plugin couldn't connect to the xboxapi.com servers. This means that either their servers are down, Xbox Live servers are down, or you are having internet connectivity problems.

### A fresh login is required to gain a new token from Microsoft
The xpiapi.com servers were unable to authorize your Xbox Live account. This means that you need to log into your xboxapi.com account and reconnect your Xbox Live account. If this happens often you may want to consider checking the "Remember Me" box when connecting your account.

### User images aren't showing up
If user images aren't showing up and you are sure that you don't have `imgSize` set to `false` then this means that the plugin ran into problems when trying to save the images to `cachePath`. You can either disable image caching by setting `cachePath` to `false` or try to figure out why the plugin couldn't save the images to the specified path. I would start by manually creating the folder that `cachePath` is set to.

## License
MIT. See the License file for more info.
