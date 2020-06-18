# docker-compose-laravel
A docker-compose workflow that sets up a LEMP network of containers for local Laravel development.

## Usage

To get started, make sure you have [Docker installed](https://docs.docker.com/get-docker/) on your system, and then clone this repository.

Containers created and their ports (if used) are as follows:

- **nginx** - `:8080`
- **mysql** - `:3306`
- **php** - 
- **phpmyadmin** - `:9000`
- **npm**

Create new Laravel project using Composer 
`docker-compose exec php composer create-project --prefer-dist laravel/laravel src`

Alternatively you can clone your existing Laravel application
```bash
# Switch into php/ directory then run:
git clone git@github.com:username/laravel-project.git src
```

Update Laravel .env file to match docker-compose configuration
```bash
APP_URL=http://localhost:8080
DB_HOST=db
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret
```

Run Artisan commands
`docker-compose exec php php src/artisan migrate`

Run npm commands without installing locally
- `docker-compose run npm run dev`
