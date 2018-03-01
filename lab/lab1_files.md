#### 1. Ver los archivos del directorio /bin
ls /bin

#### 2. Mostrar que tipo de archivo es /bin/cat, /etc/passwd ay /usr/bin/passwd.
file /bin/cat /etc/passwd /usr/bin/passwd

### 3a. Bajar el archivo image.jpg y Linux.pdf desde http://192.168.200.250/image.jpg (wget http://192.168.200.250/files/linus.jpg y wget http://192.168.200.250/files/whitepaper.pdf)

wget http://192.168.200.250/files/linus.jpg
wget http://192.168.200.250/files/linus.png
wget http://192.168.200.250/files/whitepaper.pdf

#### 3b. Mostrar el tipo de archivo de linus.jpg and whitepaper.pdf

file linus.jpg whitepaper.pdf

#### 3c. Renombre linus.jpg a linus.pdf (use mv).

mv linus.jpg linus.pdf

#### 3d. Mostrar el tipo de archivo de linus.pdf y whitepaper.pdf

file linus.pdf whitepaper.pdf

#### 4. Crear el directorio ~/lab1 e ingrese en el

mkdir ~/lab1 ; cd ~/lab1

#### 5. Crear los arvhivos today.txt y yesterday.txt en lab1.

touch today.txt yesterday.txt

#### 6. Cambie la fecha de yesterday.txt que coincida con la fecha de ayer.

touch -t 201803011205 yesterday.txt (sustituya con la fecha de ayer)

#### 7. Copiar yesterday.txt como copy.yesterday.txt

cp yesterday.txt copy.yesterday.txt

#### 8. Renombrar copy.yesterday.txt como kim

mv copy.yesterday.txt kim

#### 9. Crear el directorio con el nombre ~/testbackup y copie todos los archivos desde ~/lab1 dentro de el.

mkdir ~/testbackup ; cp -r ~/lab1 ~/testbackup/ 

#### 10. Use un comando para eliminar el directorio ~/testbackup y todos los archivos que se encuentran dentro.

rm -rf ~/testbackup 

#### 11. Crear un directorio ~/etcbackup y copie todos los archivos *.conf desde /etc dentro de el

cp -r /etc/*.conf ~/etcbackup

Only *.conf files that are directly in /etc/ are copied.

