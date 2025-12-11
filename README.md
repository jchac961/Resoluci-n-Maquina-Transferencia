# Resoluci-n-Maquina-Transferencia
En este repositorio hago un breve writeup de la maquina transferencia

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
