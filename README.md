# jquery-compat: Restore deprecated features for jQuery 1.9+

This project can be used to detect and restore APIs, features or functionality that have been deprecated in jQuery and removed as of version 1.9. They include:

* `jQuery.browser` [docs](http://api.jquery.com/jquery.browser)
* `jQuery.fn.andSelf()` [docs](http://api.jquery.com/andSelf)
* `jQuery.sub()` [docs](http://api.jquery.com/jquery.sub)
* `jQuery.fn.toggle()` [docs](http://api.jquery.com/toggle-event/) (_event click signature only_)
* `"hover"` pseudo-event name [docs](http://api.jquery.com/on/)
* `jQuery.fn.error()` [docs](http://api.jquery.com/error/)
* `ajaxStart, ajaxSend, ajaxSuccess, ajaxError, ajaxComplete, ajaxStop` global events on non-`document` targets [docs](http://api.jquery.com/category/ajax/global-ajax-event-handlers/)
* Use of `attrChange`, `attrName`, `relatedNode`, `srcElement` on the `Event` object (use `Event.originalEvent.attrChange` etc. instead)
* `jQuery.fn.attr()` using the `pass` argument (undocumented)
* `jQuery.attrFn` object (undocumented)
* `jQuery.fn.data()` data events (undocumented)
* `jQuery.fn.data("events")` to retrieve event-related data (undocumented)

See the [warnings](https://github.com/jquery/jquery-compat/blob/master/warnings.md) page for more information regarding messages the plugin generates.

In your web page, make sure to load this plugin *after* the script for jQuery:

```html
<script src="http://code.jquery.com/jquery-1.8.3.js"></script>
<script src="http://code.jquery.com/jquery-compat-0.0.0.js"></script>
```

The plugin can be included with versions of jQuery as old as 1.6.4 as a migration tool to identify potential upgrade issues. However, the plugin is only required for version 1.9 or higher to restore deprecated and removed functionality.

## Development vs. Production versions

To make it easier for jQuery developers to find and remove deprecated functionality, the development version of the plugin displays warnings on the browser's console. In browsers that don't support the console interface such as IE7, no messages are generated unless you include a debugging library such as [Firebug Lite](https://getfirebug.com/firebuglite) before including the jQuery Compat plugin. Developers can also inspect the `jQuery.compatWarnings` array to see what error messages have been generated.

All warnings generated by this plugin start with the string "JQCOMPAT". A list of the warnings you may see are in [warnings.md](https://github.com/jquery/jquery-compat/blob/master/warnings.md).

### Development version

This version provides console warning messages when deprecated and/or removed APIs are used. Use this version during development and debugging, and whenever you are reporting bugs to the jQuery team.

**Latest released development version:** This file is hosted on jQuery's CDN, and can be hotlinked if desired.
[http://code.jquery.com/jquery-compat-0.0.0.js](http://code.jquery.com/jquery-compat-0.0.0.js)

**Current work-in-progress build:** Although this file represents the most recent updates to the plugin, it may not have been thorougly tested.
[http://code.jquery.com/jquery-compat-git.js](http://code.jquery.com/jquery-compat-git.js)

### Production version

The minified production file is compressed and does not generate console warnings.  Do not use this file for development or debugging, it will make your life miserable.

**Latest released production version:**
[http://code.jquery.com/jquery-compat-0.0.0.min.js](http://code.jquery.com/jquery-compat-0.0.0.min.js)
 This file is hosted on jQuery's CDN, and can be hotlinked if desired.

**Current work-in-progress build:** Although this file represents the most recent updates to the plugin, it may not have been thorougly tested. We do not recommend using this file on production sites since it may be unstable; use the released production version above.
[http://code.jquery.com/jquery-compat-git.min.js](http://code.jquery.com/jquery-compat-git.min.js)

## Compat Plugin API

This plugin adds two properties to the `jQuery` object that can be used programmatically control and examine its behavior:

`jQuery.compatWarnings`: This property is an array of string warning messages that have been generated by the code on the page, in the order they were generated. Messages appear in the array only once, even if the condition has occurred multiple times, unless `jQuery.compatReset()` is called.

`jQuery.compatReset()`: This method clears the `jQuery.compatWarnings` array and "forgets" the list of messages that have been seen already.

## Reporting problems

Any bugs should be reported on the [jQuery Core bug tracker](http://bugs.jquery.com/) and *must* be accompanied by an executable test case that demonstrates the bug. The easiest way to do this is via an online test tool such as [jsFiddle.net](http://jsFiddle.net/) or [jsbin.com](http://jsbin.com). You can this [this jsFiddle template](http://jsfiddle.net/DUwny/) or [this jsbin template](http://jsbin.com/emuwuy/1/) as a starting point; they already contain links to the work-in-progress versions of both jQuery and the jQuery Compat plugin. Add your code there and post a link to it with your bug report.


How to run the tests:
====================================================
Clone this repo, install `grunt`:

```sh
git clone git://github.com/jquery/jquery-browser.git
cd jquery-browser
npm install -g grunt
```

Run `grunt` to `lint`, `test` and `min` release.

```sh
grunt
```

