# LAMP stack

> Docker-compose project with Alpine linux, Apache, MySQL and PHP. Super easy to get started and running in a few mins

## Install

### Using DECK

Install lamp-stack from the DECK marketplace and follow the instructions on the GUI

### From terminal with Docker

```
git clone https://github.com/deck-app/lamp-stack/
cd lamp-stack
```

Edit `.env` file to change any settings before installing like php, apache, mysql versions etc

```
docker-compose up -d
```
### Modifying project settings
From the DECK app, go to stack list and click on project's `More > configure > Advanced configuration`
Follow the instructions below and restart your stack from the GUI

#### Editing php.in

PHP ini file is located at `./apache/php_ini/php{YOUR.PHP.VERSION}.ini`

#### Installing / removing PHP extensions

Add / remove PHP extensions from `./apache/Dockerfile-{YOUR.PHP.VERSION}`

```
RUN apk add --update --no-cache bash \
				curl \
				curl-dev \
				php5-intl \
				php5-openssl \
				php5-dba \
				php5-sqlite3 \
```

#### Rebuilding from terminal

You have to rebuild the docker image after you make any changes to the project configuration, use the snippet below to rebuild and restart the stack

```
docker-compose stop && docker-compose up --build -d
```
