[![docker pull socialengine/apache-php](https://img.shields.io/badge/dockerhub-socialengine%2Fphp--apache-blue.svg)](https://registry.hub.docker.com/u/socialengine/php-apache/)

This is a Docker image with PHP (5.6), Composer, and Apache (running in 
Foreground) serving from public/ folder. Ideal for Laravel, Lumen and other 
modern php apps.

## Supported tags and `Dockerfile` links

-	[`5.6` (*5.6/Dockerfile*)](https://github.com/SocialEngine/docker-php-apache/blob/master/5.6/Dockerfile)

## Included on top of [base](https://github.com/docker-library/php) PHP image

- mbstring 
- mcrypt 
- zip
- composer (avaiable globally)

# App setup

This assumes (and built for) `index.php` file being in the `public/` directory.

At a minimum, you will want this in your `Dockerfile`

```Dockerfile
FROM socialengine/php-apache:5.6

COPY . /app

RUN composer install
```

Then you can build & run your app in the docker container.
