# docker-compose-laravel
Simplified LEPP stack for local development.

# Note
Create a docker volume called 'data-postgres' before spinning up the container

This is a workaround for an issue in which postgres permissions no longer allow
for the data to be persisted over volumes.

## Usage

Build Laravel file in src folder, or add php files to the "public/" directory. Run `docker-compose up -d --build` at root. Open browser to [http://localhost:8080](http://localhost:8080).

Three new available have been added that handle Composer, NPM, and Artisan commands without having to have these platforms installed on your local computer. Use the following command templates from your project root, modifiying them to fit your particular use case:

- `docker-compose run --rm composer update`
- `docker-compose run --rm npm run dev`
- `docker-compose run --rm artisan migrate` 

Containers created and their ports (if used) are as follows:

- **nginx** - `:8080`
- **mysql** - `:3306`
- **php** - `:9000`
- **phpmyadmin** - `:5000`
- **npm**
- **composer**
- **artisan**

## PHPMyAdmin

### Login

<pre>
server: mysql
Username: root
password: ${MYSQL_ROOT_PASSWORD}
</pre>

# Laravel

- Generate your laravel project in the root folder using the composer disposable container. You must call the project src unless you change the pathing.

# Nginx

- Nginx is set up to disallow access to non-public files. You will need to set up htaccess if you wish to change this to an apache service.

### Issues

## MYSQL Resatrting

 - Mysql continuously restarting.

### Solution
 - Delete mysql folder, recreate and redeploy containers