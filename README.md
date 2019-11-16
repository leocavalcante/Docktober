# Docktober
### Simple: [Docker](https://www.docker.com/) + [OctoberCMS](http://octobercms.com/)

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=E4F45BFVMFVQW)

#### It uses the:
- official [mysql:5.7 image](https://hub.docker.com/_/mysql/) as database (but you can change to pgsql for example),
- official [php:fpm image](https://hub.docker.com/_/php/) to run PHP over [FastCGI](https://en.wikipedia.org/wiki/FastCGI)
- and the official Apache [httpd image](https://hub.docker.com/_/httpd/) as web/proxy server.

#### How to

##### From scratch

1. `git clone https://github.com/octobercms/october.git my-app`
2. `cd my-app`
3. `git submodule add https://github.com/leocavalcante/Docktober.git .docker`
4. `docker-compose -f .docker/docker-compose.yml up -d --build`
5. `docker-compose -f .docker/docker-compose.yml exec php composer install`

Here you should already be seeing October's demo theme at `http://<YOUR_DOCKER_MACHINE_IP>:8000`.<br>
And you can work with it as a [flat-file CMS](https://vimeo.com/172202661).<br>

##### If you want some database power

1. `docker-compose -f .docker/docker-compose.yml exec php php artisan october:env`
2. Set `.env`'s `DB_HOST` to `db` and add some value for `DB_PASSWORD`
3. `docker-compose -f .docker/docker-compose.yml up -d --build`
4. `docker-compose -f .docker/docker-compose.yml exec php php artisan october:up`

Now you should be able to access `http://<YOUR_DOCKER_MACHINE_IP>:8000/backend` and enjoy full OctoberCMS.

**Recommendation:** rename [`container_name`](https://docs.docker.com/compose/compose-file/#/container-name) at `.docker/docker-compose.yml` to something meaningful.
