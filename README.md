##.plan

### 2016-12-02

  * Got vim-pandoc setup after Chris showed me the light. Changed my .vimrc to change the tabbing on pandoc filetypes to 4 spaces after both Chris and I ran into issues where rendering a markdown file to pdf with Pandoc did not indent the nested bullets correctly.
  * Started this thing. Going to try public on Github for a while. It will prevent me from putting work sensitive information on here, but I think I can be very generic in those regards.
  * Grabbed Neverwinter Nights for free on gog.com. Love that game! Spent some time getting wine setup on my Mac and actually got NWN to run. I probably should have documented the steps, but I pretty much followed this [excellent tutorial](https://www.davidbaumgold.com/tutorials/wine-mac/).
  * Just pushed the initial commit of this file, and github doesn't do well with the 4 space indent. It interpreted this list as a code block. I commented out the autocmd for now. I will have to figure this out in the future.

### 2016-12-05
  * Setting up my new MBP at work and figured I should document what I did to setup a brand new clean environment:
    * Common steps:
      * The box builder guy at work already had Chrome and iTerm2 installed so I didn't have to start with these.
      * Turned on the lower right hot corner to turn on my screen saver. Security was already setup to lock the screen when the screen saver comes on.
      * Used Airdrop to move over my private and public ssh keys from my other work box. I know you shouldn't do this, but the Ops team here encourages it because it is very hard to get them to distribute a new public key for you. I made sure the .ssh dir is mode 700 and the keys were 600 for the private and 644 for the public.
      * Used Airdrop to move over my password database file. Installed [KeePassX](https://www.keepassx.org/).
      * Installed Dropbox, and then pointed KeePass to my dropbox password database and deleted the password database I copied over.
      * Installed [Homebrew](http://brew.sh/) and installed the following:
        * fish
        * wget
        * vim
        * git
        * go
        * tmux
        * ctags
        * cmake
        * pandoc
        * Caskroom/cask/mactex
        * cask install font-hack (*Not sure why this is different?*)
        * Caskroom/cask/virtualbox
        * Caskroom/cask/vagrant
        * Caskroom/cask/postman
      * Change the default profile on iterm2 to use the font hack at 12pt regular.
      * Cloned my [dotfiles](https://github.com/pneisen/dotfiles) from Github.
        * `cd ~/dotfiles; ./setup.sh`
        * `cd ~/dotfiles/vim/plugged/YouCompleteMe; ./install.py --clang-completer --gocode-completer`
      * Download and install [Adium](https://adium.im/). Will need a new [Google App Password](https://security.google.com/settings/security/apppasswords).
      * Install Chrome extensions:
        * [cVim](https://chrome.google.com/webstore/detail/cvim/ihlenndgcmojhcghmfjfneahoeklbjjh)
        * [Markdown Reader](https://chrome.google.com/webstore/detail/markdown-reader/gpoigdifkoadgajcincpilkjmejcaanc)
        * [Sourcegraph](https://chrome.google.com/webstore/detail/markdown-reader/gpoigdifkoadgajcincpilkjmejcaanc)
      * Download and install [f.lux](https://justgetflux.com/).
      * Migrate documents, files, etc.
    * Work only steps
      * Download and install [SQL Developer](http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html).
        * Copy over oracle files from the old mac.
      * Download and install [Mattermost](https://about.mattermost.com/download/#mattermostApps).
      
### 2016-12-06
  * Ran into an issue compiling YouCompleteMe on Ubuntu. Cmake could not find the pythonlibs. `sudo apt-get install python-dev` fixed it up.
