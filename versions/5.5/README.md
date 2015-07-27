[![docker pull socialengine/apache-php][3]][4]

This is a Docker image with PHP, Composer, and Apache (running in 
Foreground) serving from public/ folder. Ideal for Laravel, Lumen and other 
modern php apps.

## Supported tags and `Dockerfile` links

-	[`5.6` (*5.6/Dockerfile*)][1]
-	[`5.5` (*5.5/Dockerfile*)][2]

## Included on top of [base][base image] PHP image

- mbstring 
- mcrypt 
- zip
- composer (avaiable globally)
- xdebug (enabled with `-e PHP_XDEBUG=1`)

# App Setup

This docker image is built for `index.php` file being in the `public/` 
directory. `mod_rewrite` is enabled.

At a minimum, you will want this in your `Dockerfile`:

```Dockerfile
FROM socialengine/php-apache:5.6

COPY . /app

RUN composer install
```

Then you can build & run your app in the docker container.

If you want to enable xdebug:

```bash
$ docker run -e PHP_XDEBUG=1 [your image]
```

[base image]: https://github.com/docker-library/php
[1]: https://github.com/SocialEngine/docker-php-apache/blob/master/versions/5.6/Dockerfile
[2]: https://github.com/SocialEngine/docker-php-apache/blob/master/versions/5.5/Dockerfile
[3]: https://img.shields.io/badge/dockerhub-socialengine%2Fphp--apache-blue.svg
[4]: https://registry.hub.docker.com/u/socialengine/php-apache/
