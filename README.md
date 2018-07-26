# laravel-lemp-env
Laravel development environment on LEMP on Docker on Vagrant

either Vagrant or Docker installed is needed.
### Requirement (Vagrant)
[Vagrant](https://www.vagrantup.com/)

install [vagrant-docker-compose](https://github.com/leighmcculloch/vagrant-docker-compose) plugin:
```
$ vagrant plugin install vagrant-docker-compose
```

### Requirement (Docker)
[Docker](https://www.docker.com/) and [Docker Compose](https://github.com/docker/compose)

## Setting up (by using Docker)
if you have only Vagrant installed on your host machine, see 'On Vagrant' section.
```
$ git clone https://github.com/Tatamo/lemp-env.git
$ cd lemp-env
$ cp .env.example .env

# edit .env file as necessary
$ vim .env

$ docker-compose up

# setting up laravel project
$ docker-compose exec workspace bash -c "cd ../ && mv laravel/.gitkeep . && composer create-project laravel/laravel --prefer-dist && mv .gitkeep laravel/"
```


## Usage
after setting up, now you can access Laravel app http://localhost:8080/ and phpMyAdmin http://localhost:8081/ .

use `workspace` container to run composer and npm.
each command is executed in laravel/ directory.
```
# composer install
$ docker-compose exec workspace composer install

# npm install
$ docker-compose exec workspace npm install
```

or run bash
```
$ docker-compose exec workspace bash
```

## On Vagrant
instead of `docker-compose up`, run:
```
$ vagrant up
```

and you can run docker-compose exec command in VM.
the project directory is mounted as `/vagrant`.
```
$ vagrant ssh

$ cd /vagrant
$ docker-compose exec workspace ...
```
