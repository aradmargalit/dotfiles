# New Computer Setup Guide

## System Preferences
- [ ] Remove all of the junk from the dock, and pin Chrome, Outlook, and Slack
- [ ] Key Repeat: Fast with Short Delay
- [ ] Battery: Show Percentage (click on battery icon)
- [ ] Customize TouchBar: Replace Siri with Lock Icon

## System Applications
- [ ] [Spectacle](https://www.spectacleapp.com/) - Resize and locate windows with ease.
- [ ] For Outlook, disable dark mode because it's awful (for now).
    ```sh
    defaults write com.microsoft.Outlook NSRequiresAquaSystemAppearance -bool yes
    ```
- [ ] In Outlook, set "time before marking as read" to 0 seconds.
- [ ] Download and install [aText](https://www.trankynam.com/atext/), my favorite text expansion app.
- [ ] Save your :eyes:, get [flux](https://justgetflux.com/).

## Software Development

### Terminal
- [ ] Install Xcode Command Line Tools and Homebrew if you haven't already
    ```sh
    xcode-select --install
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

- [ ] Install a nice theme. I use [Spaceship Prompt](https://github.com/denysdovhan/spaceship-prompt) because I like space. :rocket:
    ```sh
    # Allow for non-default themes
    cd $ZPREZTODIR
    git clone --recurse-submodules https://github.com/belak/prezto-contrib contrib
    # Replace Sorin with "spaceship" in the .zpreztorc file
    vim ~/.zpreztorc
    # Customize the prompt to be...perfect...
    echo "export SPACESHIP_PROMPT_SEPARATE_LINE=false" >> ~/.zpreztorc
    echo "export SPACESHIP_PROMPT_ADD_NEWLINE=false" >> ~/.zpreztorc
    ```

- [ ] Replace nano with anything else
    ```sh
    echo "EDITOR=vim" >> ~/.zshrc
    git config --global core.editor "vim"
    ```

- [ ] Install [iTerm2](https://www.iterm2.com/)
- [ ] In iTerm Preferences, install a reasonable color theme. I'm currently using Solarized Dark.
- [ ] Replace cat with [bat](https://github.com/sharkdp/bat)
    ```sh
    brew install bat
    echo "alias cat=bat" >> ~/.zshrc
    ```

- [ ] We don't want anyone to [steal our commits](https://github.com/jayphelps/git-blame-someone-else), so we're signing our commits with GPG.
    First, install [GPG Tools for Mac](https://gpgtools.org/)
    ```sh
    git config --global commit.gpgsign true
    # After creating your key using the GUI, find it by running
    gpg --list-secret-keys --keyid-format LONG
    # Find the key ID after the rsa4096/ and tell Git about it
    git config --global user.signingkey {KEY_ID}
    # Export your key to the clipboard
    gpg --armor --export your@email.com | pbcopy
    # Paste the key into GitHub to add it as a recognized GPG key
    ```

- [ ] To get around faster, install [autojump](https://github.com/wting/autojump).
    ```sh
    brew install autojump
    # Add the following to your ~/.zshrc
    [ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
    ```

- [ ] To quickly fuzzy-find files on your computer, use [fzf](https://github.com/junegunn/fzf)
    ```sh
    brew install fzf
    # Optional, but useful
    /usr/local/opt/fzf/install
    ```

- [ ] Preview markdown with [grip](https://github.com/joeyespo/grip)
    ```sh
    brew install grip
    ```

- [ ] Replace cURL with [httpie](https://github.com/jakubroztocil/httpie)
    ```sh
    brew install httpie
    ```

- [ ] You'll probably want `tmux` for, you know, terminal multiplexing
    ```sh
    brew install tmux
    ```

### Packages & Languages

#### Web Development :computer:
- [ ] Install NodeJS
    ```sh
    brew install node
    ```

- [ ] Install [n](https://github.com/tj/n#installation) to easily switch between Node versions
    ```sh
    npm install -g n
    ```

- [ ] Install [Yarn](https://yarnpkg.com)
    ```sh
    brew install yarn
    ```

#### Python :snake:
- [ ] Install [Pyenv](https://github.com/pyenv/pyenv) and a version of Python :snake: 3.7.x
    ```sh
    brew install pyenv
    pyenv install 3.7.1
    # Set 3.7.1 as the default version
    pyenv global 3.7.1
    # Add this to your ~/.zshrc
    eval "$(pyenv init -)"
    ```

#### Go
- [ ] Install [GVM](A Go Version Manager)
    ```sh
    brew install go
    zsh < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
    source ~/.gvm/scripts/gvm
    ```

- [ ] Use whichever Go version you prefer as your default.
    ```sh
    gvm install go1.14.1
    gvm use go1.14.1 --default
    ```

- [ ] Set your GOPATH to `~/go`
    ```sh
    echo "export GOPATH=~/go" >> ~/.zshrc
    ```

#### Database
- [ ] For MySQL, I strongly prefer [MyCli](https://github.com/dbcli/mycli) to `mysql`.
    ```sh
    brew update && brew install mycli
    # In ~/.mclirc update the following settings
    less_chatty = True
    key_bindings = vi
    multi_line = True
    # Add to your shell profile
    export LESS="-SRXF"
    ```

#### Dev Ops
- [ ] For Terraform purposes, I recommend [tfswitch](https://warrensbox.github.io/terraform-switcher/)
    ```sh
    brew install warrensbox/tap/tfswitch
    ```

### [Visual Studio Code](https://code.visualstudio.com/download)

#### Extensions
- [ ] `markdownlint` - Highlights syntax issues in your markdown.
- [ ] `Markdown Preview Github Styling` - Because they got it right the first time. Make sure to install the extension pack to get emojis and lists.
- [ ] `Python` - Linting, debugging, syntax highlighting
- [ ] `GitLens` - Shows git histories

#### Shortcuts
- [ ] "Move Editor into Next Group"  :arrow_right:  `⌘M, ⌘ →` 
- [ ] "Move Editor into Previous Group" :arrow_right:  `⌘M, ⌘ ←`

#### Settings
- [ ] Turn on File Autosave with a 1000ms delay.

### Docker :package:
- [ ] Install [Docker](https://www.docker.com/) from [Dockerhub](https://docs.docker.com/docker-for-mac/install/)