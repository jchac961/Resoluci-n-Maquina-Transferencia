# Resolucion-Maquina-Transferencia
En este repositorio hago un breve writeup de la resolución de la maquina transferencia

# Enumeración de puertos

Una vez descargada neustra maquina abrimos la misma para iniciar a trabajar
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 234238" src="https://github.com/user-attachments/assets/09d08e8f-684c-47e3-bf6c-3474806e8125" />

Una vez nuestra maquina vulnerable se encuentre funcionando, hacemos una prueba en nuestra maquina atacante haciendo un ping
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 230430" src="https://github.com/user-attachments/assets/8ba8daf1-db97-49a0-b149-b5e06eab616b" />

Tambien en la captura de pantalla anterior podemos observar que utilizamos el comando nmap -sV 172.17.0.2 , para verificar la version de los puertos que tiene la maquiona abierta 

Luego procedi a utilizar el comando nmap -sV -sC 172.17.0.2 para utilizar los scripts de nmap y verificar si alguno tiene una vulnerabilidad muy obvia y vemos en la imagen que el puerto #21 tiene acceso mediante el usuario Anonimous
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 230441" src="https://github.com/user-attachments/assets/a0af5239-69fe-438e-89e0-bbacb1ac6496" />

# Busqueda de información relevante

Luego ingrese a la maquina por medio de ftp con el comando ftp y el usuario anonymous, una vez dentro de la maquina procedi a buscar algun archivo que me pudiera dar mas información y encontre una carpeta llamada pub, accedi a ella y dentro habia un archivo llamado usuarios.txt, el cual descargue utilizando el comando "get usuarios.txt"
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 232638" src="https://github.com/user-attachments/assets/b0e3d49f-3b0c-4b16-a204-4c86a9bfea88" />

# Resultados de la busqueda 
Una vez descargado el archivo procedi a abrirlo y encontramos 6 usuarios
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 232703" src="https://github.com/user-attachments/assets/6cd06063-cdbd-46bd-9c3d-1918cee891f9" />

# Eplotación de la maquina
Luego intente ingresar a la maquina mediante ssh, en el usuario admin la contraseña estaba errada, asi que intente ingresar con el usuario alberto el cual si me permitio ingresar a la maquina
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 232929" src="https://github.com/user-attachments/assets/b2774f46-d5c1-4505-8fcf-814a7748ba77" />

# Escalacion de privilegios

Ya dentro de la maquina verifique si se encontraban algunos archivos mal configurados, utilizando el siguiente comando: find / -perm -4000 -type f 2>/dev/null
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 233106" src="https://github.com/user-attachments/assets/4888e255-fda9-4315-ab5b-a4a3ca227951" />

Buscamos en la pagina www.gtfobins.github.io a ver si encontramos alguna manera de escalar privilegios
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-11 002219" src="https://github.com/user-attachments/assets/2b4a68ff-6e29-4695-a118-acb17fc8c27e" />

Luego procedimos a utilizar el comando encontrado haciendo la corrección de poner la ruta completa del archivo /usr/bin/bash y el comando -p para crear persistencia
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 233437" src="https://github.com/user-attachments/assets/3d3e7e83-3815-4f4e-ba7c-7ed5d0d1855f" />

Despues de haber ingresado este comando ya habiamos escalado privilegios y procedimos a buscar la carpeta root usando el comaando cd /, para salir del usuario alberto, e ingresamos a la carpeta root utilizando el comando cd root. Ya dentro de esta carpeta utilizamos el comando ls -la para listar todos los archivos y encontramos el archivo flag.txt el que procedimos a abrir con el comando cat flat.txt
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 233759" src="https://github.com/user-attachments/assets/a5c5bb08-6b7e-4875-a8ed-73272c4bc6f0" />

El resultado de este archivo lo copiamos y pegamos en la maquina docker y asi completamos esta maquina con extitos
<img width="1920" height="1140" alt="Captura de pantalla 2025-12-10 233816" src="https://github.com/user-attachments/assets/8c434b1c-320f-4860-bec1-7e201d5a6aba" />

