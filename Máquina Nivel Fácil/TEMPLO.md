# RESOLUCIÓN DE LA MÁQUINA TEMPLO

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/5747aa61-8468-4ad2-b829-8205b0c1763b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8afa4b02-ad87-4e1b-a769-e929f8439dc4)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/93e0f629-81f9-4313-993a-51ef8aad29df)

Si observamos la web en el apartado de about no dice esto: 

![image](https://github.com/user-attachments/assets/b59fe9ab-b931-406b-b43b-dd85ee12f1a1)

Si hacemos gobuster nos sale un directorio que tiene un archivo txt, que contiene información. 
Nos dice que vayamos al /opt, quiere decir que si conseguimos entrar con el servicio ssh ya sabemos donde ir.

![image](https://github.com/user-attachments/assets/b1f07fd6-e2c6-4bfe-b56f-061cbb1ae408)

Si usamos NAMARI como directorio nos redirige a una página donde podemos subir archivos.

![image](https://github.com/user-attachments/assets/75807610-4f6c-4941-9f38-ccdf2231eae5)

Creamos un archivo php para subirlo a la web.

![image](https://github.com/user-attachments/assets/6fd9b2c0-cd45-4842-9f89-f5c67811d696)

![image](https://github.com/user-attachments/assets/6eef3705-229d-406e-8ce9-1a1f7421d832)

Si hacemos gobuster con el directorio /NAMARI vemos el directorio uploads, donde miraremos si podemos entrar al archivo que hemos subido.

![image](https://github.com/user-attachments/assets/b37eb90a-7d10-4850-a176-c66e8d78db31)

Ponemos nuestro archivo en el directorio uploads pero no lo encuentra.

![image](https://github.com/user-attachments/assets/ef7b3583-8b99-4962-83f4-62f0e3e14c66)

En la subida de archivos, en el apartado de incluir archivo, podemos ejecutar comandos, es vulnerable a LFI.

![image](https://github.com/user-attachments/assets/f1da1f38-5db2-4052-b5f6-d55c6f923e27)

![image](https://github.com/user-attachments/assets/d3db05ed-2b76-4516-8092-a3264daae09d)

Vamos a hacer uso de wrappers para poder leer el index.php, y así saber porque no encuentra el archivo php que hemos subido.

![image](https://github.com/user-attachments/assets/78c55deb-afa6-493f-a336-58a929ede894)

![image](https://github.com/user-attachments/assets/8be7d59d-d170-431f-a01d-85676d2d3548)

Lo decodeamos para saber que contiene este archivo.

![image](https://github.com/user-attachments/assets/f0eae811-e508-413e-a364-06443a08151f)

Podemos ver que aplica un rot13 al nombre que le hemos puesto al archivo que hemos subido.

![image](https://github.com/user-attachments/assets/30808a0f-4229-4757-9733-93733ae4c86c)

Pasamos nuestro nombre a rot13, y así es como tendría que estar subido en el servidor.

![image](https://github.com/user-attachments/assets/6ca6a1b1-7c19-40d4-9810-f4bcbee49f0f)

Ahora no nos muestra ningún error.

![image](https://github.com/user-attachments/assets/b88b35db-e6a2-4a33-b9ab-8f7020587c8f)

Y si añadimos "?cmd=whoami", nos muestra quien somos.

![image](https://github.com/user-attachments/assets/11be497a-68cb-4b30-9222-a89df82ccc0f)

Pudiendo ejecutar comandos, vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/039fd172-dfe3-4f13-8322-bdef6056fc36)

Nos ponemos en escucha y ya tenemos acceso a la máquina.

![image](https://github.com/user-attachments/assets/23fb1c25-9202-4e10-8f85-06a593cc2f5d)

Recordando la pista que nos habían dado antes, vamos al directorio opt. Buscando en los directorios ocultos vemos el .XXX y dentro de el hay el archivo backup.zip 

![image](https://github.com/user-attachments/assets/c058b724-d807-42bf-b448-7ec981ec40ff)

Nos lo traemos a nuestra máquina.

![image](https://github.com/user-attachments/assets/42de26ea-e655-4a61-949d-844e003405aa)

![image](https://github.com/user-attachments/assets/24d4b390-3cbd-4d27-a751-816a6b14ef4e)

Usamos zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/006eb115-c669-4f22-9cbd-d45d2ab57761)

Ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/2609310e-2334-4fc6-ac01-8ed536d2c1a5)

Una vez hecho esto, hacemos un unzip del archivo, esto nos devuelve el archivo Rodgar.txt

![image](https://github.com/user-attachments/assets/1efa4447-dbaa-40bc-940b-77353dc6317c)

Sabiendo esta credencial vamos a intentar entrar con el usuario: rodgar y la contraseña: 6rK5£6iqF;o|8dmla859/_ por el servicio ssh.

![image](https://github.com/user-attachments/assets/99e5ec80-3c6a-4100-9c27-9d08cf1a6da3)
![image](https://github.com/user-attachments/assets/d1a00386-7b68-4c89-967b-e1fe169c7f06)

Hacemos ls y vemos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/8cc73d2c-b6ab-4f1e-945c-cf753151fd54)

Si hacemos id vemos que tenemos el permiso lxd.

![image](https://github.com/user-attachments/assets/35906a38-f938-409c-aa44-2f2c50a58ecf)

Vemos que es vulnerable a Escalda de Privilegios.

![image](https://github.com/user-attachments/assets/6d3c6f47-eabb-4346-8dd6-00592a0eba7c)

Seguiremos los pasos de esta web: https://medium.com/@mstrbgn/privilege-escalation-using-lxd-lxc-group-assignment-to-a-user-a-security-misconfiguration-a4892f611d6f

![image](https://github.com/user-attachments/assets/9dee1010-2205-4e4c-8cda-dee803e2adfc)

![image](https://github.com/user-attachments/assets/faf86a83-55e6-4f98-beb5-4659fa7b387a)

![image](https://github.com/user-attachments/assets/4ea2487c-eba8-4fbc-bcb7-94b690b8e83a)

![image](https://github.com/user-attachments/assets/cdc23688-504b-4fbf-ab4a-78530c43a61d)

![image](https://github.com/user-attachments/assets/0de178d1-a8bd-4e7e-ae6a-530736de0d25)

![image](https://github.com/user-attachments/assets/9f594a44-7b0d-4a1d-897f-0d01af14ed69)

![image](https://github.com/user-attachments/assets/4cc0f772-8e07-4a92-a95c-786ebe273131)

![image](https://github.com/user-attachments/assets/20911ecf-ad27-470e-9a00-dcc60f1964b9)

![image](https://github.com/user-attachments/assets/25519ad4-7ac5-4732-9227-903a2e59c439)

![image](https://github.com/user-attachments/assets/9b151ab9-1acc-41e3-b1e3-a044fbf27fc8)

![image](https://github.com/user-attachments/assets/e63cc0b3-3078-4fb3-ba40-46cfb100b96a)

Y si ahora entramos en este directorio ya tenemos permisos de root y podemos conseguir la flag de este usuario.

![image](https://github.com/user-attachments/assets/802c4d30-977a-4408-87eb-4dfa7f46f595)

















