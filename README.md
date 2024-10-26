# Shuukimori 🍂 &nbsp; [![bluebuild build badge](https://github.com/abdoeeeelr/shuukimori/actions/workflows/build.yml/badge.svg)](https://github.com/abdoeeeelr/shuukimori/actions/workflows/build.yml)

> 秋季森 / 秋期森 (_shuukimori_) : 
> autumn forest. "秋季/秋期" (_shuuki_, autumn season/period) is because this project started in October, while "森" (_mori_, forest) is a reference to rpm-ostree being... well, 'forest of trees'. [^1]
[^1]: I use "秋季/秋期" instead of "秋" because it's sounds prettier (also, Japanese speaker pls correct me if I'm wrong)

This image aims to improve Fedora Kinoite for more consistent KDE experience, although I might add more non-improvement stuff here, as time goes on.

### List of changes made:
- Replaced IBus with Fcitx5, for better integrations with KDE/Qt ecosystem.
  - Also replaced Anthy with better-maintained Mozc
- Added all Noto Sans Variable fonts.
- Added [Starship](https://starship.rs) (for terminal prompt ricing) and [fastfetch](https://github.com/fastfetch-cli/fastfetch) (obligatory). 🚀
- Added [fish shell](https://fishshell.com) <><3
- Added fix for mouse cursors being Adwaita (the fallback one) in some apps (i.e. [Minecraft as a Flatpak](https://www.reddit.com/r/kde/comments/13ddktm/mouse_cursor_changing_when_over_some_apps_when/)), now it defaults to Breeze Dark. [^2]
- Replaced `gnome-ssh-askpass` with `ksshaskpass`
- and many to come, I guess...?

[^2]: The only caveat is the cursor size become smaller at that affected apps ~~(Cursors in Wayland is hell)~~

## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build (rebasing from Kinoite is recommended):

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/abdoeeeelr/shuukimori:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/abdoeeeelr/shuukimori:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

  Add `-nvidia` after `shuukimori` if you're using Nvidia GPU.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/abdoeeeelr/shuukimori
```

## Credits
- [Maple Leaves on Shrine wallpaper](https://unsplash.com/photos/red-leaves-on-gray-concrete-fence-w2CWOAij-q0)
- [Kurama Line in Autumn wallpaper](https://unsplash.com/photos/blue-train-in-the-middle-of-the-forest-0q9YhC5oZbY)
