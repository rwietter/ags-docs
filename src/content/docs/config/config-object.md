---
title: Config Object
---

When you start `ags`, it will try to `import` the `default` `export`
from a module which defaults to `~/.config/ags/config.js`.
Even if you mutate this object after initialization,
the config **will not be reloaded**.

```js
// config.js
export default {
    closeWindowDelay: {
        'window-name': 500, // milliseconds
    },
    notificationPopupTimeout: 5000, // milliseconds
    notificationForceTimeout: false,
    cacheNotificationActions: false,
    maxStreamVolume: 1.5, // float
    cacheCoverArt: true,

    onConfigParsed: function() {
        // code that runs after this object is loaded
    }

    style: App.configDir + '/style.css',
    windows: [
        // Array<Gtk.Window>
    ],
};
```

## The exported config object

| Field | Type | Description |
|-------|------|-------------|
| `closeWindowDelay` | `Record<string, number>` | Delays the closing of a window, this is useful for making animations with a revealer
| `notificationPopupTimeout` | `number` | How long should a notification be flagged for popup
| `notificationForceTimeout` | `boolean` | Force `notificationPopupTimeout` and ignore timeout set by notifications
| `cacheNotificationActions` | `boolean` | Whether to cache notification actions, so that they can be reloaded
| `maxStreamVolume` | `number` | Maximum possible volume on an Audio Stream
| `cacheCoverArt` | `boolean` | Whether to cache mpris cover arts. `true` by default
| `onConfigParsed` | `(app: App) => void` | Callback to execute after all user modules were resolved.
| `style` | `string` | Path to a css file.
| `windows` | `Array<Gtk.Window>` | List of [Windows](./widgets#window).
