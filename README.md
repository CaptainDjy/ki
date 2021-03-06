# Ki

[![Build Status](https://travis-ci.com/andweeb/ki.svg?branch=master)](https://travis-ci.com/andweeb/ki) [![codecov](https://codecov.io/gh/andweeb/ki/branch/master/graph/badge.svg)](https://codecov.io/gh/andweeb/ki)

> A proof of concept to apply the ["Zen" of vi](https://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118) to desktop automation.

### What's that?

Ki introduces a novel approach to automating macOS. Inspired by the [vi](https://en.wikipedia.org/wiki/Vi#Interface) text editor, Ki enables composable commands to execute desktop tasks to see whether it can be effective in automating the desktop environment.

From the default resting `desktop` state, enter `normal` mode with the default hotkey <kbd>⌘⎋</kbd> (Command and Escape), where an extensive set of command chains become available to achieve various workflows:
- <kbd>⌘⎋</kbd><kbd>⌘e</kbd><kbd>s</kbd> - enter `entity` mode <kbd>⌘e</kbd> and open or focus the **Safari** <kbd>s</kbd> application
- <kbd>⌘⎋</kbd><kbd>⌘a</kbd><kbd>Space</kbd><kbd>s</kbd> - enter `action` mode <kbd>⌘a</kbd> and toggle media <kbd>Space</kbd> in the frontmost **Safari** <kbd>s</kbd> window
- <kbd>⌘⎋</kbd><kbd>⌘s</kbd><kbd>s</kbd><kbd>⌘3</kbd> - enter `select` mode <kbd>⌘s</kbd> and focus a specific **Safari** <kbd>s</kbd> tab, the third one <kbd>⌘3</kbd> from the left

With those semantics in mind, we can intuit other "sentences" if we know other entities <kbd>g</kbd>, <kbd>m</kbd>, and <kbd>⇧s</kbd>:
- <kbd>⌘⎋</kbd><kbd>⌘e</kbd><kbd>g</kbd> - enter `entity` mode <kbd>⌘e</kbd> and open or focus the **Google Chrome** <kbd>g</kbd> application
- <kbd>⌘⎋</kbd><kbd>⌘a</kbd><kbd>Space</kbd><kbd>⇧s</kbd> - enter `action` mode <kbd>⌘a</kbd> and toggle the current song <kbd>Space</kbd> in the **Spotify** <kbd>⇧s</kbd> application
- <kbd>⌘⎋</kbd><kbd>⌘s</kbd><kbd>m</kbd><kbd>⌘3</kbd> - enter `select` mode <kbd>⌘s</kbd> and focus a specific **Messages** <kbd>m</kbd> conversation, the third one <kbd>⌘3</kbd> from the top

For certain applications, shortcuts can be chained even further to compose more complex workflows:
- <kbd>⌘⎋</kbd><kbd>⌘a</kbd><kbd>Space</kbd><kbd>⌘s</kbd><kbd>g</kbd><kbd>⌘4</kbd> - enter `action` mode <kbd>⌘a</kbd> to toggle media <kbd>Space</kbd>, and enter `select` mode <kbd>⌘s</kbd> to target the specific **Google Chrome** <kbd>g</kbd> tab, the fourth one <kbd>⌘4</kbd> from the left
- <kbd>⌘⎋</kbd><kbd>⌘a</kbd><kbd>w</kbd><kbd>⌘s</kbd><kbd>s</kbd><kbd>⌘2</kbd> - enter `action` mode <kbd>⌘a</kbd> to close a tab <kbd>w</kbd>, and enter `select` mode <kbd>⌘s</kbd> to target the specific **Safari** <kbd>s</kbd> tab, the second one <kbd>⌘2</kbd> from the left

To see Ki shortcuts, you can activate the **Cheatsheet** with <kbd>⌘⎋</kbd><kbd>⌘e</kbd><kbd>?</kbd>. To see all shortcuts for actions that an entity implements, you can show its **Cheatsheet** with <kbd>⌘⎋</kbd><kbd>⌘a</kbd><kbd>?</kbd><kbd>(entity)</kbd>.

## Installation

Install [Hammerspoon](http://www.hammerspoon.org) and extract [Ki.spoon.zip](https://github.com/andweeb/ki/releases/latest) to `~/.hammerspoon/Spoons`.

## Usage and Configuration

Load, configure, and start the plugin in `~/.hammerspoon/init.lua`:

```lua
hs.loadSpoon('Ki')                 -- initialize the plugin
spoon.Ki.workflowEvents = {...}    -- configure `spoon.Ki` here
spoon.Ki:start()                   -- enable keyboard shortcuts
```

Nearly everything in Ki is customizable! API documentation can be found [here](https://andweeb.github.io/ki/html/Ki.html) and usage examples [here](docs/usage-examples).

## Development

```bash
# Setup
make deps      # install local luarocks dependencies necessary for Ki
make dev-deps  # install global luarocks dev dependencies and pip requirements for the docs generator

# Development
# Prefix the target names below with `watch-` to monitor for file changes using `fswatch`
make docs      # generate source documentation
make lint      # run linter on source and spec files
make test      # run busted unit tests and generate coverage files
make dev       # build and symlink the Ki spoon to the system spoons directory for quick development
make           # build and create a spoon zip file in the `dist` folder
```
