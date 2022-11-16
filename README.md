# swiss-army-knife

---

```shell
# first make setup on this tutorial https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
echo -e "\ndeb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" | sudo tee -a /etc/apt/sources.list
sudo apt update && sudo apt upgrade -y
sudo apt install git vim tmux tmuxinator xclip apt-transport-https ca-certificates curl gnupg-agent software-properties-common yarn build-essential libssl-dev docker-ce docker-ce-cli containerd.io -y
sudo docker run hello-world
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
git clone --bare https://github.com/jean-bonilha/.dotfiles.git $HOME/.dotfiles
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
dotfiles config --local status.showUntrackedFiles no
curl -o- https://raw.githubusercontent.com/junegunn/fzf/0.35.0/install | sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
nvm install 8.17.0
nvm install 10.19.0
nvm install 12.16.0
npm i -g npm
npm install -g @vue/cli
cd
rm -rf .vim
rm -rf .tmux
git clone https://github.com/jean-bonilha/.vim.git
git clone https://github.com/jean-bonilha/.tmux.git
ln -sf .vim/.vimrc
ln -sf .tmux/.tmux.conf
touch .vimrc.local 
touch .tmux.conf.local
echo 'nnoremap j jzz' >> .vimrc.local
echo 'nnoremap <Down> jzz' >> .vimrc.local
echo 'nnoremap k kzz' >> .vimrc.local
echo 'nnoremap <Up> kzz' >> .vimrc.local
echo 'nnoremap G Gzz' >> .vimrc.local
echo "let g:minimap_highlight='MoreMsg'" >> .vimrc.local
echo '' >> .vimrc.local
echo '" emmet-vim settings' >> .vimrc.local
echo "let g:user_emmet_mode='a'" >> .vimrc.local
echo '"enable all function in all mode.' >> .vimrc.local
echo "let g:user_emmet_expandabbr_key='<Tab>'" >> .vimrc.local
cp .tmux/.tmux.conf.local .
cd .vim
git checkout heavenly
git submodule init && git submodule update
cd
mkdir -p ~/Web/srv
cd Web/srv && git clone https://github.com/laradock/laradock.git
cd laradock
git checkout v9.7
rm -rf .git
git init
git a .
git status
git commit -m 'Init'
cp env-example .env
cp .env .env.backup
git a .
git status
git commit -m 'Cria backup das configuracoes de ambiente'
mkdir -p ~/Web/pro/laravel
cd ~/Web/pro/laravel
pwd >> ~/Web/srv/laradock/.env
cd ~/Web/srv/laradock
git status
docker-compose up -d nginx mysql phpmyadmin workspace 
docker-compose ps
```
