# Setup WSL For Laravel Development

## Install WSL

Go to https://learn.microsoft.com/en-us/windows/wsl/install and follow the instructions

## Install Ubuntu 22.04 LTS

- Download Ubuntu 22.04 LTS from the Microsoft Store by going to https://apps.microsoft.com/detail/9PN20MSR04DW?hl=en-us&gl=US
- Launch Ubuntu 22.04 LTS
- Create a username and password
- Run `sudo apt update && sudo apt upgrade -y`

## Remove Password Requirement for Sudo (Optional)

- Run `sudo visudo`
- Go to the end of the file and add the following line:
  <br /> `ALL ALL = (root) NOPASSWD: /usr/sbin/service`
  <br />
  `<your_username> ALL=(ALL) NOPASSWD: ALL`
- Save and exit by pressing `Ctrl + X`, then `Y`, then `Enter` (Nano Editor)

## Install PHP and PHP Extensions

- Run `sudo apt install php-cli php-common php-curl php-json php-mbstring php-zip  php-opcache php-readline php-xml php-zip php-sqlite3 php-mysql php-pgsql redis-server php-redis imagemagick php-gd php-imagick php-pear -y`
- Verify PHP is installed by running `php -v` You should see PHP Version.

## Install MySQL

- Run `sudo apt install mysql-server -y`
- Run `sudo service mysql start`
- To change the root password run `sudo mysql`
  - Run `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';` (Replace `password` with your password).
  - Run `FLUSH PRIVILEGES;`
  - Run `exit`
- Restart MySQL by running `sudo service mysql restart`

## Node Setup

- Go to https://github.com/nodesource/distributions#debian-and-ubuntu-based-distributions and follow the instructions to install NodeJS the LTS version.

## Install Composer

- `cd ~` to go to your home directory
- Run `wget https://getcomposer.org/installer`
- Run `php installer`
- Run `sudo mv composer.phar /usr/local/bin/composer` Add composer to your path
- Run `composer --version` to verify composer is installed
- Add the following to your `~/.bashrc` file:
  <br /> `export PATH=~/.config/composer/vendor/bin:$PATH`
- Run `source ~/.bashrc` to reload your bashrc file

## Set Laravel Valet for linux

- Install Required Packages
  - Run `sudo apt-get install network-manager libnss3-tools jq xsel -y`
- Install Valet via Composer
  - Run `composer global require cpriego/valet-linux`
- Run `valet install`
- Go to your web root directory (e.g. `cd ~/var/www`)
- Run `valet park` to register your current working directory as a path that Valet should search for sites
- To test if Valet is working create a new directory in your web root directory (e.g. `mkdir -p ~/var/www/info`)

  - Run `cd ~/var/www/info`
  - Run `echo "<?php phpinfo();" > index.php`
  - On Windows you must add host `127.0.0.1     info.test` to `C:\Windows\System32\drivers\etc\hosts` file
  - You can use [Hosts File Editor](https://hostsfileeditor.com/) to edit hosts file
  - Open your browser and go to http://info.test

- Auto Valet start
- Run `nano ~/.bashrc`
  - Go to the end of the file and add the following line:
    <pre>
    if ! ps -C nginx >/dev/null; then
        sudo service mysql start # start mysql if not running
        valet start # start valet
    fi
    </pre>

## Install Laravel Installer

- Run `composer global require laravel/installer`
- Run `laravel --version` to verify Laravel Installer is installed
