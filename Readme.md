
# Development Environment Setup

* Set the default Monospace font to Inconsolata and install MS Core Fonts

    ```bash
    sudo apt-get install ttf-inconsolata ttf-mscorefonts-installer
    ```

    > Open "Font Settings" and set Monospace font to 11pt Inconsolata Medium

* Install Chromium

    ```bash
    sudo apt-get install chromium-browser
    ```

* Install [git][git]:

    ```bash
    sudo apt-get update && sudo apt-get install git-core curl build-essential openssl libssl-dev
    ```

* Install [node][node]:

    ```bash
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs
    ```

* Install [ab][ab]:

    ```bash
    sudo apt-get install apache2-utils
    ```

* Increase the limit of sockets and open files to 20000.  This allows us to run benchmark tests such as:

    ```bash
    ab -r -n 1000000 -c 10000 http://localhost/
    ```

    ```bash
    sudo vim /etc/security/limits.conf
    ```

    ```diff
    +*                hard    nofile          20000
    +*                soft    nofile          20000

    # End of file
    ```

    ```bash
    sudo vim /etc/pam.d/common-session
    ```

    ```diff
    # and here are more per-package modules (the "Additional" block)
    session required  pam_unix.so
    +session required  pam_limits.so

    # end of pam-auth-update config
    ```

    ```bash
    sudo reboot
    ```

* Improve command line with vim, zsh and [oh-my-zsh][oh-my-zsh]:

    ```bash
    sudo apt-get install vim zsh
    chsh -s /bin/zsh
    zsh
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

* Install [mongodb][mongodb]:

    ```bash
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
    sudo vim /etc/apt/sources.list.d/10gen.list
    ```

    ```conf
    deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
    ```

    ```bash
    sudo apt-get update
    sudo apt-get install mongodb-10gen
    ```

* Install [redis][redis]:

    ```bash
    sudo apt-get install redis-server
    ```

* Install [elasticsearch][elasticsearch]:

    ```bash
    cd ~/
    sudo apt-get install openjdk-7-jre-headless -y
    wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-0.20.6.deb
    sudo dpkg -i elasticsearch-0.20.6.deb
    ```

* Install [imagemagick][imagemagick]:

    ```bash
    sudo apt-get install imagemagick
    ```

* Install [phantomjs][phantomjs]

    ```bash
    sudo apt-get install build-essential chrpath git-core libssl-dev libfontconfig1-dev
    cd ~/
    git clone https://github.com/ariya/phantomjs.git
    cd phantomjs
    git checkout 1.9
    ./build.sh
    ```

[imagemagick]: http://www.imagemagick.org/script/index.php
[phantomjs]: https://github.com/ariya/phantomjs
[elasticsearch]: http://www.elasticsearch.org/download/
[redis]: http://redis.io/
[mongodb]: http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/
[git]: http://git-scm.com/
[node]: http://nodejs.org/
[ab]: http://zgadzaj.com/benchmarking-nodejs-basic-performance-tests-against-apache-php
[oh-my-zsh]: https://github.com/robbyrussell/oh-my-zsh
[zsh-themes]: https://github.com/robbyrussell/oh-my-zsh/wiki/themes
[git-configure]: https://help.github.com/articles/set-up-git
[generate-ssl-pair]: https://help.github.com/articles/generating-ssh-keys
[vim-setup]: https://github.com/niftylettuce/.vim
[jshint]: https://github.com/jshint/jshint
[git-extras]: https://github.com/visionmedia/git-extras
