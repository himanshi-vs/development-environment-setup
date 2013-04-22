
# Development Environment Setup

* Improve command line with zsh and oh-my-zsh:

    ```bash
    sudo apt-get install zsh
    curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
    exit
    ```

* Change the oh-my-zsh theme so you can differentiate it from local terminal if you're on a server.

    ```bash
    vim ~/.zshrc
    ```

    ```diff
    # Set name of the theme to load.
    # Look in ~/.oh-my-zsh/themes/
    # Optionally, if you set this to "random", it'll load a random theme each
    # time that oh-my-zsh is loaded.
    +ZSH_THEME="gianu"
    -ZSH_THEME="robbyrussell"
    ```

    ```bash
    . ~/.zshrc
    ```

* Configure git:

    ```bash
    git config --global user.name "Your Name Here"
    git config --global user.email "your_email@example.com"
    ```

* Generate a new SSL pair and add it to Github:

    ```bash
    cd ~/.ssh
    ssh-keygen -t rsa -C "your_email@example.com"
    vim id_rsa.pub
    ```

* Setup vim with NERDTree and other plugins:

    ```bash
    sudo apt-get install ruby rubygems
    sudo gem install rake
    cd ~/
    git clone https://github.com/niftylettuce/.vim.git
    cd .vim
    make install
    sudo apt-get install xclip
    ```

* Install JSHint for linting code and install a default config file in home directory:

    ```bash
    npm install -g jshint
    cd ~/
    wget https://raw.github.com/niftylettuce/development-environment-setup/master/.jshintrc
    ```


## Credits

* <https://help.github.com/articles/set-up-git>
* <https://help.github.com/articles/generating-ssh-keys>
* <https://github.com/robbyrussell/oh-my-zsh>
* <https://github.com/robbyrussell/oh-my-zsh/wiki/themes>
* <https://github.com/jshint/jshint>
