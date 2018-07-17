# lemp-env
LEMP development environment on Docker on Vagrant

## on Vagrant
### Requirement
[Vagrant](https://www.vagrantup.com/)

install [vagrant-docker-compose](https://github.com/leighmcculloch/vagrant-docker-compose) plugin:
```
$ vagrant plugin install vagrant-docker-compose
```

### Setting up
```
$ git clone https://github.com/Tatamo/lemp-env.git
$ cd lemp-env
$ cp .env.example .env

# edit .env file
$ vim .env

$ vagrant up
```

## on Docker
### Requirement
[Docker](https://www.docker.com/) and [Docker Compose](https://github.com/docker/compose)

### Setting up
```
$ git clone https://github.com/Tatamo/lemp-env.git
$ cd lemp-env
$ cp .env.example .env

# edit .env file
$ vim .env

$ docker-compose up
```

## Usage
after setting up, now you can access Laravel app http://localhost:8080/ and phpMyAdmin http://localhost:8081/ .

use `workspace` container to run composer and npm.
each command is executed in laravel/ directory.
```
# composer install
$ docker-compose exec workspace composer install

# npm install
# .bashrc needs to be loaded, so current work-around here:
$ docker-compose exec workspace bash --login -c "npm install"
```

or run bash
```
$ docker-compose exec workspace bash
```
