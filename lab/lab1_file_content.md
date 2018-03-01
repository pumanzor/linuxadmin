#### 1. Mostrar las primeras 15 lineas del archivo /etc/services.

head -12 /etc/services

#### 2. Mostrar las ultimas 2 lineas del archivo /etc/passwd

tail -1 /etc/passwd

#### 3. Use cat para crear el archivo llamado count.txt de la siguiente forma:

    cat > count.txt
    One
    Two
    Three
    Four
    Five (seguido de Ctrl-d)

#### 4. Use cp para crear un respaldo de es archivo (count.txt) como cnt.txt.

cp count.txt cnt.txt

#### 5. Use cat para crear un respaldo del archivo de este archivo como catcnt.txt.

cat count.txt > catcnt.txt

#### 6. Muestre el contenido de catcnt.txt, pero con todas las lineas en orden inverso (ultima linea primero).

tac catcnt.txt

#### 7. Use more para mostrar el contenido de /etc/services.

more /etc/services

#### 8. Use ls para buscar el archivo mas grande dentro de /etc.

ls -lrS /etc

#### 9. Abrir 2 emulardores de terminales y asegurese de que ambos se encuentran en el mismo directorio. 

ejecute

line > tailing.txt 

en el primer terminal, luego ejecute

tail -f tailing.txt 

en el segundo terminal. 

luego vuelva al primer terminal y ejecute nuevamente:

line >> tailing.txt (note the double >>),

verifique que tail -f en el segundo terminal muestra ambas lineas. salir de tail -f con Ctrl-C.
