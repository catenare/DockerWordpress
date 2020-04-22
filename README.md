# Generic Wordpress Configuration using Docker
* Uses **composer.json** to manage Wordpress as a package.
* Wordpress site is hosted in containers.

## Resources
* [Introduction to Wordpress and Composer](https://www.pmg.com/blog/composer-and-wordpress/?cn-reloaded=1)
* [wordpress with Composer Support](https://github.com/johnpbloch/wordpress)
* [WordPress Packagist](https://wpackagist.org/) - WordPress Packages compatible with Composer

## Instructions
* Create **.env** file. Look at example.env
  * To generate custom salts `openssl rand -base64 35` - Will generate 35 character custom salts.
* `export DOCKER_BUILDKIT=1` - Will parallize the build of the docker image.
* Start Wordpress and Nginx. `docker-compose up`
* Start Mysql Server> `docker run --env-file .env --name wordpressdb --network wordpress_cloud_default -v "$PWD/database":/var/lib/mysql -p 3306:3306 -p 33060:33060 mysql:5`
* Connect to server at `http://localhost:7000`
* Should see the Wordpress Admin install page.

## Development
### Complete environment including MySQL Server as part of compose file.
  * Change **WORDPRESS_DB_HOST** in **.env** file to `WORDPRESS_DB_HOST=localhost:/var/run/mysqld/mysqld.sock`
  * `docker-compose -f dev-docker-compose.yml up` - Will build the local container and configure with NGINX and MySQL Server. Edit .env file accordingly.
