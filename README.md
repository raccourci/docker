# Docker Images by Raccourci Agency

## Available versions

### PUPPET 5

- Puppet 8 + Debian 12 Bookworm amd64 (docker tags: `debian12-bookworm`) - `docker pull raccourci/puppet:debian12-bookworm-amd64`
- Puppet 8 + Debian 12 Bookworm (docker tags: `debian12-bookworm`) - `docker pull raccourci/puppet:debian12-bookworm`
- Puppet 7 + Debian 11 Bullseye amd64 (docker tags: `debian11-bullseye`) - `docker pull raccourci/puppet:debian11-bullseye-amd64`
- Puppet 7 + Debian 11 Bullseye (docker tags: `debian11-bullseye`) - `docker pull raccourci/puppet:debian11-bullseye`
- Puppet 5 + Debian 10 Buster (docker tags: `debian10-buster`) - `docker pull raccourci/puppet:debian10-buster`
- Puppet 5 + Debian 9 Stretch (docker tags: `debian9-stretch`) - `docker pull raccourci/puppet:debian9-stretch`

### NODE 9

- Node 9 + Alpine (docker tags: `9-alpine`) - `docker pull raccourci/node:9-alpine`

### NGINX

- Nginx + Alpine (docker tags: `alpine`) - `docker pull raccourci/nginx:alpine`

### PHP 7

- PHP cli + Alpine (docker tags: `7-cli-alpine`) - `docker pull raccourci/php:7-cli-alpine`
- PHP fpm + Alpine (docker tags: `7-fpm-alpine`) - `docker pull raccourci/php:7-fpm-alpine`

### PHP7 + COMPOSER

- Composer + Alpine (docker tags: `7-alpine`) - `docker pull raccourci/composer:7-alpine`

### PHP7 + COMPOSER + WP CLI

- WP CLI + Alpine (docker tags: `7-alpine`) - `docker pull raccourci/wp-cli:7-alpine`

## How debug

````
docker-compose rm && docker-compose build --no-cache && docker-compose up
````

## License

View [LICENSE](LICENSE) for the software contained in this image.
