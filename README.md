# PHP Docker Development
A template for developers to use Docker as a PHP development environment with VSCode.  
XCode is setup within the PHP container for step debugging.  

## Setup
1. Copy ./php/conf.d/example-xdebug.ini to ./nginx/conf.d/xdebug.ini
2. Copy ./php/conf.d/example-error_reporting.ini to ./nginx/conf.d/error_reporting.ini
3. Copy ./nginx/conf.d/example-default.conf to ./nginx/conf.d/default.conf
4. Copy ./.env.example to ./.env and set variables as necessary.
5. Copy ./php/example-php.ini to ./php/php.ini
6. `docker compose up -d`

### Developing
Developing in this environment is easy. A ./workspace volume will be mounted. You can place your PHP files there.  
By default the entrypoint is `index.php`.  
Files such as images can be put here as well. For example, ./workspaces/images/image.png would be accessible at http://localhost:8080/images/image.png.  

### VSCode
Make sure to setup your .vscode/launch.json correctly. Path mappings need to be setup for XDebug to work correctly.  
Launch debug with defults and modify launch.json similar to this:
```json
{
    "configurations": [
            {
                "name": "Listen for Xdebug",
                "type": "php",
                "request": "launch",
                "port": 9003,
                "pathMappings": {
                    "/var/www/html": "${workspaceFolder}",
                }
            },
    ]
}```