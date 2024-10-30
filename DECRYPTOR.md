# RESOLUCIÓN DE LA MÁQUINA DECRYPTOR

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/82ecc940-3099-4a52-b959-49b3e121e345)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8468ae53-ec6f-44dd-8703-e3192f047902)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/22df490f-a91b-4871-afa7-b4878e21b2fe)

Vamos al puerto 80, y si inspeccionamos la web nos encontramos con esto: 

![image](https://github.com/user-attachments/assets/ab5fdfbc-583c-4328-beac-d4da90a7ef68)

Lo decodeamos.

![image](https://github.com/user-attachments/assets/d82ed7d1-e032-4bb7-bec1-ca4cd5cf8ff3)

Despues de probar varias combinaciones en el puerto ssh y ftp, hemos encontrado la correcta.

En el puerto ftp ponemos como usuario: mario y como contraseña: marioeatslettuce

![image](https://github.com/user-attachments/assets/2849086a-50f7-4bcb-a185-4120cdb39754)

Llendo al directorio home vemos que hay otro usuario llamado chiquero.

Vemos un archivo, parece ser un keepass, por tanto nos lo transferimos a nuestra máquina.

![image](https://github.com/user-attachments/assets/f8d0df14-2b29-4579-8e9a-98d6d8faf40b)

Hacemos un keepass2john para convertir el archivo que tenemos en un hash.

![image](https://github.com/user-attachments/assets/4cc4742a-9306-4ff1-bf70-e029419b5fad)
![image](https://github.com/user-attachments/assets/f20d4fcf-9fe5-476e-bcfe-38bb06568b1f)

Y ahora hacemos un john con el diccionario rockyu para sacar credenciales del hash.

![image](https://github.com/user-attachments/assets/168003d9-becd-4562-abba-9de39bd95be1)

Ya podemos entrar en el kpcli con el documento user.kdbx y las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/790c912e-dc18-4d75-bebd-acdad78cf2e6)

Entramos como root, y nos sale solo una entrada, la vemos con show, y para ver el contenido que hay en rojo hacemos -f

![image](https://github.com/user-attachments/assets/d5e05c44-9ddb-43b3-8e6e-85f20c1610b4)

Sabiendo estas nuevas credenciales entraremos con el servicio ssh.

![image](https://github.com/user-attachments/assets/ba03c4db-2e96-43a1-a4bb-7dba4da83faa)

Haciendo un sudo -l nos muestra esto: 

![image](https://github.com/user-attachments/assets/a083f239-7048-40f6-b05f-cacdd2409c7c)

Vamos al GTFObins y vemos lo siguiente: 

![image](https://github.com/user-attachments/assets/b4e019c9-2feb-4f93-a623-9d2d690c6ccc)

Este comando nos permite cambiar el propietario y grupo de un fichero o directorio.

![image](https://github.com/user-attachments/assets/f11d66f0-07f9-4349-bbcf-6e36538175f8)

Y ya somos root.

![image](https://github.com/user-attachments/assets/45ec896d-21ca-4cc0-95dc-70570de09a44)









