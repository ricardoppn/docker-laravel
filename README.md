
# Setup Docker Para Projetos Laravel (8, 9 ou 10)
## Utilizando nginx, MySql, Redis, Laravel

### Passo a passo
Clone Repositório
```sh
git clone https://github.com/ricardoppn/docker-laravel.git
```

Clone os Arquivos do Laravel
```sh
git clone https://github.com/laravel/laravel.git app-laravel
```


Copie os arquivos do diretório app-laravel para o docker-laravel, criado anteriormente
```sh
cp -rf app-laravel/* docker-laravel
```
```sh
cd docker-laravel/
```


Crie o Arquivo .env
```sh
cp .env.example .env
```


Atualize as variáveis de ambiente do arquivo .env
```dosini
APP_NAME="NOME DA SUA APLICA
APP_URL=http://localhost:8989 #VERIFIQUE DISPONIBILIDADE DA PORTE EM SEU S.O

DB_CONNECTION=mysql
DB_HOST=db #NOME DO CONTAINER DO BANCO
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=root

CACHE_DRIVER=redis #NOME DO CONTAINER DO REDIS
QUEUE_CONNECTION=redis #NOME DO CONTAINER DO REDIS
SESSION_DRIVER=redis #NOME DO CONTAINER DO REDIS

REDIS_HOST=redis #NOME DO CONTAINER DO REDIS
REDIS_PASSWORD=null
REDIS_PORT=6379
```


Suba os containers do projeto
```sh
docker-compose up -d
```


Acessar o container
```sh
docker-compose exec app bash
```


Instalar as dependências do projeto
```sh
composer install
```


Gerar a key do projeto Laravel
```sh
php artisan key:generate
```


Acessar o projeto
[http://localhost:8989](http://localhost:8989)
