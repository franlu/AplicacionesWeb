# Guía de instalación de MySQL Server en Debian 13

## 🧰 Requisitos previos

Actualiza los paquetes del sistema:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## ⚙️ Paso 1: Instalar dependencias necesarias

Instala las utilidades requeridas para añadir repositorios externos y manejar paquetes:

```bash
sudo apt install wget gnupg lsb-release -y
```

---

## 🗂️ Paso 2: Instalar MariaDB

:link: Guía de [instalación](https://www.rosehosting.com/blog/how-to-install-mariadb-on-debian-13/)

## 🗂️ (*) Paso: Añadir el repositorio oficial de MySQL

Descarga y añade la clave GPG del repositorio de MySQL:

```bash
wget https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
sudo gpg --dearmor -o /usr/share/keyrings/mysql.gpg RPM-GPG-KEY-mysql-2023
```

Agrega el repositorio oficial de MySQL para Debian 13:

```bash
echo "deb [signed-by=/usr/share/keyrings/mysql.gpg] https://repo.mysql.com/apt/debian/ $(lsb_release -sc) mysql-8.0" | sudo tee /etc/apt/sources.list.d/mysql.list
```

Actualiza el índice de paquetes:

```bash
sudo apt update
```

:link: Guía de [instalación manual](https://wiki.crowncloud.net/?How_to_Install_MySQL_8_on_Debian_13=)


---

## 💾 (*) Paso: Instalar MySQL Server

Instala el paquete principal de MySQL Server:

```bash
sudo apt install mysql-server -y
```

Verifica que el servicio esté activo:

```bash
sudo systemctl status mysql
```

En caso de que no esté activo, inícialo manualmente:

```bash
sudo systemctl start mysql
sudo systemctl enable mysql
```

---

## 🔐 Paso 4: Asegurar la instalación

Ejecuta el script de configuración segura:

```bash
sudo mysql_secure_installation
```

Durante el proceso podrás:
- Establecer la contraseña del usuario `root`.
- Eliminar usuarios anónimos.
- Deshabilitar el acceso remoto del root.
- Eliminar la base de datos de prueba.
- Recargar las tablas de privilegios.

---

## 🧠 Paso 5: Probar MySQL

Verifica la versión instalada:

```bash
mysql --version
```

Accede a la consola MySQL como root:

```bash
sudo mysql -u root -p
```

Si todo está correcto, deberías ver el prompt de MySQL (`mysql>`).

---

## 🔧 Paso 6: Comandos útiles

- **Ver estado del servicio:**  
  ```bash
  sudo systemctl status mysql
  ```

- **Reiniciar MySQL:**  
  ```bash
  sudo systemctl restart mysql
  ```

- **Detener MySQL:**  
  ```bash
  sudo systemctl stop mysql
  ```

- **Habilitar arranque automático:**  
  ```bash
  sudo systemctl enable mysql
  ```

---

## ✅ Comprobación final

Ejecuta:

```bash
sudo systemctl status mysql
```

Si ves “**active (running)**”, MySQL está correctamente instalado y funcionando.

---

© 2025 Guía creada por ChatGPT – Instalación de MySQL Server en Debian 13.