1.- En un archivo, ¿indica el permiso x que un archivo es obligatoriamente un programa?

No. Es posible poner el permiso x en cualquier fichero, incluso si no es un programa.

2.- Dispone del permiso w de escritura en un fichero. ¿Esto le da el permiso de suprimirlo?

No. Son los permisos del directorio que contiene el fichero que indican si un usuario tiene el permiso suprimir un fichero.

3.- Un directorio que le pertenece está en otro directorio en el cual el permiso x está ausente. ¿Puede acceder a
su directorio?

    A - Sí: me pertenece, por lo tanto puedo acceder a ello.
    B - Sí: ya que me pertenece, el directorio que lo contiene también.
    C - No: el directorio que lo contiene no me pertenece.
    D - No, no tengo permiso de cruzar el directorio que lo contiene.

D. El permiso x que falta impide cualquier acceso al directorio, incluso si contiene ficheros y directorios que le
pertenecen.


4.- Usted es el propietario del fichero fic, que ha retirado a los miembros del grupo y otros todos los permisos sobre él. Sin embargo, el directorio que lo contiene dispone del permiso w para los miembros del grupo.

¿Quién puede suprimir su fichero?

    A - Usted solamente.
    B - Usted y los miembros del grupo del directorio.
    C - Nadie: suprimió todos los permisos del fichero.D - Los demás.
    
    B. Es el permiso de escritura en el directorio el que autoriza a las personas a modificar su contenido.

5.- Con chmod, ¿cuáles son los parámetros que se deben colocar para suprimir los permisos de escritura a los demás, dar el permiso de lectura y ejecución a los miembros del grupo y todos los permisos a usted?

u=rwx,g=rw,o­w.

6.- Convierta los permisos rwxr-x--- en octal.

750.

7.- ¿Cuál sería la máscara más severa para todo el mundo excepto usted?

    A - 700
    B - 066
    C - 077
    D - 022

C. Retira todos los permisos a los miembros del grupo y a los demás.

8.- ¿Cuál es el efecto de la máscara 011 en un fichero? Indique los permisos del fichero en símbolos.

rw-rw-rw. Como el permiso x (1) está ausente por defecto, eso no cambia nada.

8.- Usted forma parte de los grupos «users» y «audio». ¿Tiene permiso de cambiar el grupo de uno de sus fichero a «vídeo»?

No, no forma parte del grupo «vídeo».

9.-cUn comando de conexión a un módem necesita poder leer y escribir en un periférico que pertenece a root. El comando pertenece también a root. Usted puede:

    A - Dar los permisos r y w del periférico a todo el mundo.
    B - Dar el permiso w al grupo del periférico y el permiso SGID al programa del mismo grupo.
    C - Dar el permiso SUID al programa del mismo propietario que el periférico.
    D - Hacer que su usuario pertenezca al mismo grupo que el periférico.

Prefiera la respuesta D con los permisos adaptados. Evite si es posible los permisos SUID/SGID, inútiles o en programas poco seguros.

10.- Quiere crear un directorio donde todo el mundo pueda escribir ficheros, donde todos los ficheros tengan el mismo grupo, pero donde nadie pueda suprimir los ficheros de los demás. ¿Cuáles deben ser los derechos?

rwxrwsrwt, o sea, 3777 en octal.

