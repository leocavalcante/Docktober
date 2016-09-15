# Docktober
### Simple: [Docker](https://www.docker.com/) + [OctoberCMS](http://octobercms.com/)

#### It uses the:
- official [mysql:5.7 image](https://hub.docker.com/_/mysql/) as database (but you can change to pgsql for example),
- official [php:fpm image](https://hub.docker.com/_/php/) to run PHP over [FastCGI](https://en.wikipedia.org/wiki/FastCGI)
- and the official Apache [httpd image](https://hub.docker.com/_/httpd/) as web/proxy server.

#### How to

##### From scratch

1. `git clone https://github.com/octobercms/october.git my-app`
2. `cd my-app`
3. `git clone https://github.com/leocavalcante/Docktober.git .docker`
4. `docker-compose -f .docker/docker-compose.yml up -d --build`
5. `docker exec docker_php_1 composer install`

Here you should already be seeing October's demo theme at `http://<YOUR_DOCKER_MACHINE_IP>:8000`.<br>
And you can work with it as a [flat-file CMS](https://vimeo.com/172202661)

**if you want some database power**

1. `docker exec docker_php_1 php artisan october:env`
2. Set `.env`'s `DB_HOST` to `db` and add some `DB_PASSWORD`
3. `docker-compose -f .docker/docker-compose.yml up -d --build`
4. `docker exec docker_php_1 php artisan october:up`

Now you should be able to access `http://<YOUR_DOCKER_MACHINE_IP>:8000/backend` and enjoy OctoberCMS.
