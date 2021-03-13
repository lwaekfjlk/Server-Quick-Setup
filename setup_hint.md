How to set up your raw server account at the quickest speed?

## Anaconda Install

1. wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

2. run this sh
3. conda init ( we need to init this conda and allow us to do conda activate )

### OhMyZsh Install

1. sudo apt-get install zsh (if there is no zsh on the server)
2. git clone https://github.com.cnpmjs.org//robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
3. cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
4. chsh -s /bin/zsh
5. reboot
6. ～/.zshrc ZSH_THEME="jonathan" (or other themes)
7. plugins=(git sublime vscode rand-quote extract tmux zsh-syntax-highlighting zsh-autosuggestions)
8. git clone https://github.com.cnpmjs.org/zsh-users/zsh-syntax-highlighting.git
9. mv zsh-syntax-highlighting/ $ZSH_CUSTOM/plugins/
10. git clone https://github.com.cnpmjs.org/zsh-users/zsh-autosuggestions.git
11. mv zsh-autosuggestions/ $ZSH_CUSTOM/plugins/

### OhMyTmux Install

1. sudo apt-get install tmux (install tmux if there is no tmux on the server)
2. git clone https://github.com.cnpmjs.org/gpakosz/.tmux.git
3. ln -s -f .tmux/.tmux.conf
4. cp .tmux/.tmux.conf.local . (notice there is one dot at the end which means the current directory)
5. add (set -g mouse on) in .tmux.conf.local file

### NeoVim Install

1. wget https://github.com.cnpmjs.org/neovim/neovim/releases/download/v0.4.3/nvim-linux64.tar.gz
2. tar -zxvf nvim-linux64.tar.gz
3. add the /bin file in the neovim into .zshrc as part of $PATH

4. source ~/.zshrc
5. modify the corresponding install.sh in the neovim-init.vim
   1. pip install -> pip3 install to prevent protential problems
   2. if having trouble downloading when :PlugInstall, choose to do Step7 below
6. sh install.sh
7. Since PlugInstall would have problems downloading, we copy the files under /.config/plugged and put these files into the same plugged/ file 
8. Change init.vim under /.config/nvim/ to allow jj and line number display
   1. let map leader=','
   2. inoremap jj <Esc>`^
   3. set number
   4. set cindent
   5. set smartindent
   6. set ruler