# Preparar ambiente na digital ocean

## atualizar pacotes e atualizar
```bash
sudo apt update
sudo apt upgrade -y
```
## instalar php
```bash
sudo apt install software-properties-common ca-certificates lsb-release apt-transport-https -y
sudo LC_ALL=C.UTF-8 -y
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update
sudo apt install php8.3 php8.3-mysql php8.3-mbstring php8.3-xml php8.3-curl php8.3-zip php8.3-sqlite3 -y 
```
## instalar composer
```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```