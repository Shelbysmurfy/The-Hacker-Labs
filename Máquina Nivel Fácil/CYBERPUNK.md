# RESOLUCIÓN DE LA MÁQUINA CYBERPUNK

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/4930c672-24a3-4dc1-93d4-00e716468127)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/2cb77a6d-f42c-4836-ac6f-538b82c0d963)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/81c00fea-542f-40bc-a634-39563159f548)
![image](https://github.com/user-attachments/assets/1f2f0fa0-6e2b-4f66-a233-03e1b35f9847)
![image](https://github.com/user-attachments/assets/4e068b9b-cd7b-4a4d-99ea-6cddb86d6886)

Viendo que el puerto 80 esta abierto, entramos en el para ver que web nos encontramos.

![image](https://github.com/user-attachments/assets/afee8bec-d6f6-44a9-9e36-d9875ecb5d74)

Ahora con la herramienta gobuster buscaremos directorios que esten activos en la web.

![image](https://github.com/user-attachments/assets/89ba572c-7c31-4379-baa5-eeec90c1c490)

Vemos que que hay dos de todos los que me han salido que tiene codigo 200, por tanto vamos a probarlos.

El index.html no me muestra nada, pero el secret.txt muestra lo siguiente:

![image](https://github.com/user-attachments/assets/96222537-1bbd-4b41-8518-c4fa1b2a2b20)

Al principio hemos visto que en el servicio ftp podemos entrar a través del usuario anonymous.

Nos encontramos con los mismos archivos que hemos visto antes gracias al gobuster.

![image](https://github.com/user-attachments/assets/85f99951-4ebd-4f83-b4a1-2071e3b5d51b)

Intentaremos hacer reverse shell subiendo un archivo .php al servicio ftp, para ello primero hemos de crearlo en el nuestro.

![image](https://github.com/user-attachments/assets/0306dc3d-228b-46a9-abbe-84adf8729527)

Una vez creado pondremos el mismo directorio desde donde esta el archivo, y entraremos en el servicio ftp.

![image](https://github.com/user-attachments/assets/62fe7ab8-0383-4a99-8b9b-58faf4cf3348)

Una vez subido iremos a la web y intentaremos abrirlo y inyectar código gracias a el.

![image](https://github.com/user-attachments/assets/bd3e29b0-98ec-44fd-ad0e-ac0ef7d40899)

Abrimos el BurpSuite y hacemos lo siguiente para poder ejecutar comandos desde nuestra terminal.

Ponemos esto y lo encodeamos como url.

![image](https://github.com/user-attachments/assets/d64cc563-37a3-40cc-a143-626cd562f1de)

Una vez hecho lo pondremos en nuestra web junto a unn bas -c "lo que hemos encodeado"

![image](https://github.com/user-attachments/assets/242f3655-5725-4127-82a5-c23aac522b5c)

Mientras estaremos en escucha desde nuestra terminal para poder obtener acceso.

![image](https://github.com/user-attachments/assets/1e22ef8e-f9d2-4a93-89fd-ba22814c5266)

Después de investigar un rato nos encontramos con esto en el directorio opt.

![image](https://github.com/user-attachments/assets/9dcd194b-d4cf-4fca-bc3d-0ad5b9bd3335)

Buscamos que es en internet, nos sale que es un brainfuck, por tanto vamos a buscar como decodearlo.

![image](https://github.com/user-attachments/assets/cf383e49-0969-4556-8d82-a5b2e9e9793a)

Entramos como usuario arasaka y en el directorio raiz nos encontramos con la flag user.

![image](https://github.com/user-attachments/assets/57b22e41-6477-4eb8-92a0-fc0c34d2b18e)

Al hacer sudo -l nos muestra esto: 

![image](https://github.com/user-attachments/assets/54c0d559-5374-4705-96ec-164429833925)

Haremos python hyjacking.

Primero crearemos un archivo .py con este contenido.

![image](https://github.com/user-attachments/assets/387010e1-65da-407f-a2b8-227035119bbf)

Segundo ejecutaremos esto para poder tener permisos de root.

![image](https://github.com/user-attachments/assets/3f85760f-5b13-4bd0-9bd1-3d9a3bea1f93)

Y por ultimo ejecutaremos estos dos comandos, para poder convertirnos en root.

![image](https://github.com/user-attachments/assets/16d17b7c-6ebc-4ed7-b55c-cf7356a4fccd)

Y tendríamos la segunda flag que buscamos, la del usuario root.

![image](https://github.com/user-attachments/assets/e61b7646-9ae0-4e22-a7c7-0edd5c0f46d5)

































