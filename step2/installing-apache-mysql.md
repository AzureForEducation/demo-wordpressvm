# Step 2 - Installing MySQL, Apache, and PHP

Wordpress is one of the (if not the one) most famous CMS (Content Management System) in the market nowadays. There are lots of companies and educational institutions around the globe using it in so many different ways. This is why we decided to pick up it to make this demo.

## Wordpress' requirements

Wordpress has the following environment's requirements:

* PHP version 7.2 or greater
* MySQL version 5.6 or higher OR MariaDB version 10.0 or greater
* HTTPS support

So once we're using the VM approach to host that environment, we need to go after the whole environment so, as soon as we start as soon we close this.

## Installing PHP 7.2

Let's start installing PHP 7, once Wordpress requires it. Not occasionally we've selected Ubuntu 16.04. PHP 7's packages are already part of this Ubuntu's version, so we don't need to download this package to our server. To get that installed, go over the steps below.

1) Install Python services

    ```shell
    sudo apt-get install python-software-properties
    ```

2) Add the apt-get repository for PHP

    ```shell
    sudo add-apt-repository ppa:ondrej/php
    ```

3) Update the environment

    ```shell
    sudo apt update
    ```

4) Finally, installing PHP 7.2

    ```shell
    sudo apt install -y php7.2
    ```

5) Installing some additional and essential extensions

    ```shell
    sudo apt install php7.2-curl php7.2-gd php7.2-json php7.2-mbstring php-mcrypt
    ```

## Installing Apache 2

Now we have PHP already installed, its time to install and configure the element which gives life to that PHP applications and is where these applications are going to live physically; Apache 2.

To get that installed, execute out the following command-line.

```shell
sudo apt install apache2 libapache2-mod-php7.2
```

## Installing MySQL

Finally, let's install mysql-server packages for MySQL database. Also, install php-mysql package to use MySQL support using php. Use the following command to install it.

```shell
sudo apt install mysql-server php7.2-mysql
```

This command you raise two new screens asking you to select a password for the "root" admin (which is the administrator for that MySQL Server). Please, type a password that fits best to your needs and press enter. The process will continue normally.

Now, to set up the default configurations to the MySQL Server, we just installed, do execute the following command-line.

```shell
sudo mysql_secure_installation
```

This process will raise up some questions to you. First, type the password you just configured to the MySQL Server root user and then, for all the other items, "N".

Done.

## Restarting the services manually

Now, let's restart both MySQL and Apache services to reload any changes done manually. We can do that by executing the following command-lines.

1) Restarting Apache
```shell
sudo systemctl restart apache2.service
```

2) Restarting MySQL
```shell
sudo systemctl restart mysql.service
```

Done. This is all about the installation of the services required by Wordpress. Now, let's keep hacking and install Wordpress on top of this service.