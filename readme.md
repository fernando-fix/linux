## Redefinir senha root

```bash
sudo passwd root
```

## Google chrome

```bash
sudo apt update
sudo apt upgrade
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Snap
```bash
sudo apt update
sudo apt upgrade
sudo apt install snapd
```
## Visual Studio Code
```bash
sudo apt update
sudo apt upgrade
sudo snap install code --classic
```

## PHP
```bash
sudo apt update
sudo apt upgrade

sudo apt install software-properties-common ca-certificates lsb-release apt-transport-https
sudo LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php 
sudo apt update

sudo apt install php7.4 
sudo apt install php7.4-mysql php7.4-mbstring php7.4-xml php7.4-curl 

sudo apt install php8.1 
sudo apt install php8.1-mysql php8.1-mbstring php8.1-xml php8.1-curl 

sudo apt install php8.2 
sudo apt install php8.2-mysql php8.2-mbstring php8.2-xml php8.2-curl 

sudo apt install php8.3 
sudo apt install php8.3-mysql php8.3-mbstring php8.3-xml php8.3-curl

php -v
```

### Alternar versão de PHP
```bash
# Alterar de php7.4 para php8.3
sudo update-alternatives --set php /usr/bin/php8.3
sudo a2dismod php7.4
sudo a2enmod php8.3
sudo systemctl restart apache2

# Alterar de php8.3 para php7.4
sudo update-alternatives --set php /usr/bin/php7.4
sudo a2dismod php8.3
sudo a2enmod php7.4
sudo systemctl restart apache2

# Escolher versão do php pelo menu
sudo update-alternatives --config php
```

## Composer
```bash
sudo apt update
sudo apt upgrade

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e21205b207c3ff031906575712edab6f13eb0b361f2085f1f1237b7126d785e826a450292b6cfd1d64d92e6563bbde02') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

sudo mv composer.phar /usr/local/bin/composer
```

## MariaDB
```bash
sudo apt update
sudo apt upgrade
sudo apt install mariadb-server
sudo mysql_secure_installation
```

## phpmyadmin
```bash
wget -P Downloads https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.tar.gz
wget -P Downloads https://files.phpmyadmin.net/phpmyadmin.keyring
cd Downloads
gpg --import phpmyadmin.keyring
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.tar.gz.asc
gpg --verify phpMyAdmin-latest-all-languages.tar.gz.asc
mkdir /var/www/html/phpmyadmin
tar xvf phpMyAdmin-latest-all-languages.tar.gz --strip-components=1 -C /var/www/html/phpmyadmin
cp /var/www/html/phpmyadmin/config.sample.inc.php /var/www/html/phpmyadmin/config.inc.php
nano /var/www/html/phpmyadmin/config.inc.php
chmod 660 /var/www/html/phpmyadmin/config.inc.php
chown -R www-data:www-data /var/www/html/phpmyadmin/
systemctl restart apache2
```

## Alterar senha do root no phpmyadmin
```bash
mysql -u root
ALTER USER 'root'@'localhost' INDENTIFIED BY 'novaSenha';
```

## dar permissões para a pasta html
```bash
sudo chmod -R 777 /var/www/html/ 
```

## alterar arquivos para acesso local
```bash
sudo nano /etc/apache2/sites-enabled/000-default.conf
sudo nano /etc/hosts
systemctl restart apache2
```