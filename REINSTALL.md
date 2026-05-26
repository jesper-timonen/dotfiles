# Post-Wipe Reinstall Plan

## 1. Xcode CLI Tools
```bash
xcode-select --install
```

## 2. Homebrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 3. Brew Packages
```bash
brew install zsh zsh-autosuggestions zsh-syntax-highlighting \
  fd ripgrep jq tree wget unzip \
  git gh neovim make \
  nvm rust python \
  felixkratz/formulae/borders

brew install --cask raycast ghostty aerospace
```

## 4. Dotfiles
```bash
git clone git@github.com:jesper-timonen/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
stow aerospace zsh .config
```

## 5. Oh-My-Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Re-stow after — installer overwrites `.zshrc`:
```bash
cd ~/.dotfiles && stow -R zsh
```

## 6. Node (via nvm)
```bash
nvm install --lts
```

## 7. Manual App Installs
- Firefox
- LinearMouse
- REAPER
- Spotify
- Stats
- Steam

## 8. Post-Install Notes

**Zsh as default shell** — set brew's zsh as default:
```bash
echo $(brew --prefix)/bin/zsh | sudo tee -a /etc/shells
chsh -s $(brew --prefix)/bin/zsh
```

**Node before Neovim** — install Node via nvm before launching nvim. LSP servers require `npm` in PATH:
```bash
nvm install --lts
```

**Neovim** — lazy.nvim auto-installs plugins on first launch. Requires `make` and C compiler (Xcode CLI tools covers this).

**Borders** — start as a service after install:
```bash
brew services start borders
```

**AeroSpace** — grant Accessibility permissions in System Settings on first launch.

**LinearMouse** — grant Accessibility and Input Monitoring permissions on first launch.

**nvm** — verify `.zshrc` sources nvm from the correct brew path after install.
