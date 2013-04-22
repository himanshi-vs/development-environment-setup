
# Development Environment Setup

* Improve command line with zsh and [oh-my-zsh][oh-my-zsh]:

    ```bash
    sudo apt-get install zsh
    curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
    exit
    ```

* Change the [oh-my-zsh theme][zsh-themes] so you can differentiate it from local terminal if you're on a server.

    ```bash
    vim ~/.zshrc
    ```

    ```diff
    # Set name of the theme to load.
    # Look in ~/.oh-my-zsh/themes/
    # Optionally, if you set this to "random", it'll load a random theme each
    # time that oh-my-zsh is loaded.
    +ZSH_THEME="lambda"
    -ZSH_THEME="robbyrussell"
    ```

    ```bash
    . ~/.zshrc
    ```

* Configure git with [your information][git-configure]:

    ```bash
    git config --global user.name "Your Name Here"
    git config --global user.email "your_email@example.com"
    ```

* Generate a new SSL pair and [add it to Github][generate-ssl-pair]:

    ```bash
    cd ~/.ssh
    ssh-keygen -t rsa -C "your_email@example.com"
    vim id_rsa.pub
    ```

* Setup vim with [NERDTree and other plugins][vim-setup]:

    ```bash
    sudo apt-get install ruby rubygems
    sudo gem install rake
    cd ~/
    git clone https://github.com/niftylettuce/.vim.git
    cd .vim
    make install
    sudo apt-get install xclip
    ```

* Install [jshint][jshint] for linting code on save and install a default config file in home directory:

    ```bash
    npm install -g jshint
    cd ~/
    wget https://raw.github.com/niftylettuce/development-environment-setup/master/.jshintrc
    ```

* Install [git-extras][git-extras] for writing shorter git commands using aliases:

    ```bash
    cd /tmp && git clone --depth 1 https://github.com/visionmedia/git-extras.git && cd git-extras && sudo make install
    ```


[oh-my-zsh]: https://github.com/robbyrussell/oh-my-zsh
[zsh-themes]: https://github.com/robbyrussell/oh-my-zsh/wiki/themes
[git-configure]: https://help.github.com/articles/set-up-git
[generate-ssl-pair]: https://help.github.com/articles/generating-ssh-keys
[vim-setup]: https://github.com/niftylettuce/.vim
[jshint]: https://github.com/jshint/jshint
[git-extras]: https://github.com/visionmedia/git-extras
