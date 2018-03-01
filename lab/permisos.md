#### setting permissions (chmod)

##### Permissions can be changed with chmod. The first example gives the user owner execute permissions.

paul@laika:~/perms$ ls -l permissions.txt 
-rw-r--r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt
paul@laika:~/perms$ chmod u+x permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwxr--r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt
This example removes the group owners read permission.

paul@laika:~/perms$ chmod g-r permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwx---r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt
This example removes the others read permission.

paul@laika:~/perms$ chmod o-r permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwx------ 1 paul paul 0 2007-02-07 22:34 permissions.txt
This example gives all of them the write permission.

paul@laika:~/perms$ chmod a+w permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwx-w--w- 1 paul paul 0 2007-02-07 22:34 permissions.txt
You don't even have to type the a.

paul@laika:~/perms$ chmod +x permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwx-wx-wx 1 paul paul 0 2007-02-07 22:34 permissions.txt
You can also set explicit permissions.

paul@laika:~/perms$ chmod u=rw permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rw--wx-wx 1 paul paul 0 2007-02-07 22:34 permissions.txt
Feel free to make any kind of combination.

paul@laika:~/perms$ chmod u=rw,g=rw,o=r permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rw-rw-r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt
Even fishy combinations are accepted by chmod.

paul@laika:~/perms$ chmod u=rwx,ug+rw,o=r permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwxrw-r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt


setting octal permissions

Most Unix administrators will use the old school octal system to talk about and set permissions. Look at the triplet bitwise, equating r to 4, w to 2, and x to 1.

Octal permissions

binary	octal	permission
000	0	---
001	1	--x
010	2	-w-
011	3	-wx
100	4	r--
101	5	r-x
110	6	rw-
111	7	rwx

This makes 777 equal to rwxrwxrwx and by the same logic, 654 mean rw-r-xr-- . The chmod command will accept these numbers.

paul@laika:~/perms$ chmod 777 permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwxrwxrwx 1 paul paul 0 2007-02-07 22:34 permissions.txt
paul@laika:~/perms$ chmod 664 permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rw-rw-r-- 1 paul paul 0 2007-02-07 22:34 permissions.txt
paul@laika:~/perms$ chmod 750 permissions.txt 
paul@laika:~/perms$ ls -l permissions.txt 
-rwxr-x--- 1 paul paul 0 2007-02-07 22:34 permissions.txt



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

Todo el mundo puede suprimir este fichero: sus permisos no tienen importancia. Son los permisos del directorio, en particular el permiso de escritura en el directorio, los que determinan quién puede suprimir los ficheros que hay dentro.

4.- Retire el permiso SUID a /usr/bin/passwd y modifique su contraseña. Intente modificar su contraseña. No funciona: passwd debe ser root para modificar los ficheros. Vuelva a poner el
permiso s.

    $ chmod u-s /usr/bin/passwd
    $ passwd =>Error
    $ chmod u+s /usr/bin/passwd
