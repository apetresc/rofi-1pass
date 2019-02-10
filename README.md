# rofi-1pass

Custom script for Rofi that allows you to copy passwords from your 1Password vaults. Based on the
wonderfully simple [rofi-lpass](https://github.com/Mange/rofi-lpass) by Magnus Bergmark.

## Features

* List all your entries
* Copy password of an entry
* Copy username / email of an entry
* Generate 2FA OTP of an entry (if entry has 2FA set up)
* Copy URL (if entry has an URL)
* Open URL (if entry has an URL)
* Interactive password prompt with configurable `PINENTRY_PROGRAM`

## Non-Features

* Creating or editing new entries through rofi

## Dependencies

* [1Password command-line tool](https://support.1password.com/command-line-getting-started/) for connecting to 1Password
* [jq](https://stedolan.github.io/jq/) for parsing the JSON output of the 1Password CLI
* [xclip](https://github.com/astrand/xclip) for putting the selected entries onto your X11 clipboard

In order to support interactive login (where `rofi-1pass` will prompt you for your password if you
don't currently have a session active), you will need a [pinentry](https://www.gnupg.org/related_software/pinentry/index.html)
program, which are usually part of [GnuPG](https://www.gnupg.org/), present in virtually every distribution.

The default pinentry program is `pinentry-x11`. If you prefer to use another, like [pinentry-rofi](https://gist.github.com/sardemff7/759cbf956bea20d382a6128c641d2746),
just set the `PINENTRY_PROGRAM` environment variable.

All of the above need to be on your `PATH` when running `rofi-1pass`. They are present in
most package managers.

## Installation

1. Symlink the script to somewhere on your `$PATH`: `ln -s $(pwd)/rofi-1pass ~/bin/rofi-1pass`.
2. If you _don't_ have `pinentry`, make sure your environment has an active `OP_SESSION`.
Alternatively, you can put the output of `op signin` into `~/.op/session` where it will be
automatically sourced.
3. Run rofi with this as a custom script: `rofi -modi 1pass:rofi-1pass -show 1pass`.

### Arch Linux

On Arch, the AUR has a [rofi-1pass](https://aur.archlinux.org/packages/rofi-1pass/) PKGBUILD.

## License

Copyright © 2018 Adrian Petrescu. Code released under the MIT license.
