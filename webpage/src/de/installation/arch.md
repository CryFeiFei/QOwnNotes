# Installieren Sie unter Arch Linux

## Arch User Repository (AUR)

Alternativ gibt es auch ein offizielles Package für QOwnNotes auf AUR, es heißt `qownnotes`.

Sie finden es hier: [QOwnNotes auf AUR](https://aur.archlinux.org/packages/qownnotes)

Synchronisieren Sie Ihre Package-Datenbank und installieren Sie das Package mit `yay`:

```bash
yay -S qownnotes
```

::: tip
Falls Sie den Prozess beschleunigen möchten, interessiert Sie vielleicht [CCACHE und AUR](https://www.reddit.com/r/archlinux/comments/6vez44/a_small_tip_if_you_compile_from_aur/).
:::

## pacman

::: warning
[OBS](https://build.opensuse.org/package/show/home:pbek:QOwnNotes/desktop) scheint momentan Probleme auf Arch Linux zu haben. Nutzen Sie am besten einfach AUR oder den [Applmage](./appimage.md).
:::

Fügen Sie die folgenden Zeilen zu Ihrem `/etc/pacman.conf` mit `sudo nano /etc/pacman.conf` hinzu:

```ini
[home_pbek_QOwnNotes_Arch_Extra]
SigLevel = Optional TrustAll
Server = http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Arch_Extra/$arch
```

Führen Sie die folgenden Befehle aus, um dem Repository zu vertrauen:

```bash
wget http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Arch_Extra/x86_64/home_pbek_QOwnNotes_Arch_Extra.key -O - | sudo pacman-key --add -
sudo pacman-key --lsign-key F2205FB121DF142B31450865A3BA514562A835DB
```

Falls der Befehl `sudo pacman-key --lsign-key F2205FB121DF142B31450865A3BA514562A835DB` mit einer Nachricht wie `ERROR: FFC43FC94539B8B0 could not be locally signed.` fehlschlägt, könnten Sie zunächst die tatsächliche *keyid* des heruntergeladenen Schlüssels herausfinden, d.h. mit dem Befehl (und Output):

```bash
gpg /path/to/downloaded/home_pbek_QOwnNotes_Arch_Extra.key
gpg: WARNING: no command supplied.  Trying to guess what you mean ...
pub   rsa2048 2019-07-31 [SC] [expires: 2021-10-10]
      F2205FB121DF142B31450865A3BA514562A835DB
uid           home:pbek OBS Project <home:pbek@build.opensuse.org>
```

Sie können nun Ihre Package-Datenbank synchronisieren und das Package mit `pacman` installieren:

```bash
sudo pacman -Syy qownnotes
```

[Direkter Download](https://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Arch_Extra)

::: tip
Sie können das Repository natürlich auch mit anderen Arch-basierten Distributionen verwenden, wie Manjaro.
:::
