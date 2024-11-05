# Comandos para deploy de aplicação docker em VPS

## Criar usuário caso não tenha e dar permissões sudo
```bash
sudo useradd -m -s /bin/bash fernando
sudo passwd fernando
sudo usermod -aG sudo fernando
```

## Instalar todas as dependencias e configurar docker para o usuário
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git -y
sudo apt install docker.io docker-compose -y
sudo systemctl enable --now docker docker.socket containerd
sudo usermod -aG docker fernando
su - fernando
```

## Testar se o docker foi instalado corretamente
```bash
docker --version
docker run hello-world
```

## Clonar o projeto com docker
```bash
git clone https://github.com/fernando-fix/ankivesp
cd ankivesp
cp .env.example .env
nano .env
```

## Fazer deploy da aplicação e entrar no bash
```bash
sudo docker-compose up -d
docker exec -u root -it ankivesp_app_1 bash
```

## Liberar as permissões da pasta www
```bash
chown -R www-data:www-data /var/www
chmod -R 775 /var/www
exit
```

## Entrar no usuário padrão do sistema
```bash
docker exec -it ankivesp_app_1 bash
```

## Finalizar o deploy com os comandos artisan do laravel
```bash
git config --global --add safe.directory /var/www
composer install
php artisan key:generate
php artisan migrate --seed
```

## Outros comandos docker úteis
```bash
docker exec -u root -it ankivesp_app_1 bash
docker exec -it ankivesp_db_1 bash
docker exec -it ankivesp_db_1 mysql -u root -p
sudo systemctl restart docker
docker exec -it ankivesp_app_1 bash
sudo docker-compose down -v
```
