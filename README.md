# Setup WSL For Laravel Development

## Install WSL

Go to https://learn.microsoft.com/en-us/windows/wsl/install-manual and follow the instructions

## Install Ubuntu 22.04 LTS

- Download Ubuntu 22.04 LTS from the Microsoft Store by going to https://apps.microsoft.com/detail/9PN20MSR04DW?hl=en-us&gl=US
- Launch Ubuntu 22.04 LTS
- Create a username and password
- Run
  ```bash
  sudo apt-get update && sudo apt-get upgrade -y
  ```

## Remove Password Requirement for Sudo (Optional)

- Run `sudo visudo`
- Go to the end of the file and add the following line:
  ```bash
  ALL ALL = (root) NOPASSWD: /usr/sbin/service
  <your_username> ALL=(ALL) NOPASSWD: ALL
  ```
- Save and exit by pressing `Ctrl + X`, then `Y`, then `Enter` (Nano Editor)

## Install PHP MySQL Nginx Redis and required packages...

- Run
  ```bash
  sudo apt-get install network-manager libnss3-tools jq xsel build-essential libssl-dev zip unzip dnsmasq nginx mysql-server php-fpm php-cli php-mysql php-sqlite3 php-intl php-zip php-xml php-curl php-mbstring redis-server php-redis php-pear php-dev pkg-config libz-dev libzip-dev libmemcached-dev libmemcached11 libmemcachedutil2 libmagickwand-dev imagemagick memcached -y
  ```
- Verify PHP is installed by running `php -v` You should see PHP Version.

## Setup MySQL

- Run `sudo service mysql start`
- To change the root password run `sudo mysql`
  - Run
    ```sql
    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
    ```
  - Replace `password` with your password.
  - Run
    ```sql
    FLUSH PRIVILEGES;
    ```
  - Run
    ```sql
    exit;
    ```
- Restart MySQL by running
  ```bash
  sudo service mysql restart
  ```

## Node Setup

- Download and import the Nodesource GPG key

  ```bash
  sudo apt-get update
  sudo apt-get install -y ca-certificates curl gnupg
  sudo mkdir -p /etc/apt/keyrings
  curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
  ```

- Create deb repository

  ```bash
  NODE_MAJOR=20
  echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
  ```

  _**Note:** check node LTS version and replace NODE_MAJOR with the version you want to install._

- Update and install NodeJS

  ```bash
  sudo apt-get update
  sudo apt-get install -y nodejs
  ```

- [Reference](https://github.com/nodesource/distributions#debian-and-ubuntu-based-distributions)

## Install Composer

- `cd ~` to go to your home directory
- Run
  ```bash
  wget https://getcomposer.org/installer
  ```
- Run
  ```bash
  php installer
  ```
- Run

  ```bash
  sudo mv composer.phar /usr/local/bin/composer
  ```

  _Add composer to your path_

- Run `composer --version` to verify composer is installed
- Add this to the end of your `~/.bashrc` file
  by running

  ```bash
  nano ~/.bashrc
  ```

  and adding the following line:

  ```bash
  export PATH="$HOME/.config/composer/vendor/bin:$PATH"
  ```

  save and exit by pressing `Ctrl + X`, then `Y`, then `Enter` (Nano Editor)

- Run

  ```bash
  source ~/.bashrc
  ```

  to reload your bashrc file

## Set Laravel Valet for linux

- Install Required Packages
  - Run
    ```bash
    sudo apt-get install network-manager libnss3-tools jq xsel -y
    ```
- Install Valet via Composer
  - Run
    ```bash
    composer global require cpriego/valet-linux
    ```
- Run
  ```bash
  valet install
  ```
- Go to your web root directory (e.g. `cd /var/www`)
- Run `valet park` to register your current working directory as a path that Valet should search for sites
- To test if Valet is working create a new directory in your web root directory (e.g. `mkdir -p /var/www/info`)

  - Run `cd /var/www/info`
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

## Editor Setup (VSCode)

- Install VSCode
- Install VSCode [Remote WSL Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)
- Open WSL Terminal
- Go to your project folder
- Run `code .` to open VSCode

## Others (Optional)

- [Laravel Roadmap](https://github.com/Hasnayeen/laravel-developer-roadmap)

# [Next Step Create Laravel Project](createLaravelProject.md)
