#### 1. compruebe que el archivo /bin/cat existe. Que tipos de archivos son /bin/dd y /bin/echo

ls /bin/cat ; file /bin/cat
ls /bin/dd ; file /bin/dd
ls /bin/echo ; file /bin/echo

#### 2. Cual es el tamaño de los archivos del kernel (vmlinu*) que se encuentran dentro de /boot ?

ls -lh /boot/vm*

#### 3. Crear el directorio ~/test. Luego ejecute los siguientes comandos:

    cd ~/test
    dd if=/dev/zero of=zeroes.txt count=1 bs=100
    od zeroes.txt
    
dd copiara una vez (count=1) un bloque de 100 bytes de tamaño (bs=100) desde el archivo /dev/zero en ~/test/zeroes.txt. 
puede ud describir la funcionalidad del archivo /dev/zero ?

/dev/zero es un dispotivico especial en Linux. Puede ser considerado como una fuente de ceros. Ud no puede enviar algo
hacia /dev/zero, pero ud puede leer ceros desde el.

#### 4. ejecute el siguiente comando:

dd if=/dev/random of=random.txt count=1 bs=100 ; od random.txt

dd copiara una vez (count=1) un bloque de tamaño 100 bytes (bs=100) desde el archivo /dev/random hacia ~/test/random.txt. 
puede explicar la funcionalidad del archivo /dev/random ?

/dev/random actua como un generador de numeros aleatorios en Linux.

#### 5. Use el comando cat o more para ver el contenido de /etc/hosts y /etc/resolv.conf.
Para que sirven estos 2 archivos?

/etc/hosts contiene nombre de hosts con sus direcciones IP
/etc/resolv.conf deberia contener la direccion ip de los servidores dns.

#### 6. Ver el contenido del archivo /proc/cpuinfo. Cual es el modelo del procesador?


#### 7. Puede ud ingresar al directorio /root como usuario normal?



