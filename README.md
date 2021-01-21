Dockerize Symfony Project
===

Example configuration to dockerize a Symfony 5 project with the following containers :

* Nginx (alpine)
* PHP 7.4 FPM (alpine)
* Mysql 5.7 (debian)
* _(production)_ PHP 7.4 cron jobs

## Prepare your project 

Copy these files into your symfony project :

    - docker/
    - .dockerignore
    - manage.sh

Add these environment variables into your symfony __.env__ (and .env.local) file :

    ###> docker ###
    COMPANY_NAME=acme
    PROJECT_NAME=sf-project
    NETWORK_NAME=sf-project-network
    PUBLIC_PORT=8080
    MYSQL_ROOT_PASSWORD=root
    MYSQL_USER=user
    MYSQL_PASSWORD=password
    MYSQL_DATABASE=sf-project
    ###< docker ###

_COMPANY_NAME_ is used to prefix containers images names. 

Fix _manage.sh_ file permission :

    git update-index --chmod="+" ./manage.sh

## Usage

    ./manage.sh build (nginx|php)   # Builds the image
    ./manage.sh up                  # Starts containers
    ./manage.sh down                # Stop containers
    ./manage.sh sf [cmd]            # Runs a symfony command into the PHP container
    ./manage.sh composer [cmd]      # Runs a composer command into the PHP container
