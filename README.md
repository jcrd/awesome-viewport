# awesome-viewport

awesome-viewport is a library for [Awesome](https://github.com/awesomeWM/awesome)
window manager that manages tags based on viewports.

## Installation

```
$ git clone https://github.com/jcrd/awesome-viewport.git
$ cd awesome-viewport
$ luarocks make --local rockspec/awesome-viewport-devel-1.rockspec
```

## Usage

Require the library:
```lua
local viewport = require("awesome-viewport")
```

Connect to a screen to begin managing its tags:
```lua
screen.connect_signal("request::desktop_decoration",
  function (s)
      viewport.connect(s)
  end)
```

View a single tag:
```lua
tag1:view_only()
```

This tag will be the new viewport.

Get the viewport for the focused screen:

```lua
viewport()
```

Toggle another tag into view:
```lua
awful.tag.viewtoggle(tag2)
```

`tag1` will remember that `tag2` is toggled while its the viewport, so that if
the viewport changes and `tag1` is re-viewed, `tag2` will also be toggled into
view.

See the [API documentation](https://jcrd.github.io/awesome-viewport/) for
descriptions of all functions.

## License

awesome-viewport is licensed under the GNU General Public License v3.0 or later
(see [LICENSE](LICENSE)).
