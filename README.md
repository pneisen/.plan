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
          * `ln -s /usr/local/texlive/2016/bin/x86_64-darwin/pdflatex /usr/local/bin`
          * `ln -s /usr/local/texlive/2016/bin/x86_64-darwin/xelatex  /usr/local/bin`
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
          * Check *Allow access to file URLs*
          * Associate .md files with Chrome in finder
        * [Sourcegraph](https://chrome.google.com/webstore/detail/markdown-reader/gpoigdifkoadgajcincpilkjmejcaanc)
      * Download and install [f.lux](https://justgetflux.com/).
      * Migrate documents, files, etc.
    * Work only steps
      * Download and install [SQL Developer](http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html).
        * Copy over oracle files from the old mac.
      * Download and install [Mattermost](https://about.mattermost.com/download/#mattermostApps).

### 2016-12-06
  * Ran into an issue compiling YouCompleteMe on Ubuntu. Cmake could not find the pythonlibs. `sudo apt-get install python-dev` fixed it up.

### 2016-12-12
  * Chris sent me this gem: [Vimwiki](http://vimwiki.github.io/). Looks pretty neat, I want to play with it and see if I could use it.
  * [vim-pandoc](https://github.com/vim-pandoc/vim-pandoc) isn't caught up to the 1.18 version of Pandoc on Homebrew. This breaks some things like generating the pdf from within Vim using a command like this: `:Pandoc pdf -V geometry=margin=0.5in -V mainfont=Arial -V fontsize=12pt`
  * I also noticed that vim-pandoc remaps your jk keys to work with soft wraps, but it doesn't do line end and line start. I will have to add those myself.
  * Worked on a fish shell function for managing my .plan editing. It is going to:
    * Check to see if the .plan repo has been cloned. If not, clone it in the usual spot
    * pushd the current directory and move to the .plan directory
    * Pull down the latest .plan from Github
    * Open the README.md in vim
    * Check to see if I made any changes: `git diff --shortstat 2> /dev/null | tail -n1`
    * If changes, commit using the date in the commit message.
    * Push to Github.
    * popd back to the previous directory

### 2016-12-13
  * Finished up my .plan fish function. The source is here: [.plan.fish](https://github.com/pneisen/dotfiles/blob/master/config/fish/functions/.plan.fish)
  * Fish's caching of settings bit me today. I was changing functions and not seeing the changes. I had to delete the ~/.config/fish/fishd* file to have it refresh the settings. I will look for a better way, but this works for now.
    * I figured this out. A `source ~/.config/fish/config.fish` will do the trick. I added an abbreviation named *reload* that does this.
  * I don't know that lib/pq-timeouts is needed now that Go 1.8 supports contexts for sql drivers. I'm going to have to look more into this. #todo

### 2016-12-14
  * Read a few quotes off [Cat-v](http://cat-v.org/) that I loved and were inspiring to me:
    * "Only the mediocre are always at their best." -- Jean Giraudoux
    * "Eventually, I decided that thinking was not getting me very far and it was time to try building." -- Rob Pike
    * "Share your knowledge. It’s a way to achieve immortality." -- Dalai Lama
  * The *reload* abbreviation isn't going to work. Forgot that *reload* is an upstart command.
    * Fixed this. Changed it to *fish_reload*.

### 2016-12-15
  * Keith sent me this [xkcd comic](http://xkcd.com/1768/). Some good advice there.
  * Chris and I were both looking for a way to color or underline links in a pandoc generated pdf. I found the urlcolor option for LaTeX. This is how I am generating pdfs now: `pandoc -V geometry=margin=0.5in -V mainfont=Arial -V fontsize=12pt -V urlcolor=cyan -f markdown_github -o test.pdf test.md`
  * Read a Hacker News comment about Urgency vs Importance. He example was planning things ahead and getting tickets so you don't get caught up in chores, etc. You can lose a random Saturday to your todo list, but if you have tickets to fly to Europe, that is going to take precedence. Makes me think I need to plan some camping and activities now for this summer.
