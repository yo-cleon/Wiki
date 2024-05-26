# Recuperar Contraseña Root MariaDB 10.1.4

1. Detenemos el servidor de base de datos:
    $ sudo systemctl stop mariadb

    Puede ser necesario parar tambień los procesos que haya corriendo de MariaDB. Para ello, buscamos los procesos iniciados con:
        $ ps -aux | grep -i mysql
    y los terminamos con:
        $ sudo kill -9 <proccess_id>

2. Reiniciamos el servidor de base de datos en modo seguro, sin comprobación de permisos:
   $ sudo mysqld_safe --skip-grant-tables --skip-networking &

3. Conectamos con el servidor como usuario root
   $ mysq -u root

4. Recargamos las tablas de permisos:
   MariaDB [(none)]> FLUSH PRIVILEGES;

5. Seleccionamos la bbdd mysql y modificamos la contraseña del usuario root:
    MariaDB [(none)]> use mysql;
    MariaDB [(none)]> ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';

6. Reiniciamos el servidor de MariaDB normalmente
    $ sudo systemctl start mysql

7. Verificamos que podemos conectar correctamente con la nueva contraseña
    $ mysql -u root -p

## Links

- [How To Reset Your MySQL or MariaDB Root Password](https://www.digitalocean.com/community/tutorials/how-to-reset-your-mysql-or-mariadb-root-password)