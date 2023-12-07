# Install PHPMyAdmin

## Download PHPMyAdmin

- Go to web root directory e.g.
  ```bash
  cd /var/www
  ```
- Run
  ```bash
    wget https://files.phpmyadmin.net/phpMyAdmin/5.2.1/phpMyAdmin-5.2.1-all-languages.zip
  ```
  **Note:** You can find the latest version of PHPMyAdmin [here](https://www.phpmyadmin.net/downloads/)
- To unzip the downloaded file Run:
  ```bash
  unzip phpMyAdmin-5.2.1-all-languages.zip
  ```
- And rename the folder to `phpmyadmin` by running:
  ```bash
  mv phpMyAdmin-5.2.1-all-languages phpmyadmin
  ```
- Now go to the phpmyadmin directory by running:
  ```bash
  cd phpmyadmin
  ```
- Install composer dependencies by running:
  ```bash
  composer install
  ```
- Copy the `config.sample.inc.php` file to `config.inc.php` by running:
  ```bash
  cp config.sample.inc.php config.inc.php
  ```
- Generate a random string to use as the blowfish secret key by running:
  ```bash
  openssl rand -base64 32
  ```
- First, run the command mentioned earlier and note down its output.
- Then, use the `sodium_hex2bin('32_byte_string')` function with the output you got.
- For example, in the `config.inc.php` file, you might write:
  ```php
  $cfg['blowfish_secret'] = sodium_hex2bin('f16ce59f45714194371b48fe362072dc3b019da7861558cd4ad29e4d6fb13851');
  ```

## Add PHPMyAdmin to Valet

- [Check this WSL for Laravel Development](README.md)
- Add host to Windows hosts file
  ```code
  127.0.0.1 phpmyadmin.test
  ```
- Go to http://phpmyadmin.test
- Login with your MySQL username and password
