# Basic-Docker-compose-file

This Docker Compose file defines a multi-container environment for deploying WordPress along with a MySQL database and phpMyAdmin for database management. The components are:

Services:
        
        db: This service defines a MySQL database container. It uses the mysql:5.7 image, sets the container name to mysql_5_7, mounts a volume db_data to persist MySQL data, sets environment variables for MySQL configuration (root password, database name, user, and password), and connects it to the wordpress-site network.
        
        wordpress: This service defines a WordPress container. It depends on the db service, uses the wordpress:latest image, sets the container name to WPBackup, maps port 3005 on the host to port 80 in the container for accessing WordPress, mounts the current directory (./) to the container's /var/www/html directory for persistent storage, sets environment variables for WordPress database configuration, and connects it to the wordpress-site network.
        
        phpmyadmin: This service defines a phpMyAdmin container for managing the MySQL database. It uses the phpmyadmin/phpmyadmin image, sets the container name to phpmyadmin, sets environment variables for connecting to the MySQL database (PMA_HOST, MYSQL_ROOT_PASSWORD, MYSQL_USER, and MYSQL_PASSWORD), maps port 8081 on the host to port 80 in the container for accessing phpMyAdmin, and connects it to the wordpress-site network.

    Volumes:
        db_data: This volume is used by the MySQL container to persist its data.

    Networks:
        wordpress-site: This network is used to connect the containers (db, wordpress, and phpmyadmin) so they can communicate with each other.

This Docker Compose configuration sets up a complete environment for running WordPress with a MySQL database and phpMyAdmin for easy database management.
