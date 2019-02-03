# rofi-1pass

Custom script for Rofi that allows you to copy passwords from your 1Password vaults. Based on the
wonderfully simple [rofi-lpass](https://github.com/Mange/rofi-lpass) by Magnus Bergmark.

## Features

* List all your entries
* Copy password of an entry
* Copy username / email of an entry
* Copy URL (if entry has an URL)
* Open URL (if entry has an URL)

## Installation

1. Make sure you have the [1Password command-line tool](https://support.1password.com/command-line-getting-started/)
installed, with `op` on your `PATH`.
2. Make sure your session is signed into your 1Password vault already (`rofi-1pass` does not yet
support interactive signin).
3. Symlink the script to somewhere on your `$PATH`: `ln -s $(pwd)/rofi-1pass ~/bin/rofi-1pass`.
4. Run rofi with this as a custom script: `rofi -modi 1pass:rofi-1pass -show 1pass`.

## Usage
To use rofi-1pass with i3, or when executing via a keyboard shortcut that does not have access to your environment, you can do the following:
1. Pipe the results of op signin $subdomain to ~/.op/session like so:
```shell
$ op signin my > ~/.op/session
```
2. Run rofi

## License

Copyright © 2018 Adrian Petrescu. Code released under the MIT license.
