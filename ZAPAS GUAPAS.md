# RESOLUCIÓN DE LA MÁQUINA ZAPAS GUAPAS

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/3195eae5-4543-41f2-83df-260f36316d87)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/14b3e50c-49ee-4778-89f0-e6efbe7536d8)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/8fe042c5-8a22-4a0e-8ef2-7a88a7ac1f15)

Viendo que el puerto 80 esta abierto, entramos en el para ver que web nos encontramos.

![image](https://github.com/user-attachments/assets/b259d7e9-be2f-4905-b8dc-3973dcef9b25)

No encontramos nada interesante, por tanto buscaremos directorios con la herramienta dirsearch, que funciona muy similar que el Gobuster.

![image](https://github.com/user-attachments/assets/a945fc39-68ee-40a0-9a2c-71f085e8368c)

Entramos en el directorio login.html

![image](https://github.com/user-attachments/assets/bbdd6248-1a6e-46db-a2d1-1204d1ecf672)

Después de estar probando un rato, vemos que en el apartado de la contraseña se puede inyectar código como si se tratara de una bash.

Ponemos id y nos muestra esto.

![image](https://github.com/user-attachments/assets/d70f7d8f-7e72-4cca-b3d0-1b41273fa23f)

Y al poner cat /etc/passwd nos muestra tres usuarios: root, proadidas y pronike.

![image](https://github.com/user-attachments/assets/343e83b4-047b-425d-af9f-904db4b0ff4f)

Al saber que podemos inyectar comandos, haremos una reverse shell para poder acceder de manera remota al sistema.

Ponemos la IP de nuestra máquina, un puerto cualquiera, y usamos busybox.

![image](https://github.com/user-attachments/assets/f3c7e2e7-c78e-4ca8-b896-d9b38ca3cec1)

Y como podemos ver ya tenemos acceso al sistema.

![image](https://github.com/user-attachments/assets/070e10a8-4b14-4422-989f-ff88ae54ee8c)

Seguidamente haremos el tratamiento TTY.
LINK: https://invertebr4do.github.io/tratamiento-de-tty/#

![image](https://github.com/user-attachments/assets/6e8fda56-e18e-4d44-baab-cc8dfb1b1a04)

Entramos dentro de el usuario proadidas y pronike y nos encontramos dos archivos .txt

![image](https://github.com/user-attachments/assets/b9b8a12a-7829-4867-bf79-b75caf8e198a)

![image](https://github.com/user-attachments/assets/46e6183d-d0c5-4677-8d67-2835096af57c)

Como en ninguno de ellos podemos encontrar ni hacer nada, nos vamos otra vez al directorio raiz donde vemos el directorio opt, el cual contiene un archivo .zip dentro.

![image](https://github.com/user-attachments/assets/04e0ff30-53f9-4866-9d65-d8bffaad4109)

Entonces lo que hacemos es iniciar un servidor con python 3 para poder obtener ese archivo desde mi máquina principal.

![image](https://github.com/user-attachments/assets/d906979f-5abb-42a9-b6a0-339ad98d349d)

Desde mi maquina principal lo cojo.

![image](https://github.com/user-attachments/assets/f4ef1865-98ee-483b-a2ce-d1218e2e00c8)

Usamos zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/66d59cdd-d1c3-4aec-bafa-f9d0493de425)

Y ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/394a16dd-5777-4742-bafb-39779ea3323f)

Hacemos un unzip del archivo, ponemos la contraseña que hemos conseguido y abrimos el archivo password.txt

![image](https://github.com/user-attachments/assets/5969d658-7871-439f-a016-b31cebc1f16b)

Entramos como pronike, ya que sabemos su contraseña.

![image](https://github.com/user-attachments/assets/c8b08076-0a45-4e8b-9825-1bcea4ff7c79)

Haciendo un sudo -l vemos que tenemos permisos sudo en apt.

![image](https://github.com/user-attachments/assets/11d4b52b-530e-4985-bbc9-50149f54b2f3)

Abrimos el GTFObins, y en apartado de apt seguimos los pasos que nos dicen.

![image](https://github.com/user-attachments/assets/5200afcf-bc85-4d9f-9e88-f771f2d440f3)

Después de sudo añadimos -u proadidas, porque es en lo que queremos convertirnos.

![image](https://github.com/user-attachments/assets/85af6dca-0aa2-418d-829d-6b54a00d53f4)

Volvemos a hacer sudo -l y nos vuelve a aparecer lo mismo, pero esta vez nos sale la opcion de root, pero con aws.

![image](https://github.com/user-attachments/assets/38ceffac-0486-45e9-baaf-060c56abea18)

![image](https://github.com/user-attachments/assets/5a911314-9bfc-4b51-8198-fb977ec912a9)

Entramos en el usuario proadidas, y encontramnos la primera flag que está en el archivo user.txt

![image](https://github.com/user-attachments/assets/86a7401e-7994-4bee-9261-c833f5b9a429)

Y para encontrar la flag del root, iremos al directorio root que esta en home y abriremos el archivo root.txt

![image](https://github.com/user-attachments/assets/4a4b163c-00cc-40cf-968a-071acbd097ad)


















