# init-loader.el

`init-loader.el` is based on [tarao's fork version](https://gist.github.com/tarao/4362564).


## What is it ?

`init-loader.el` is a loader of configuration files.

You can seperate configuration files easily by `init-loader.el`.


## Sample code

````elisp
(require 'init-loader)

;; Load configuration files in '/path/to/init-directory'.
(init-loader-load "/path/to/init-directory")

;; If you omit arguments, then `init-loader.el' loads from `init-loader-directory'
(init-loader-load)
````

## Order of loading

`init-loader.el` loads configuration files by following rules.

1. Configuration files which start with two digits. Small number file is loaded earlier than large number file.

  e.g. "00_utils.el" "01_ik-cmd.el" "21_javascript.el" ... "99_global-keys.el"

2. Windows specific configuration files if system is Windows. First load files that start with 'windows-'. Second load files that start with 'meadow-'

  e.g. "windows-fonts.el", "windows-system.el", "meadow-commands.el", "meadow-fonts.el"

3. MacOSX specific configuration files if system is MacOSX. First load files that start with 'carbon-'. Second load files that start with 'cocoa-'

  e.g. "carbon-applescript.el", "cocoa-fonts.el", "cocoa-plist.el"

4. No window Emacs specific configuration files which start with 'nw-'

  e.g. "nw-config.el", "nw-key.el"


## interfaces

Show loading log messeage

    M-x init-loader-show-log


## Customize

Configuration files directory(Default is '~/.emacs.d/init')

    init-loader-directory

Show log message after initializing if this value is non-nil(Default is `t`)

    init-loader-show-log-after-init

Byte-Compile configuration files if this value is non-nil(Default is `nil`)

    init-loader-byte-compile

## Hooks

Call hooks before byte-compiling configuration file if `init-loader-byte-compile` is non-nil

    init-loader-before-compile-hook
