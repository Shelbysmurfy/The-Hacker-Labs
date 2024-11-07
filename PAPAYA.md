# RESOLUCIÓN DE LA MÁQUINA PAPAYA

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/280963b7-ed16-42da-872e-e1ab3dd4f163)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/28233986-8540-4828-8e7b-1fb57c46746a)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/d4ff86cd-02d5-4271-9dd5-f713faad362d)
![image](https://github.com/user-attachments/assets/ba724ade-1b06-4287-acc8-370fda6e8c4f)

Abrimos el servicio 21 ftp, con el usuario anonymous.

![image](https://github.com/user-attachments/assets/c46c487e-9440-4a67-86f1-1b0609dcc703)

Haciendo ls -l vemos que hay un archivo llamado secret.txt, nos lo pasamos a nuestra máquina y lo abrimos.

![image](https://github.com/user-attachments/assets/9903be50-849f-4b1a-a4bd-2bffa791033b)

![image](https://github.com/user-attachments/assets/528e8b6e-5f41-4884-b529-8daa0b163c1e)

Utilizamos la técnica rot13 para desencriptarlo.

![image](https://github.com/user-attachments/assets/1896e3a6-f48d-40f9-a16a-8a82d87e84fd)

Cuando ponemos la IP de la máquina víctima nos redirije a papaya.thl y no nos va, nos vamos al /etc/hosts para arreglarlo.

![image](https://github.com/user-attachments/assets/165ece33-6615-43be-a8e0-a221e880ab31)

Recargamos la página y nos muestra esto: 

![image](https://github.com/user-attachments/assets/39df1b8f-392f-49a8-884e-c43223a549b8)

Con gobuster encontramos el directorio /themes/prueba y que dentro suyo esta el el archivo prueba.php

![image](https://github.com/user-attachments/assets/c0552549-0439-422c-acf3-8b4693a37389)

Si hacemos los que nos dice podemos ejecutar comandos.

![image](https://github.com/user-attachments/assets/62f359cb-4bbd-4304-ab90-356e4a5d9bff)

Abrimos el BurpSuite y hacemos lo siguiente para poder ejecutar comandos desde nuestra terminal.

Ponemos esto y lo encodeamos como url.

![image](https://github.com/user-attachments/assets/d26b148d-8d82-4a21-8b2a-bec72a26fb52)

Una vez hecho lo pondremos en nuestra web junto a un bash -c "lo que hemos encodeado"

![image](https://github.com/user-attachments/assets/e18865c2-50cb-42ce-9ff2-9db6629da966)

Mientras estaremos en escucha desde nuestra terminal para poder obtener acceso.

![image](https://github.com/user-attachments/assets/32e10a80-a10d-4f24-91ad-3f44091f117a)

En el directorio elKarte hay el archivo Settings.php, donde encontramos unas credenciales.

![image](https://github.com/user-attachments/assets/562470df-fd56-4e0c-8bb7-4c7e42ca6e7e)

Haciendo uso del comando ss -tunlp encontramos un servicio corriendo en el puerto 3306, que viene a ser el de mysql, por tanto vamos a usar las credenciales que hemos encontrado antes para ver si podemos entrar.

![image](https://github.com/user-attachments/assets/2d11f01c-9e29-46e4-8b0f-e27cec290060)

Efectivamente si podemos entrar.

![image](https://github.com/user-attachments/assets/2dd1de15-0ce1-497c-81cb-f1d540020f8a)

Dentro encontramos mucha información pero antes vamos a ir a otra cosa.

En el directorio /opt nos encontramos un archivo.zip encriptado, nos lo pasamos a nuestra máquina.

![image](https://github.com/user-attachments/assets/dc1c2862-a177-4a66-a526-f67a9c0a794a)

![image](https://github.com/user-attachments/assets/21e33200-609e-4cf6-bf0c-3d45af69af50)

Usamos zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/a92263ca-39d9-4cad-8d3f-b6fc6c6935bc)
.. 
Y ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/29f60d63-c9ad-4641-9c5e-a13fe1ef9a04)

Una vez hecho esto, hacemos un unzip del archivo, esto nos devuelve el archivo pass.txt

![image](https://github.com/user-attachments/assets/da982d2c-e270-4501-a0a4-24ee0059f585)

Sabiendo esta credencial vamos a intentar entrar con el usuario: papaya y la contraseña:papayarica por el servicio ssh.

![image](https://github.com/user-attachments/assets/2cad30c4-4d87-4f1d-8c86-538d766029e7)

Haciendo ls encontramos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/388f9175-4710-47da-8b61-4611b9f78a9a)

Y si hacemos sudo -l encontramos lo siguiente: 

![image](https://github.com/user-attachments/assets/832a8c4b-ffe6-48a9-b9a1-809a072ccd0c)

Nos vamos al GTFObins y buscamos por scp.

![image](https://github.com/user-attachments/assets/3abaaece-5f28-4d4c-a73d-ff7904018d8d)

Seguimos estos pasos y conseguimos ser root.

![image](https://github.com/user-attachments/assets/8cf3149b-c4ad-4c01-919b-23a05ea9355d)


