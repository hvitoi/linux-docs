# zsh

## Installation

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Plugins

- <https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins>
- <https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins>

- Enabling plugins

```sh
vi ~/.zshrc
```

```conf
plugins=(
  git
  bundler
  dotenv
  osx
  rake
  rbenv
  ruby
)
```

## Themes

```conf
ZSH_THEME="robbyrussell" # Default theme
ZSH_THEME="agnoster" # fancy
```

```conf
ZSH_THEME="random" # random on each start
ZSH_THEME_RANDOM_CANDIDATES=(
  "robbyrussell"
  "agnoster"
)
ZSH_THEME_RANDOM_IGNORED=(pygmalion tjkirch_mod)
```

## Installation folder

- `~/.oh-my-zsh`

```sh
echo $ZSH
```
