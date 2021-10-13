# TEMPLATE DOCKER FOR LARAVEL & NUXTJS

This example create a environment facilitate you can run your project in server.

About `laravel` it just create environment not exec any command to help you deploy automatically.

About `nuxtjs` it auto generate and start app. Then when update `nuxtjs` src you need rebuild docker image.

## How to use?

1. You need to clone example files.

```command
    cp ./.env.example ./.env
    cp ./docker-compose.example.yml ./docker-compose.yml
    cp -r ./nginx/ssl-example ./nginx/ssl
```

Then change them to your tailored configs. You can ignore update ssl files.

2. Clone your laravel and nuxtjs.

Clone it accordingly to `./laravel/src` and `./nuxtjs/src`

3. Config nuxtjs

Normally you would set private laravel url (local url to laravel) to `http://nginx:8000`

4. Run your project

```command
    docker-compose up -d
```

5. Instantiate laravel

```command
    docker-compose exec laravel composer install --ignore-platform-reqs
    docker-compose exec laravel php artisan key:generate -n
    docker-compose exec laravel php artisan optimize
    docker-compose exec laravel php artisan migrate --seed
    docker-compose exec laravel php artisan storage:link
```

## How to update code?

1. Update `laravel`, then we just exec needed.
2. Update `Nuxtjs`, then we need just below command.

```command
    docker-compose down
    docker-compose build --no-cache nuxtjs
    docker-compose up -d
```
