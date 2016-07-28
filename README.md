# Docktober
### Simple: [Docker](https://www.docker.com/) + [OctoberCMS](http://octobercms.com/)

#### It uses the:
- official [mysql:5.7 image](https://hub.docker.com/_/mysql/) as database,
- official [php:fpm image](https://hub.docker.com/_/php/) to run PHP over [FastCGI](https://en.wikipedia.org/wiki/FastCGI)
- and the official Apache [httpd image](https://hub.docker.com/_/httpd/) as web/proxy server.

#### First
Make sure that your October project is using `.env` to setup MySQL's user, password and database name.
Then place this repo contents at some folder in your project, like a `.docker` folder.

#### Up!

![Pixar Up](https://media.giphy.com/media/H8P253lLGnEn6/giphy.gif)

#### Docker Up!
Run `docker-composer up` at project root folder so Docker can use the same `.env` file as the October:
```bash
docker-compose -f .docker/docker-compose.yml up -d --build
```
`docker-compose.yml` will load your project's `.env` file and make a [variable substitution](https://docs.docker.com/compose/compose-file/#variable-substitution) at MySQL's image environment variables.
MySQL image is pretty nice so when it creates a new container it also create a database and set passwords using this same config, so October will be already configured.

#### October Up!
Then run `october:up` at PHP-FPM's container:
```bash
docker exec docker_php_1 php artisan october:up
```

You should be all set. Access `http://<YOUR_DOCKER_MACHINE_IP>:8000` and see your October project running.
