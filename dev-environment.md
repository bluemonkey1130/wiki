### Development Environment
I've managed to set up a nice environment which requires minimal configuration for hosting local sites. I'm using [Laravel](https://laravel.com/) & [Valet](https://laravel.com/docs/8.x/valet).

> Valet is a Laravel development environment for Mac minimalists. No Vagrant, no /etc/hosts file. You can even share your sites publicly using local tunnels. Yeah, we like it too.

> Laravel Valet configures your Mac to always run Nginx in the background when your machine starts. Then, using DnsMasq, Valet proxies all requests on the *.test domain to point to sites installed on your local machine.

> Rather than running a virtual machine Ã  la Docker, Valet runs Nginx in the background and uses your local PHP and MySQL. This keeps your development environment very lean, only using about 7MB of RAM.

> Out of the box, Valet support includes, but is not limited to:
> - [Laravel](https://laravel.com)
> - [Lumen](https://lumen.laravel.com)
> - [Symfony](https://symfony.com)
> - [Zend](https://framework.zend.com)
> - [CakePHP 3](https://cakephp.org)
> - [WordPress](https://wordpress.org)
> - [Bedrock](https://roots.io/bedrock/)
> - [Craft](https://craftcms.com)
> - [Statamic](https://statamic.com)
> - [Jigsaw](http://jigsaw.tighten.co)
> - Static HTML

I found several useful guides online: [here](https://dev.to/pixleight/local-craft-cms-development-with-laravel-valet-27f8), [here](https://medium.com/@jalendport/running-craft-cms-3-on-laravel-valet-6df61e5193fd) & [here](https://bymayo.co.uk/writing/installing-laravel-valet-for-craft-cms)

Once it's all set up next time I need to create a craft theme all I have to do is:
````bash
# Move to your parked projects directory
cd ~/Sites

# Create a new database
mysql -u root -e "CREATE DATABASE new_db_name"

# Install Craft
composer create-project craftcms/craft new-site-name

# Setup Craft, filling in database credentials
# with username root and no password
new-site-name/craft setup
````
``new-site-name`` will automatically be served at ``http://<new-site-name>.test``

Or if preferred, you can install ``phpmyadmin`` and mange the database using the GUI, [here's](https://thepoweruser.wordpress.com/2018/11/22/how-to-set-up-and-use-phpmyadmin-with-laravel-valet/) a guide

Valet will automatically start its daemon each time your machine boots. There is no need to run ``valet start`` or ``valet install`` ever again once the initial Valet installation is complete.

#### Sharing Sites
To share a site, navigate to the site's directory in your terminal and run the ``valet share`` command. A publicly accessible URL will be inserted into your clipboard and is ready to paste directly into your browser. That's it.

general.php - this hooks up the styles to the shared domain which is new each time like: ``  http://d37419f75d41.ngrok.io ``
```php
$isNgrok = array_key_exists("HTTP_X_ORIGINAL_HOST", $_SERVER) && strpos($_SERVER["HTTP_X_ORIGINAL_HOST"], "ngrok");
$host = 'http://' . $_SERVER[$isNgrok ? 'HTTP_X_ORIGINAL_HOST' : 'SERVER_NAME'] . '/';
```
---