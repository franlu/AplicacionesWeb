# Guía de Instalación de Moodle 5.1 en Debian 13 (con LAMP previo)

## 1. Requisitos previos

Asegúrate de tener instalado Apache, MariaDB/MySQL, PHP 8.2+ y las extensiones necesarias.

### Extensiones PHP

```
sudo apt update
sudo apt install php-curl php-gd php-intl php-mbstring php-xml php-zip php-soap php-xmlrpc php-bcmath php-ldap
sudo systemctl restart apache2
```

## 2. Crear base de datos

```
sudo mysql -u root -p
```

```
CREATE DATABASE moodle DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'moodleuser'@'localhost' IDENTIFIED BY 'ContraseñaSegura123';
GRANT ALL PRIVILEGES ON moodle.* TO 'moodleuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

## 3. Descargar Moodle 5.1

```
cd /var/www/
sudo wget https://download.moodle.org/download.php/direct/stable501/moodle-latest-501.tgz
sudo tar -xvzf moodle-latest-501.tgz
sudo rm -r moodle-latest-501.tgz
```

## 4. Crear moodledata

```
cd /var/www/
sudo mkdir moodledata
sudo chown -R www-data:www-data moodledata
sudo chmod -R 755 moodledata
```

## 5. Permisos

```
sudo chown -R www-data:www-data /var/www/moodle
sudo chmod -R 755 /var/www/moodle
```

## 6. Configuración de Apache

Crear archivo:

```
sudo nano /etc/apache2/sites-available/moodle.conf
```

Contenido:

```
<VirtualHost *:80>
    ServerName moodle.local
    DocumentRoot /var/www/moodle
    <Directory /var/www/moodle>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Activar:

```
sudo a2ensite moodle.conf
sudo a2enmod rewrite
sudo systemctl reload apache2
```

## 7. Instalar vía navegador

Accede a:

```
http://moodle.local
```

Sigue los pasos de configuración.

## 8. Ajustes PHP opcionales

```
sudo nano /etc/php/8.2/apache2/php.ini
```

Cambiar:

```
max_execution_time = 300
memory_limit = 512M
post_max_size = 256M
upload_max_filesize = 256M
```

## 9. Instalación completa 🎉
