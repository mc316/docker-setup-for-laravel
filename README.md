# Docker Setup for Laravel

This is a Docker setup for a Laravel project. This project focuses on deploying your Laravel application using Docker.The images used in this setup are:

```
nginx
php
mysql
composer
npm
```


### Prerequisites

You need to have a `docker` and `docker-compose` in your machine to make this work. Please refer to the [docker documents](https://docs.docker.com/get-docker/) on how to install docker and docker-compose in your machine.

### Getting Started

Once you've got your `docker` and `docker-compose` working in your machine.

1. Copy _**all**_ _the contents_ of your Laravel project to the `src/` folder.
2. Modify your database envrionment variables in your `.env` file with the configured mysql environment variables in the `docker-compose.yml` file.
    
    _your .env_
    ```
        DB_PORT=3307
        DB_DATABASE=homestead
        DB_USERNAME=homestead
        DB_PASSWORD=secret
    ```

    _docker-compose.yml_
    ```
        mysql:
            ports:
            - "3307:3306"
            environment:
                MYSQL_DATABASE: homestead
                MYSQL_USER: homestead
                MYSQL_PASSWORD: secret
    ```

3. If you haven't build your docker images then `docker-compose build` or if you already did, then `docker-compose up -d`

4. If docker finished it's process without error, you may check your laravel app in your `http://localhost:8088`

### Running Composer, NPM and Artisan Commands outside of Docker
You may run composer, NPM and artisan commands outside of docker with these commands:

```
    docker-compose run --rm composer <command>
    docker-compose run --rm npm <command>
    docker-compose run --rm artisan <command>
```

### Nginx Config
There's a file called `default.conf` inside the `nginx/` directory that is being used by the *nginx* container. You may modify this if you want to do something with the nginx conf.

### Updating Docker Image Versions
You can update the Images you want to use in the `docker-compose.yml` except for PHP which is in the `Dockerfile`.

### Acknowledgments

This project is based on [Andre Schemelyun's](https://www.youtube.com/channel/UCc07-IBVwRlOsMg2WMdd8Sg) youtube video [tutorial](https://www.youtube.com/watch?v=5N6gTVCG_rw). Please follow and subscribe to his channel, he has lots of great tutorials about Laravel.

