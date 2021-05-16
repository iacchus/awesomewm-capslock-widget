# A simple CAPS LOCK widget for Awesome

(fork from https://github.com/stefano-m/awesome-capslock_widget)

(**See also** the [AwesomeWM Num Lock widget](https://github.com/iacchus/awesomewm-numlock-widget))

Useful when you have a keyboard that does not have a CAPS LOCK indicator.

This widget is really simple and parses the output of `xset` to figure out
whether CAPS LOCK is active or not. (Hint: you need the `xset` utility for this
widget to work)

This script is simple and you can edit the file `init.lua` if you want to change
it.

# Installation

1. Ensure that `xset` is available to you on your system.
2. Clone this repository in your `~/.config/awesome/` folder.
   ```
   cd ~/.config/awesome/
   git clone git@github.com:iacchus/awesomewm-capslock-widget.git
   ```
3. Refer to **Usage** (below.) and follow it's three steps.
4. Restart Awesome (e.g. press `modkey + Control + R` or run `awesome-client
   "awesome.restart()"` from a terminal).

# Usage

For **Awesome 4.x**, add the following to your `~/.config/awesome/rc.lua`:

``` lua
-- FIRST. If you just cloned the repo in ~/.config/awesome/ require the module
--          at the beginning of the file (anywhere there should be ok.):
local capslock = require("awesomewm-capslock-widget")

-- etcetc... more config here...

-- SECOND. Add the widget to the wibox: Look for "-- Right widgets",
--           as shown below, and add the line `capslock,` where you want to
--           see the widget (pay attention to the ending commas `,`):
    s.mywibox:setup {

      -- more config here...

      { -- Right widgets
        layout = wibox.layout.fixed.horizontal,
        wibox.widget.systray(),
        capslock,
-- more config here

-- THIRD. Add the keybinding to `global_keys` so that the widget can change state
--          on keypress, by adding the line `capslock.key` there:
--
-- {{{ Key bindings
local globalkeys = awful.util.table.join(
  capslock.key,
-- more config follows
```

Now, when CAPS LOCK is active, an uppercase letter **A** will be displayed

![active_capslock screenshot](/screenshots/active_capslock_widget.png?raw=true)

when CAPS LOCK is inactive, a lowecase letter **a** will be displayed:

![inactive_capslock screenshot](/screenshots/inactive_capslock_widget.png?raw=true)

These can be changed by changing the `activated` and `deactivated`
attributes of the widget as
[Pango markup](https://developer.gnome.org/pygtk/stable/pango-markup-language.html)
strings. You will probably need to adjust the `forced_width` attribute too.

For example:

``` lua
local capslock = require("capslock")
capslock.forced_width = 35
capslock.activated = "<u>CAPS</u>"
capslock.deactivated = "<u>caps</u>"
```

When the mouse is over the widget, a tooltip that says `Caps Lock on`/`Caps
Lock off` is also shown.

# Contributing

If you have ideas about how to make this better, feel free to open an issue or
submit a pull request.
