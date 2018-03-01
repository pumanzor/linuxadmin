#### 1. Mostrar su actual directorio de trabajo.
pwd

#### 2. Cambiar de manera directa al directorio /etc
cd /etc

#### 3. volver el directorio de trabajo del usuario
cd (and the enter key)

#### 4. Ir al directorio padre del directorio actual
cd .. (with space between cd and ..)

#### 5. ir al directorio raiz
cd /

#### 6. Listar el contenido del directorio raiz
ls

#### 7. Ver el contenido del directorio raiz como listado
ls -l

#### 8. Desde el lugar que se encuentra listar el contenido del directorio.
ls /sbin

#### 9. Listar el contenido del directorio /boot en el formato humano.
ls -lh /boot

#### 10. Crear el directorio "testdir" en su directorio home.
cd; mkdir testdir

#### 11. ir al directorio /etc y desde ese lugar crear el directorio "newdir" en el directorio home.
cd /etc ; mkdir /home/user/newdir   (user es el nombre de usuario)

o

mkdir ~/newdir

#### 12. Crear en un solo comando los directorios dir1/dir2/dir3 (dir3 es subdirectorio de dir2 y dir2 es subdirectorio de dir1) 
mkdir -p ~/dir1/dir2/dir3

o

mkdir -p /home/user/dir1/dir2/dir3

#### 13. Eliminar el directorio testdir.
rmdir testdir

