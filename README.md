# awesome-viewport

awesome-viewport is a library for [Awesome](https://github.com/awesomeWM/awesome)
window manager that manages tags based on viewports.

## Installation

```
$ git clone https://github.com/jcrd/awesome-viewport.git
$ cd awesome-viewport
$ luarocks make --local rockspec/awesome-viewport-devel-1.rockspec
```

## Concept

Once connected to a screen, selecting a single tag will make that tag the active
viewport. This tag will remember any other selected tags when the viewport
changes, so that when it is re-selected, all previously selected tags are
viewed.

For example:

![Tag 1 is selected, becoming the active viewport][1]

* Tag 1 is selected, becoming the active viewport.

![Tag 2 is toggled into view][2]

* Tag 2 is toggled into view. Tag 1, as the active viewport, will record this.

![Tag 2 is selected, but tag 1 is not viewed][3]

* If tag 2 is selected, it becomes the new active viewport, and tag 1 will not be
  viewed. The association is one way.

![Tag 1 is selected, toggling tag 2 into view][2]

* Tag 1 is re-selected, becoming the active viewport. Because tag 2 was viewed
  when tag 1 was previously the active viewport, it is toggled back into view.

[1]: https://github.com/jcrd/awesome-viewport/blob/assets/1.png
[2]: https://github.com/jcrd/awesome-viewport/blob/assets/2.png
[3]: https://github.com/jcrd/awesome-viewport/blob/assets/3.png

## Usage

Require the library:
```lua
local viewport = require("awesome-viewport")
```

Connect to a screen to begin managing its tags:
```lua
awful.screen.connect_for_each_screen(function (s)
      viewport.connect(s)
  end)
```

View a single tag:
```lua
tag1:view_only()
```

This tag will be the active viewport.

Get the active viewport for the focused screen:

```lua
viewport()
```

Toggle another tag into view:
```lua
awful.tag.viewtoggle(tag2)
```

`tag1` will remember that `tag2` is toggled while its the active viewport, so
that if the viewport changes and `tag1` is re-viewed, `tag2` will also be
toggled into view.

See the [API documentation](https://jcrd.github.io/awesome-viewport/) for
descriptions of all functions.

## License

This project is licensed under the MIT License (see [LICENSE](LICENSE)).
