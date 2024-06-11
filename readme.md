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

## Update GIT
```bash
add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

## PHP
```bash
sudo apt update
sudo apt upgrade

sudo apt install software-properties-common ca-certificates lsb-release apt-transport-https -y
sudo LC_ALL=C.UTF-8
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update -y 

sudo apt install php7.4 php7.4-mysql php7.4-mbstring php7.4-xml php7.4-curl php7.4-zip php7.4-sqlite3 -y 

sudo apt install php8.0 php8.0-mysql php8.0-mbstring php8.0-xml php8.0-curl php8.0-zip php8.0-sqlite3 -y 

sudo apt install php8.1 php8.1-mysql php8.1-mbstring php8.1-xml php8.1-curl php8.1-zip php8.1-sqlite3 -y 

sudo apt install php8.2 php8.2-mysql php8.2-mbstring php8.2-xml php8.2-curl php8.2-zip php8.2-sqlite3 -y 

sudo apt install php8.3 php8.3-mysql php8.3-mbstring php8.3-xml php8.3-curl php8.3-zip php8.3-sqlite3 -y

php -v
```

### Alternar versão de PHP
```bash
# Alterar versão do PHP para php7.4
sudo a2dismod php7.4
sudo a2dismod php8.0
sudo a2dismod php8.1
sudo a2dismod php8.2
sudo a2dismod php8.3
sudo update-alternatives --set php /usr/bin/php7.4
sudo a2enmod php7.4
sudo systemctl restart apache2
php -v

# Alterar versão do PHP para php8.0
sudo a2dismod php7.4
sudo a2dismod php8.0
sudo a2dismod php8.1
sudo a2dismod php8.2
sudo a2dismod php8.3
sudo update-alternatives --set php /usr/bin/php8.0
sudo a2enmod php8.0
sudo systemctl restart apache2
php -v

# Alterar versão do PHP para php8.1
sudo a2dismod php7.4
sudo a2dismod php8.0
sudo a2dismod php8.1
sudo a2dismod php8.2
sudo a2dismod php8.3
sudo update-alternatives --set php /usr/bin/php8.1
sudo a2enmod php8.1
sudo systemctl restart apache2
php -v

# Alterar versão do PHP para php8.2
sudo a2dismod php7.4
sudo a2dismod php8.0
sudo a2dismod php8.1
sudo a2dismod php8.2
sudo a2dismod php8.3
sudo update-alternatives --set php /usr/bin/php8.2
sudo a2enmod php8.2
sudo systemctl restart apache2
php -v

# Alterar versão do PHP para php8.3
sudo a2dismod php7.4
sudo a2dismod php8.0
sudo a2dismod php8.1
sudo a2dismod php8.2
sudo a2dismod php8.3
sudo update-alternatives --set php /usr/bin/php8.3
sudo a2enmod php8.3
sudo systemctl restart apache2
php -v

# Escolher versão do php pelo menu
sudo update-alternatives --config php
```

## Composer
```bash
sudo apt update
sudo apt upgrade

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```

## MariaDB
```bash
sudo apt update
sudo apt upgrade
sudo apt install mariadb-server -y
sudo mysql_secure_installation
# Enter current password for root (enter for none): Enter
# Switch to unix_socket authentication: Y
# Change root password: N
# Remove anonymous users? Y
# Disallow root login remotely? Y
# Remove test database and access to it? Y
# Reload privilege tables now? Y
```

## Criar usuário no mariadb
```bash
mysql -u root -p
GRANT ALL ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```

## Alterar senha do root no mariadb
```bash
mysql -u root
ALTER USER 'root'@'localhost' IDENTIFIED BY 'novaSenha';
FLUSH PRIVILEGES;
exit;
```

## instalação phpmyadmin
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

## dar permissões para a pasta html e phpmyadmin
```bash
sudo chmod -R 777 /var/www/html/
sudo chmod -R 755 /var/www/html/phpmyadmin
```

## alterar arquivos para acesso local
```bash
sudo nano /etc/apache2/sites-enabled/000-default.conf
sudo nano /etc/hosts
systemctl restart apache2
```

## dar permissão para endereços web amigáveis
```bash
sudo nano /etc/apache2/apache2.conf
```
```html
Alterar:
De:
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

Para:
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
```

## Habilitar modo de reescrita do apache
```bash
sudo a2enmod rewrite
```

## Node
```bash
# Instalar nvm e Node com opções de gerenciamento da versão
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

# Habilitar o nvm
source ~/.profile

# Listar as versões instaladas
nvm ls

# Listar versões disponíveis para instalação
nvm ls-remote

# Instalar a versão desejada
nvm install vX.X.X

# Para instalar a versão mais recente basta
nvm install node

# Para remover uma versão instalada
nvm uninstall vX.X.X

# Para trocar a versão a ser utiliada
nvm use vX.X.X

# Caso deseje nomear as versões para facilitar a troca entre versões
nvm alias meunome vX.X.X
nvm use meunome

# Para remver um nome para a versão
nvm unalias meunome

# Definir uma versão como padrão
nvm alias default vX.X.X

# Verificar a versão atual
nvm current
```

# Preparar ambiente da digital ocean
```bash
# listar chaves ssh no seu computador
ls -la ~/.ssh

# gerar uma chave pública e privada no computador local
ssh-keygen

# desvincular conexões antigas de uma conexão
ssh-keygen -R seuIp

# conectar no servidor ssh
ssh root@seuIp
# conectar no servidor ssh informando uma porta específica
ssh root@seuIp -p numeroDaPorta
# conectar no servidor ssh informando uma chave ssh específica
ssh root@seuIp -i nomeDaChave

# Após conectar no servidor
# Adicionar usuário no sistema
adduser seuUsuario
# Copiar chave ssh para a pasta do usuário criado
cp -r ~/.ssh /home/seuUsuario/
# Alterar permissões da pasta do usuário criado
sudo chown -R seuUsuario:seuUsuario /home/seuUsuario/.ssh
```