# Library Site Architecture #

Create a library ecosystem by linking:

Your WordPress site should function as your library's home page
Your Koha site should function as your library's OPAC
Your Omeka site should function as your library's digital library (archives)

- Connect and login VM instance and find the directory where WordPress files are

- `cd wordpress`  `ls`
- the key files and directories you'll find there:

index.php: This is the main entry point for your WordPress site.
wp-admin: This directory contains all the files necessary for the WordPress admin dashboard.
wp-content: This directory contains your themes, plugins, uploads, and other site-specific content.
wp-includes: This directory contains core WordPress files.
wp-config.php: This file contains your WordPress configuration settings.

- Connection lost keeps happening. Need to go back to VM Instance to restart Apache2.

`sudo systemctl restart apache2`

My Library page:

http://34.162.174.62/wordpress/
