# rofi-1pass

Custom script for Rofi that allows you to copy passwords from your 1Password vaults. Based on the
wonderfully simple [rofi-lpass](https://github.com/Mange/rofi-lpass) by Magnus Bergmark.

## Features

* List all your entries
* Copy password of an entry
* Copy username / email of an entry
* Copy URL (if entry has an URL)
* Open URL (if entry has an URL)

## Dependencies

In order to support interactive login (where `rofi-1pass` will prompt you for your password if you
don't currently have a session active), you will need `pinentry-x11`, which is part of [GnuPG](https://www.gnupg.org/),
which is part of virtually every distribution.

## Installation

1. Make sure you have the [1Password command-line tool](https://support.1password.com/command-line-getting-started/)
installed, with `op` on your `PATH`.
2. Symlink the script to somewhere on your `$PATH`: `ln -s $(pwd)/rofi-1pass ~/bin/rofi-1pass`.
3. If you _don't_ have `pinentry-x11`, make sure your environment has an active `OP_SESSION`.
Alternatively, you can put the output of `op signin` into `~/.op/session` where it will be
automatically sourced.
4. Run rofi with this as a custom script: `rofi -modi 1pass:rofi-1pass -show 1pass`.

## License

Copyright © 2018 Adrian Petrescu. Code released under the MIT license.
