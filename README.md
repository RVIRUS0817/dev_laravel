# dev_laravel

![スクリーンショット 2020-12-19 13 16 24](https://user-images.githubusercontent.com/5633085/102680644-77f4df00-41fd-11eb-9f15-fc1a36eb88cc.jpg)


- docker images
  - app-laravel
    - php:7.4-fpm-alpine (nginx,php-fpm,supervisor)
  - mysql-57
    - mysql:5.7


- git clone or fork

```
mkdir -p ~/git/github
cd ~/git/github
git clone git@github.com:RVIRUS0817/dev_laravel.git
```

- add localhost /etc/hosts

```
sudo vim /etc/hosts
127.0.0.1 dev.adachin.com
```

- docker run

```
cd dev_laravel
cp .env.example .env
cd docker/dev
docker-compose up -d
```

- app deploy

```
docker exec -it laravel-app bash

composer install
php artisan key:generate
php artisan config:cache
php artisan migrate
/usr/bin/supervisorctl restart app
``` 

- Access

http://dev.adachin.com/


![スクリーンショット 2020-12-19 13 41 49](https://user-images.githubusercontent.com/5633085/102680880-fe122500-41ff-11eb-9562-d284dd369142.jpg)


- DB login

```
docker exec -it app-laravel bash
mysql -u root -h db -p
```

## How to download Laravel app

```
composer global require laravel/installer

laravel new app
or
composer create-project --prefer-dist laravel/laravel app
```

