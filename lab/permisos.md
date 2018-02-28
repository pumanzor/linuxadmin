## Los permisos

Objetivo: modificar los permisos y comprender el mecanismo de los permisos y límites de los usuarios.
1. Modifique los propietarios y grupos de /DATOS en seb:users.

    $ chown seb:users /DATOS

2. Todo el mundo debe poder escribir en esta carpeta, pero sin suprimir los ficheros de los demás. Asimismo, todos los ficheros creados en este directorio deben pertenecer al grupo
users. Coloque los permisos correctos: hacen falta todos los permisos para todo el mundo, el permiso sticky y el SGID-bit:
   
   $ chmod 3777 /DATOS

3. Cree un directorio de prueba en /tmp con los permisos rwxrwxrwx. Cree un fichero en él y modifique sus permisos retirando el permiso w al grupo y los demás. ¿Quién puede
suprimirlo?

    $ mkdir /tmp/test
    $ chmod 777 /tmp/test
    $ touch /tmp/test/pepito
    $ chmod g-w,o-w /tmp/test/pepito

Todo el mundo puede suprimir este fichero: sus permisos no tienen importancia. Son los permisos del directorio, en particular el permiso de escritura en el directorio, los que
determinan quién puede suprimir los ficheros que hay dentro.

4.- Retire el permiso SUID a /usr/bin/passwd y modifique su contraseña. Intente modificar su contraseña. No funciona: passwd debe ser root para modificar los ficheros. Vuelva a poner el
permiso s.

    $ chmod u-s /usr/bin/passwd
    $ passwd =>Error
    $ chmod u+s /usr/bin/passwd
