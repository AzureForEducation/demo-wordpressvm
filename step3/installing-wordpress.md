# Step 3 - Installing and configuring Wordpress

We're almost there. The very next thing we need to do is to download Wordpress in our server, once we don't have it so far.

To get that, within your VM, please go after the following steps.

1) Download Wordpress to your current directory.

    ```shell
    curl -O https://wordpress.org/latest.tar.gz
    ```

2) Now we have it, let's "untar" that file we just downloaded. To get that, type the following command-line.

    ```shell    
    tar xvzf latest.tar.gz
    ```

3) Once you have unpacked Wordpress, now we'll need to move that "wordpress" directory (the unpackaging process generated it) to <code>/var/www/</code> directory, which is the default directory managed by Apache in web applications scenarios. To get that, execute the command-line below (considering you're in the same directory as "wordpress").

    ```shell
    sudo cp -a wordpress /var/www/html/
    ```

    If everything went well, by executing the command-line below you should be able to see the "wordpress" directory listed into its new home.

    ```shell
    cd /var/www/html/
    ls
    ```

4) Wordpress uses MySQL as the data repository for the application. This is why we've installed the service. So, before to move ahead with the final Wordpress' configuration, we need first create the database for the application. To that, type the following command-line below.

    ```shell
    mysql -u root -p
    ```

    Executing this command will make mysql_agent ask you for the password tied to the root user (remember? we've established that when we configured MySQL in step 2). Type the password out. By doing this, you should be able to see the MySQL console. Once there, type the following command-line below to create a new database.

    ```sql
    CREATE DATABASE wordpress_db;
    ```

    Done. Database "wordpress_db" has been successfully created. Now we can get back to the Wordpress configuration. To leave the MySQL environment, just type <code>exit;</code>.

5) Wordpress' configuration seats on "wp-config.php" file. This way, we need to adjust some information in there. The first step towards that is to open up that file by typing the following command-line.

    ```shell
    cd wordpress
    sudo nano wp-config-sample.php
    ```

    By doing this, you'll probably be seeing a screen like that one presented by the image below. That is how a wp-config file looks like. The items we're going update on that file to get our Wordpress up and running, are underlined in red.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-vm-nano.PNG" width="600" />

    Replace the content on that three pointed fields properly as follows:

    <code>database_name_here</code> by <code>wordpress_db</code>

    <code>username_here</code> by <code>root</code>

    <code>password_here</code> by <code>{your password}</code>

    Press <code>ctrl + X</code> to close editions on that document and then, press <code>Y</code> to confirm that the file is being saved.

    Now, rename that "wp-config-sample.php" file to "wp-config.php". To get that, just run the command-line presented below.

    ```shell
    mv wp-config-sample.php wp-config.php
    ```
    
    That's all. On end, your "wp-config-sample.php" file should be pretty similar to that one presented by the image below.

    <img src="https://raw.githubusercontent.com/AzureForEducation/demo-wordpressvm/master/images/wordpress-new-wp-config.PNG" width="480" />

    Done. Now we can go to the final configuration stuff and last tests.