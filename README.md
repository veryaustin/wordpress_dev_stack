# Wordpress Local Development Stack (Docker)

A [Wordpress] development stack using [Docker], [PHP], [phpMyAdmin], [MySQL], & [Mailhog]

## Requirements

* [Docker] with engine version 18.06.0 or better.

## Installation
1. Clone repo
2. Create the following required secrets in the directory located in `./secrets`
    * mysql_database_name.txt
    * mysql_password.txt
    * mysql_root_password.txt
    * mysql_user.txt
3. Run `docker-compose up` to build & spin up a local wordpress development environment
4. [Wordpress] is available at: [http://localhost:8000](http://localhost:8000)
5. [PHPMyAdmin] is available at [http://localhost:8080](http://localhost:8080)
6. [Mailhog] is available at: [http://localhost:1025](http://localhost:1025)

## Usage
### Secrets
Secrets are simple text files and the value of the secret should be written on the first line of the document.

### Wordpress

Access [Wordpress] at: [http://localhost:8000](http://localhost:8000)

[Wordpress] is pulled from the `wordpress:latest` docker hub build and modified by `uploads.ini`. 
If configuration changes are needed,  they can be modified in `./wordpress_dev/configs/uploads.ini` before build time. This file configuration sets php.ini to the follow values:

  ``` php
  file_uploads = On
  memory_limit = 128M
  upload_max_filesize = 128M
  post_max_size = 128M
  max_execution_time = 600
  ```


### phpMyAdmin

[phpMyAdmin] is a web GUI for managing MySQL databases. It is pulled from the `phpmyadmin:latest` docker hub build

Access [phpMyAdmin] at [http://localhost:8080](http://localhost:8080) 

### MySQL

[MySQL] is available via the host operating system & any MySQL client on port `:3306` and is pulled from the `mysql:5.7` docker hub build

### Mailhog

[Mailhog] is a Web API for SMTP testing and provides a local web interface in which to see test outbound email from the Wordpress development environment. If configuration changes are needed, they can be modified in `./wordpress_dev/configs/mailhog.ini` before build time.

Access [Mailhog] at [http://localhost:1025](http://localhost:1025)


## Credits
Thank you to the [Docker], [Wordpress], [PHP], [phpMyAadmin], [MySQL] & [Mailhog] development teams.

[Docker]: https://www.docker.com
[Wordpress]: https://www.wordpress.org/
[PHP]: https://www.php.net/
[phpMyAdmin]: https://www.phpmyadmin.net/
[MySQL]: https://www.mysql.com/
[Mailhog]: https://github.com/mailhog/MailHog