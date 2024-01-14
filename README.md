# PHP Docker Development
A template for developers to use Docker as a PHP development environment, including Xdebug.

## Setup
1. Copy ./php/conf.d/example-xdebug.ini to ./nginx/conf.d/xdebug.ini
2. Copy ./php/conf.d/example-error_reporting.ini to ./nginx/conf.d/error_reporting.ini
3. Copy ./nginx/conf.d/example-default.conf to ./nginx/conf.d/default.conf
4. Copy ./.env.example to ./.env and set variables as necessary.
5. `docker compose up -d`

### Developing
Developing in this environment is easy. A ./workspace volume will be mounted. You can place your PHP files there.  
By default the entrypoint is `index.php`.  
Files such as images can be put here as well. For example, ./workspaces/images/image.png would be accessible at http://localhost:8080/images/image.png.  