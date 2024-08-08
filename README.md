# Techplement
DEPLOYING A WORDPRESS HOMEPAGE IN MONOLITHIC ARCHITECTURE
STEPS:
• Create 1 EC2 Instance and Deploy wordpress and MYSQL on that Instance.
• Configure the Security Group for your instances.
• EC2 instance type: t2-micro, and USE AMI: Ubuntu
• Create a welcome page in wordpress that will be the homepage
STEPS: 1. Log in to your AWS Management Console.
2. Navigate to the EC2 Dashboard and click on “Launch Instance”.
3. Give the instance a name like “Monolithic”
4. Select an appropriate Amazon Machine Image (AMI) based on your requirements. For this example, let's choose the latest Ubuntu Server.
5. Choose the instance type according to your needs. We'll go with a t2.micro(Free Tier) instance.
6. Configure instance details including the number of instances, network settings, and storage. Ensure to create or select a security group that permits inbound traffic on HTTP (port 80) and SSH (port 22).
7. Review the configurations and click on the “Launch Instance” button. This setup should get you started with your EC2 instance running a WordPress server on a monolithic architecture.
This setup should get you started with your EC2 instance running a WordPress server on a monolithic architecture

COMMANDS TO FOLLOW:
1. Install Apache server on Ubuntu:
• sudo apt update
• sudo apt install apache2
2. Install PHP runtime and PHP MySQL connector:
• sudo apt install php libapache2-mod-php php-mysql
3. Install MySQL server:
• sudo apt install mysql-server
4. Login to MySQL server:
• sudo mysql -u root
5. Change authentication plugin to mysql_native_password (change the password to something strong):
• ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by
'Akshay@123';
6. Create a new database user for WordPress (change the password to something strong):
• CREATE USER 'vaibhavi_user'@'localhost' IDENTIFIED BY ' Akshay@123';
7. Create a database for WordPress:
• CREATE DATABASE wp;
8. Grant all privileges on the database 'wp' to the newly created user:
• GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@'localhost';
• exit;
9. Download WordPress:
• cd /tmp • wget https://wordpress.org/latest.tar.gz
10. Unzip:
• tar -xvf latest.tar.gz
11. Move WordPress folder to Apache document root:
• sudo mv wordpress/ /var/www/html
12. Command to restart/reload Apache server:
• sudo systemctl restart apache2
13. Now, navigate to the WordPress directory and configure the wp-config.php file:
• cd /var/www/html/wordpress
• sudo cp wp-config-sample.php wp-config.php
• sudo vim wp-config.php Open your browser and navigate to your WordPress instance's
public IP address.
Follow the WordPress installation wizard to complete the setup.

DEPLOYING A WORDPRESS HOMEPAGE IN MONOLITHIC ARCHITECTURE
Description:
• Setting up Wordpress and MYSQL in two different EC2 instances
• Configure the necessary security group for the instances.
• EC2 instance type: t2-micro, AMI: ubuntu-*.
Create a welcome page in wordpress that will be the homepage.
Creating 2 Instances 1 for Wordpress as well AS 1 for MySQL
(STEPS to create 2 EC2 instances are same)
1. Access your AWS Management Console.
2. Go to the EC2 Dashboard and hit “Launch Instance”.
3. Name your instance “ Instance1” and "Instance2".
4. Pick an appropriate Amazon Machine Image (AMI). I will Opt for Ubuntu Latest Version.
5. Select the instance type based on your needs. I'll go with a t2.micro(free-tier) instance.
6. Configure instance details like the number of instances, network settings, and storage. Ensure to include a security group allowing inbound traffic on HTTP (port 80), SSH (port 22) & MYSQL (port 3306) .
7. Review your settings and proceed by clicking “Launch instance”.
I Will be Setting Up mysql-1 First:
1. Install MySQL on MySQL Instance:
• sudo apt install mysql-server -y
• sudo apt update
• sudo apt install apache2 y
• sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf (change bind to address 0.0.0.0)
• systemctl restart mysql
Now Install PHP and Other Dependencies on WordPress Instance:
• sudo apt update
• sudo apt install apache2
• sudo apt install php libapache2-mod-php php-mysql -y
• sudo systemctl restart apache2
Create MySQL Database:
• ALTER USER 'root'@'localhost' IDENTIFIED BY 'Akshay12';
• CREATE DATABASE wp;
• CREATE USER 'wp_user'@'%' IDENTIFIED BY 'Akshay12';
• GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@'%';
• Exit
ON Instance 2
• sudo apt update
• sudo apt install apache2 -y
• mysql -u wp user -p -h %
•show DATABASES;
•use wp;
•show tables;
•cd /tmp
Download WordPress:
• wget https://wordpress.org/latest.tar.gz
•sudo apt install unzip
•unzip latest.zip
• sudo mv wordpress /var/www/html/ (moving wordpress)
• cd /var/www/html/wordpress (changing directory)
3.Update the database settings: In the Browser, enter public ip of web server ex: 8.8.8.8/wordpress to finish setup
4.Now
• vim wp-config.php (create file and paste the configuration rules in this file)
• sudo systemctl restart apache2
Browse with your public IP/wordpress. Wordpress will automatically connect to the MySQL server on another EC2.
