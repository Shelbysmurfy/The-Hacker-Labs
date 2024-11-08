# RESOLUCIÓN DE LA MÁQUINA PAELLA

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/2720db0a-6591-48a9-a8fd-42cd43d90671)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/84d59c4d-a26c-4257-a437-7a4be5616740)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/2c3dd235-8a6f-426d-9797-a03c7580c0e7)

Entramos en el puerto 10000, que tiene habilitado el servicio http.

![image](https://github.com/user-attachments/assets/4d46bf90-74b4-4309-9a7f-436c6fa88cd3)

Hacemos whatweb para ver que encontramos, y al ver la versió 1.920 le hacemos un searchsploit para ver a que es vulnerable.

![image](https://github.com/user-attachments/assets/8f8db02a-6d8b-4e1d-9dd7-455b2f349bf1)

Nos metemos en el segundo, en el de autentificación, y vemos que encontramos.

![image](https://github.com/user-attachments/assets/892cdfbf-b723-4e99-a03b-522633d63c27)
![image](https://github.com/user-attachments/assets/751dba12-7d05-41b8-9e6d-4de25f390a33)

Abrimos el metasploit con msfconsole y buscamos por webmin.

![image](https://github.com/user-attachments/assets/4753986a-becd-400a-8802-347bc12abd50)

Vemos que en el apartado 10, en la descripción, esta el exploit del password_change.cgi, este se usaba en el codigo que hemos visto anteriormente, por tanto vamos a seleccionarlo con el comando use 10.

![image](https://github.com/user-attachments/assets/e981236c-312c-43a0-9d85-6718cced70ac)

Ahora haremos un "set RHOSTS" para seleccionar la máquina víctima y un "set LHOST" para la nuestra.

![image](https://github.com/user-attachments/assets/5212c428-3b45-4754-a03b-91b0c45d6ca7)

Una vez hecho esto usaremos el comando run para ejecutarlo, y podemos ver como ya estamos dentro y somos el usuario paella.

![image](https://github.com/user-attachments/assets/a0a1b75f-a0a0-4f49-b0fb-011cb5fd0b48)

Hacemos una reverse shell para poder manipular la consola de una manera más fácil.

![image](https://github.com/user-attachments/assets/6809c930-1d54-4fb1-8ed2-61b5edb171ae)
![image](https://github.com/user-attachments/assets/25367fa5-3a04-4f46-9f94-89f1941f32ff)

Hacemos el tratamiento de la tty y ya se nos ve todo perfecto y podemos trabajar adecuadamente.

![image](https://github.com/user-attachments/assets/187ca756-28c2-4449-8f46-bb9c3454b327)

Y si nos vamos al directorio /home/paella, encontramos la primera flag, la del usuario.

![image](https://github.com/user-attachments/assets/b45bd8ad-fca4-4760-8af8-06087cc1706a)

Encontramos la capabilitie gdb, también la podemos encontrar haciendo uso del linpeas.sh

![image](https://github.com/user-attachments/assets/940cc3f1-bb48-4bbd-861a-e3176a3ba721)

Nos vamos al GTFObins y ejecutaremos lo que nos diga.

![image](https://github.com/user-attachments/assets/a6af76de-fb9c-4752-8608-73c0f1e67ba6)

Ejecutamos el comando que nos indica, pero añadiendo el os.system("bash"), porque sino no funcionaba.

![image](https://github.com/user-attachments/assets/9e7f016a-02af-4203-b07b-22f152a18811)

Y finalmente conseguimos ser el usuario root.

![image](https://github.com/user-attachments/assets/7f6a25cf-32bb-4b67-886d-c81654906cf3)

