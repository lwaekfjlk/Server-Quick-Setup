How to set up your raw server account at the quickest speed?

## Anaconda Install ( when you are in zsh, ensure install process will modify .zshrc)

1. wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

2. run this sh
3. select the installation address and do conda init according to the installation guide
4. if you use zsh, need to copy >>> conda init >>> part shell code into .zshrc

### OhMyZsh Install

1. sudo apt-get install zsh (if there is no zsh on the server)
2. git clone https://github.com.cnpmjs.org/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
3. cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
4. chsh -s /bin/zsh
5. reboot
6. ～/.zshrc ZSH_THEME="jonathan" (or other themes)
7. plugins=(git sublime vscode extract tmux zsh-syntax-highlighting zsh-autosuggestions)
8. git clone https://github.com.cnpmjs.org/zsh-users/zsh-syntax-highlighting.git
9. mv zsh-syntax-highlighting/ $ZSH_CUSTOM/plugins/
10. git clone https://github.com.cnpmjs.org/zsh-users/zsh-autosuggestions.git
11. mv zsh-autosuggestions/ $ZSH_CUSTOM/plugins/

### OhMyTmux Install

1. sudo apt-get install tmux (install tmux if there is no tmux on the server)
2. git clone https://github.com.cnpmjs.org/gpakosz/.tmux.git
3. ln -s -f .tmux/.tmux.conf
4. cp .tmux/.tmux.conf.local . (notice there is one dot at the end which means the current directory)
5. add one line (set -g mouse on) in .tmux.conf.local file (if you use tmux 1.x)
6. add two line 1st line is (set-option -g mouse on) and 2nd line is
       (bind -n WheelUpPane if-shell -F -t = "#{mouse_any_flag}" "send-keys -M" "if -Ft= '#{pane_in_mode}' 'send-keys -M' 'copy-mode -e'") (if you use tmux 2.x)

### NeoVim Install

1. wget https://github.com.cnpmjs.org/neovim/neovim/releases/download/v0.4.3/nvim-linux64.tar.gz

2. tar -zxvf nvim-linux64.tar.gz

3. add the /bin file in the neovim into .zshrc as part of \$PATH    export PATH=\$HOME/path_to_nvim/nvim-linux64/bin:\$PATH

4. source ~/.zshrc

5. install neovim configuration

6. python3 -m pip install --user --upgrade pynvim 

   1. easy way

      Since the install of install.sh can be quite difficult due to the existence of GFW, we provide a complete file to be put under ~/.config/nvim in order to directly use NeoVim

      BaiduPan to Download nvim.zip to unzip and put under  ~/.config as a /nvim subfile

      链接: https://pan.baidu.com/s/1oXcHtykRPB2Ws7UIQKnLWA  密码: lu60

      After that, you still need to download neovim-init.vim and run install.sh until the process of plugin installing in order to download some necessary packagess.
   2. hard way

      1. modify the corresponding install.sh in the neovim-init.vim
         1. pip install -> pip3 install to prevent protential problems
         2. if having trouble downloading when :PlugInstall, choose to do Step7 below
      2. sh install.sh
      3. Since PlugInstall would have problems downloading, we copy the files under /.config/plugged and put these files into the same plugged/ file 
      4. Change init.vim under /.config/nvim/ to allow jj and line number display
         1. let map leader=','
         2. inoremap jj <Esc>`^
         3. set number
         4. set cindent
         5. set smartindent
         6. set ruler

### CPU/GPU show 
1. pip install gpustat [under base env]
2. add "alias gpu='~/anaconda3/bin/gpustat -i 1 --color'" into ~/.zshrc
3. hostnamectl   to check the version of linux
   if is ubuntub-based : sudo apt install epel-release , then we can sudo apt-install htop
   if is centos-based  : sudo yum install epel-release, then we can sudo yum htop
   
### Big File Transfer Notice
1. use df -h to check the NVM/HDD/SSD mount location
2. put huge files into /NVM /HDD mount location
