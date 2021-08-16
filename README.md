# Docker for ProcessWire

Running all the required php extensions for [ProcessWire](https://github.com/processwire/processwire) and also the following:

* PHP 7.4-apache
* ImageMagick

## Installation

Clone the ProcessWire repository.
```
git clone https://github.com/processwire/processwire.git app/public
```

Now run docker compose command and you are good to go.

```
docker-compose up
```

The docker container where ProcessWire is installed can be accessed via 127.0.0.1, visit this I.P. in your browser to start the [ProcessWire installation](https://processwire.com/docs/start/install/new/).

Information about the mysql connection can be found in `docker-compose.yml`.

I run this all in vscode with the [Docker Remote](https://github.com/Microsoft/vscode-remote-release) extension. View [all my extensions here](https://github.com/Geerodge/dotfiles).

## Important Notes - Do Not Skip

* When starting the docker container for the first time the mysql settings (database name, user, pass) from docker-compose.yml will be loaded and are annoyingly persistent. Remember to use the command "docker-compose down -v" in terminal, even after closing in vscode when changing these and not being able to connect.

* When connecting to database from within the container, do not use localhost or 127.0.0.1. Use mysql (the service name), especially useful on the /install.php script for processwire.
