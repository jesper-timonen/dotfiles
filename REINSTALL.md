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
