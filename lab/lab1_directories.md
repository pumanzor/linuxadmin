#### 1. Mostrar su actual directorio de trabajo.
pwd

#### 2. Cambiar de manera directa al directorio /etc
cd /etc

#### 3. volver el directorio de trabajo del usuarios
cd (and the enter key)

#### 4. Ir al directorio padre del directorio actual
cd .. (with space between cd and ..)

#### 5. ir al directorio raiz
cd /

#### 6. Listar el contenido del directorio raiz
ls

#### 7. Listar el directorio raiz en formato de listado
ls -l

#### 8. Desde el lugar que se encuentra listar el contenido del directorio.
ls /sbin

#### 9. Listar el contenido del directorio /boot en el formato humano.
ls -lh /boot

#### 10. Crear el directorio "testdir" en su directorio home.
mkdir testdir

#### 11. ir al directorio /etc y desde ese lugar crear el directorio "newdir" en el directorio home.
cd /etc ; mkdir /home/user/newdir

#### 12. Create in one command the directories ~/dir1/dir2/dir3 (dir3 is a subdirectory from dir2, and dir2 is a subdirectory from dir1 ).
mkdir -p ~/dir1/dir2/dir3

#### 13. Remove the directory testdir.
rmdir testdir

#### 14. If time permits (or if you are waiting for other students to finish this practice), use and understand pushd and popd. Use the man page of bash to find information about these commands.
man bash           # opens the manual
/pushd             # searches for pushd
n                  # next (do this two/three times)
The Bash shell has two built-in commands called pushd and popd. Both commands work with a common stack of previous directories. Pushd adds a directory to the stack and changes to a new current directory, popd removes a directory from the stack and sets the current directory.

paul@debian7:/etc$ cd /bin
paul@debian7:/bin$ pushd /lib
/lib /bin
paul@debian7:/lib$ pushd /proc
/proc /lib /bin
paul@debian7:/proc$ popd
/lib /bin
paul@debian7:/lib$ popd
/bin
