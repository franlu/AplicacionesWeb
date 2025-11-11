# 🧩 Actividad guiada: Copias de seguridad en WordPress

## 🎯 Objetivo
Aprender a realizar una **copia de seguridad completa de un sitio WordPress instalado en local**, incluyendo tanto los archivos del proyecto como la base de datos MySQL, y a restaurarla correctamente.

## 🧠 Reflexiona

> 💬 *“Hay dos tipos de alumn@s: los que hacen copias de seguridad y los que aún están rehaciendo su práctica/proyecto.”* — **Profe con experiencia**


## Antes de empezar: conceptos clave

### 🔹 Copia de seguridad (backup)
Una **copia de seguridad** es una duplicación de los archivos y datos de un sistema para poder restaurarlos en caso de fallo, corrupción o pérdida.

### 🔹 Archivos del sitio WordPress
Contienen el **código fuente**, los **temas**, los **plugins** y los **archivos multimedia**.  
Estos archivos se encuentran en la carpeta donde está instalado WordPress (por ejemplo, `C:\xampp\htdocs\miblog` o `/var/www/html/wordpress`).

### 🔹 Base de datos MySQL
Contiene todo el **contenido dinámico** del sitio: usuarios, entradas, páginas, menús, opciones, etc.  
En un entorno local, la base de datos se administra desde el **servidor MySQL** que ejecuta XAMPP, LAMP, WAMP o similar.

## 🚀 Realizar una copia con plugin (método automático)

### 🪄 Instrucciones

1. Entra en el **Panel de administración** de WordPress → **Plugins → Añadir nuevo**.  
2. Busca **UpdraftPlus** (también puedes usar otros como *BackWPup* o *Duplicator*).  
3. **Instala** y **activa** el plugin.  
4. Ve a **Ajustes → UpdraftPlus Backups**.  
5. Crea una **copia manual** seleccionando:  
   - ✔️ **Archivos**  
   - ✔️ **Base de datos**  
6. Haz clic en **“Respaldar ahora”**.  
7. Espera a que finalice el proceso y **descarga los archivos resultantes** (uno o varios ficheros `.zip`).


## 🚀 Realizar una copia (método manual)

### 1️⃣ Identificar los elementos a respaldar
1. Carpeta de WordPress (por ejemplo `wordpress/` dentro de `html/`).
2. Base de datos MySQL asociada (consultar en `wp-config.php`):
   ```php
   define('DB_NAME', 'nombre_base');
   define('DB_USER', 'usuario');
   define('DB_PASSWORD', 'contraseña');
   define('DB_HOST', 'localhost');
   ```

### 2️⃣ Realizar la copia de seguridad de los archivos

1. Abre el terminal en el directorio raíz que contiene tu instalación de WordPress.  
   Por ejemplo:
   ```bash
   cd /var/www/html
   ```
2. Crea un archivo comprimido con todos los archivos del sitio:
   ```bash
   tar -czvf copia_wp_archivos.tar.gz wordpress/
   ```
   - `-c`: crea el archivo  
   - `-z`: comprime con gzip  
   - `-v`: muestra el progreso  
   - `-f`: indica el nombre del archivo resultante

3. Verifica que el archivo se ha creado correctamente:
   ```bash
   ls -lh copia_wp_archivos.tar.gz
   ```

### 3️⃣ Realizar la copia de seguridad de la base de datos MySQL desde el terminal

1. Ejecuta el siguiente comando para exportar la base de datos:
   ```bash
   mysqldump -u usuario -p nombre_base > copia_wp_bbdd.sql
   ```
   - `usuario`: el nombre de usuario MySQL  
   - `-p`: solicitará la contraseña  
   - `nombre_base`: el nombre de la base de datos (ver en `wp-config.php`)  
   - `>`: redirige la salida al archivo `copia_wp_bbdd.sql`

2. Comprueba que el archivo `.sql` se ha creado:
   ```bash
   ls -lh copia_wp_bbdd.sql
   ```

### 4️⃣ Probar la restauración (opcional, pero muy recomendable)

#### 🔸 Restaurar los archivos
1. Crea una nueva carpeta para el sitio restaurado:
   ```bash
   mkdir miblog_restaurado
   ```
2. Descomprime la copia:
   ```bash
   tar -xzvf copia_wp_archivos.tar.gz -C wordpress_restaurado/
   ```

#### 🔸 Restaurar la base de datos
1. Crea una nueva base de datos vacía desde MySQL:
   ```bash
   mysql -u usuario -p -e "CREATE DATABASE nombre_restaurado;"
   ```
2. Importa la copia de seguridad:
   ```bash
   mysql -u usuario -p nombre_restaurado < copia_wp_bbdd.sql
   ```
3. Modifica el archivo `wp-config.php` del sitio restaurado para que use la nueva base de datos:
   ```php
   define('DB_NAME', 'nombre_restaurado');
   ```

4. Inicia el servidor local y comprueba que el sitio funciona correctamente.


### 5️⃣ Verificación final
- Comprueba que los archivos están intactos y que puedes acceder al panel de WordPress (`http://localhost/wordpress_restaurado`).
- Si todo funciona, ¡has completado tu copia y restauración con éxito! 🎉

## 🧩 Preguntas de repaso

1. ¿Qué información se guarda en la base de datos de WordPress?  
2. ¿Dónde se almacenan los temas y plugins en una instalación local?  
3. ¿Qué comando se utiliza para crear una copia de los archivos del sitio?  
4. ¿Qué herramienta se usa para exportar una base de datos desde terminal?  
5. ¿Qué diferencia hay entre exportar e importar una base de datos?  
6. ¿Qué archivo contiene las credenciales de conexión a la base de datos?  
7. ¿Por qué es importante realizar copias de seguridad periódicas?  
8. ¿Qué se debe modificar en `wp-config.php` al restaurar una base de datos con otro nombre?

