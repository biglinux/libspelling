# libspelling for BigLinux

The Arch Linux recipe for [libspelling](https://gitlab.gnome.org/GNOME/libspelling) with one
patch, `pkgbuild/free-unused-dictionaries.patch`.

Upstream keeps every dictionary it loads until the process exits. With the patch, a dictionary is
freed when the last spell checker using it goes away, so a program that closes its last
spell-checked editor gets back the dictionary's memory: 26 to 30 MiB with the pt_BR hunspell
dictionary.

## Updating

On a new upstream release, set `pkgver`, set `pkgrel` to the Arch release followed by `.1`, rebase
the patch on the new tag and run `updpkgsums`. Retire this repository once upstream frees unused
dictionaries itself.

The package belongs in `biglinux-priority`: from any repository listed after `[extra]`, pacman
installs the Arch package instead.
