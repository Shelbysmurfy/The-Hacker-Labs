# RESOLUCIÓN DE LA MÁQUINA THEFIRSTAVENGER

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/9f039636-8da7-4751-b95e-81635962aff6)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/2003aaa4-5a30-4615-8623-ebdb121966af)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/1550a1a1-b10f-4c67-aef1-fa16a76dcff3)

Abrimos el puerto 80 y no hay nada.

![image](https://github.com/user-attachments/assets/88967e4d-8a83-4efc-96dd-e741b4c92dba)

Hacemos fuerza bruta con gobuster y encontramos esto: 

![image](https://github.com/user-attachments/assets/ba9174a3-3b7c-4ea7-a632-27a393986a90)

![image](https://github.com/user-attachments/assets/838b3c2a-dd03-46bc-82b0-9bdd1807416c)

Y ahora volvemos a hacer fuerza bruta, pero esta vez añadiendo el directorio que hemos conseguido antes.

![image](https://github.com/user-attachments/assets/2d6efce5-de95-4930-9027-d2976f2df07e)

La dirección del wp-admin no carga, ya que tenemos que añadir en el /etc/hosts, la dirección de thefirstavenger.thl

![image](https://github.com/user-attachments/assets/e6664f34-778a-4c78-8fb5-f5dde6720b28)

Hacemos un wpsacn de la dirección "http://thefirstavenger.thl/wp1/".

![image](https://github.com/user-attachments/assets/019412d5-6731-4541-9d42-35e922ee082e)

Encontramos el usuario admin.

![image](https://github.com/user-attachments/assets/3171aaa1-dbbc-4c82-a2b6-59942d56b8d6)

Ahora hacemos un wpscan indicando que el usuario es admin y en la contraseña ponemos el diccionario rockyou.

![image](https://github.com/user-attachments/assets/247f12c3-ff73-4b3e-9278-840335feda16)

Y encontramos la contraseña del usuario admin.

![image](https://github.com/user-attachments/assets/55d39b84-209d-49dc-9da3-ebf4437c9be2)

Nos vamos a pluggins y instalamos el File Manager.

![image](https://github.com/user-attachments/assets/13cf95cf-0431-4c9c-acd7-f0f02d756a93)

Entramos en /wp-content/themes/, y seleccionames el que queramos, dentro de el creamos un archivo php.

![image](https://github.com/user-attachments/assets/1792a716-12ac-4b38-bc56-86ea5f939b13)

Lo abrimos desde la página web y ya podemos inyectar código.

![image](https://github.com/user-attachments/assets/221b98d3-ad5d-460d-afdb-484772871df5)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/270cdb5a-c647-47f2-8a2d-2c8f16939fbd)

Nos ponemos en escucha desde la terminal y conseguimos acceso.

![image](https://github.com/user-attachments/assets/fffdeabb-175f-4966-883f-bac8403a0c28)

Si visualizamos el wp-config.php encontramos unas credenciales de la base de datos.

![image](https://github.com/user-attachments/assets/a3927ffd-3a87-4f63-bb7e-69e5bc19060b)

![image](https://github.com/user-attachments/assets/bb336edb-a93b-4992-a935-4e684552c537)

Entramos en el servicio de mysql.

![image](https://github.com/user-attachments/assets/3c03bc73-6111-47ac-adea-916a98f3907a)

Antes de poder entrar hemos tenido que buscar la ip de el servicio de mysql, que pertenece al puerto 3306.

![image](https://github.com/user-attachments/assets/92d6b196-623b-4060-ac8f-ffe0603b3909)

Una vez dentro, hemos encontrado una lista de usuarios.

![image](https://github.com/user-attachments/assets/80d6efe1-d6b0-412b-b5d5-dd96b867da73)

En el directorio home teníamos el usuario steve.

![image](https://github.com/user-attachments/assets/f86b884f-da0d-4c6e-af35-6d5ebd30cf91)

La contraseña del usuario Steve es un md5.

![image](https://github.com/user-attachments/assets/d6c0817f-4602-460e-8d3b-6def0e03594b)

Vamos a guardarla y a intentar romperlo con john.

![image](https://github.com/user-attachments/assets/26f96c37-bfcf-4f58-a385-38c182cd1a6b)

Entramos como el usuario steve con las cerdenciales obtenidas.

![image](https://github.com/user-attachments/assets/23f7ecf2-719b-41a9-8881-80dddaaa1ca0)

Hacemos ls y podemos ver la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/cf46f98c-fa02-4319-93ba-bd00559d78c7)

Usando el comando ss -tunlp vemos que el puerto 7092 esta corriendo de forma local.

![image](https://github.com/user-attachments/assets/59d71bbc-f173-4238-bd8c-1d16588efd87)

Haremos un port forwarding con ssh puesto que tenemos credenciales, en este caso le indicamos que queremos traernos el puerto 7092 de la maquina victima al puerto 7092 de nuestro localhost.

![image](https://github.com/user-attachments/assets/397d1208-8e4c-4409-a875-316b866ba2d0)
![image](https://github.com/user-attachments/assets/1b473d22-f6e3-40c1-a0ac-0fffe50a08d6)

Accedemos al servicio que hemos habilitado desde nuestro navegador.

![image](https://github.com/user-attachments/assets/6e5faff8-cf1c-49b3-ad5f-c00baea9c9b4)

Vemos que es vulnerable a SSTI.

![image](https://github.com/user-attachments/assets/f689f778-e829-4171-8e22-80b4a329e6f0)

Nos vamos al link: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/Python.md#jinja2---basic-injection

Y cogemos el comado de Exploit de SSTI para ejecutarlo.

![image](https://github.com/user-attachments/assets/bd5a2c42-73dc-4750-8fd7-768cc3f1a3c5)

Cambiamos la parte donde pone id por "chmod u+s /bin/bash", y ejecutamos bash -p en la máquina y ya tenemos acceso como root.

![image](https://github.com/user-attachments/assets/8f0f315f-a43e-4479-9da9-8b117ae73614)


















