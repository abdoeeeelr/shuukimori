# **⚠️ THIS IMAGE IS STILL WIP!!! ⚠️**
# You have been warned!
---

# Shuukimori &nbsp; [![bluebuild build badge](https://github.com/blue-build/template/actions/workflows/build.yml/badge.svg)](https://github.com/blue-build/template/actions/workflows/build.yml)

秋季森 / 秋期森 (_shuukimori_) [^1]
:  autumn forest. "秋季/秋期" (_shuuki_, autumn) is because this project started in October, while "森" (_mori_, forest) is a reference to rpm-ostree.
[^1]: Please correct me if the spelling is wrong 😭 I'm not a proper Japanese speaker, just fascinated with it.

This image is built from [Universal Blue image](https://universal-blue.org), which by itself is a [Fedora Atomic](https://fedoraproject.org/atomic-desktops/) derivatives. This image aims to improve Fedora Kinoite for more consistent KDE experience.

List of changes made:
- Replaced IBus with Fcitx5, for better integrations with KDE ecosystem
- Added several Noto Sans fonts, not all, just the one with variable font support.
- Added [Starship](https://starship.rs) (for terminal prompt ricing) and [fastfetch](https://github.com/fastfetch-cli/fastfetch) (obligatory).
- Added fix for mouse cursors being Adwaita (the fallback one) in some apps (i.e. [Minecraft as a Flatpak](https://www.reddit.com/r/kde/comments/13ddktm/mouse_cursor_changing_when_over_some_apps_when/)), now it defaults to Breeze Dark.
- and many to come, I guess.

## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

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

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/blue-build/template
```
