```bash
# atualizar pacotes e atualizar
sudo apt update
sudo apt upgrade -y

# php
sudo apt install software-properties-common ca-certificates lsb-release apt-transport-https -y
sudo LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
sudo apt update
sudo apt install php8.2 php8.2-mysql php8.2-mbstring php8.2-xml php8.2-curl php8.2-zip -y 

# instalar composer
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer

```