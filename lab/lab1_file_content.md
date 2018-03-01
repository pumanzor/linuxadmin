#### 1. Mostrar las primeras 15 lineas del archivo /etc/services.

head -12 /etc/services

#### 2. Mostrar las ultimas 2 lineas del archivo /etc/passwd

tail -1 /etc/passwd

#### 3. Use cat para crear el archivo llamado count.txt de la siguiente formas:

    cat > count.txt
    One
    Two
    Three
    Four
    Five (seguido de Ctrl-d)

#### 4. Use cp to make a backup of this file to cnt.txt.

cp count.txt cnt.txt
5. Use cat to make a backup of this file to catcnt.txt.

cat count.txt > catcnt.txt
6. Display catcnt.txt, but with all lines in reverse order (the last line first).

tac catcnt.txt
7. Use more to display /etc/services.

more /etc/services
8. Display the readable character strings from the /usr/bin/passwd command.

strings /usr/bin/passwd
9. Use ls to find the biggest file in /etc.

ls -lrS /etc
10. Open two terminal windows (or tabs) and make sure you are in the same directory in both. Type echo this is the first line > tailing.txt in the first terminal, then issue tail -f tailing.txt in the second terminal. Now go back to the first terminal and type echo This is another line >> tailing.txt (note the double >>), verify that the tail -f in the second terminal shows both lines. Stop the tail -f with Ctrl-C.

11. Use cat to create a file named tailing.txt that contains the contents of tailing.txt followed by the contents of /etc/passwd.

cat /etc/passwd >> tailing.txt
12. Use cat to create a file named tailing.txt that contains the contents of tailing.txt preceded by the contents of /etc/passwd.

mv tailing.txt tmp.txt ; cat /etc/passwd tmp.txt > tailing.txt
