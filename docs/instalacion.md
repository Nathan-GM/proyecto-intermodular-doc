# Instalación

## Requisitos

* PHP 8.0
* MySQL para la gestión de la base de datos
* Servidor web para poder servir la página. Por ejemplo Apache o Nginx.
* Navegador en el que ver la página correctamente.

## Pasos de instalación

1. Clonar el repositorio de trabajo al equipo donde se va a desplegar.
2. Importar a MySQL la base de datos.
3. Si existieran fichero .env, configurar con los datos correspondientes.
    * Esto podría incluir por ejemplo la ruta a la base de datos.
4. Configurar Nginx o Apache para desplegar la aplicación.
5. Acceder a la aplicación.

### Como instalar el servidor de Nginx en Linux

1. Actualizar repositorios e instalar Nginx:
```
    sudo apt update
    sudo apt install nginx
```
2. Comprobar que se haya instalado
```
    systemctl status nginx
```

3. Una vez instalado, crear la carpeta que tendrá los recursos en el directorio:
```
    /var/www/nombre_web/html
```
4. Crear los fichero de configuración. Estos ficheros se encargaran de decirle que puerto debe usar, donde está el directorio que debe usar, el nombre del sitio, etc. Se encuentran en los siguientes directorios:
```
    /etc/nginx/sites-available/nombre_web || Indica que el sitio esta disponible para ofrecerse
    /etc/nginx/sites-enabled/nombre_web || Indica que el sitio se esta ofreciendo.

Para crearlo en sites-enabled se usa el siguiente comando:

    sudo ln -s/etc/nginx/sites-available/nombre_web /etc/nginx/sites-enabled/
```

5. Reiniciar el servicio de Nginx
```
sudo systemctl restart nginx
```

6. Tras esto, el sitio web debería estar disponbile si todo ha ido correctamente.

## Variables de entorno (si aplica)

En caso de usarse variables de entorno, se recomienda configurar las siguientes para bases de datos
* **DB_HOST**: Se indica donde se encuentra la base de datos.
    * Ejemplo: `127.0.0.1:3000`
* **DB_USER**: Se indica el usuario que se usa para interactuar con la base de datos. Ha de tener permisos para poder listar, agregar y editar la base de datos.
    * Ejemplo: `NathanGM`
* **DB_PASSWORD**: Se indica la contraseña del usuario mencionado anteriormente.
    * Ejemplo: `1234` -> debería ser una contraseña segura, esto es un ejemplo
* **DB_NAME**: Se indica el nombre de la base de datos con la que se interactua.
    * Ejemplo: `tienda-DB`