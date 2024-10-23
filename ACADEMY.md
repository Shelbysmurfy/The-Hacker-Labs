# RESOLUCIÓN DE LA MÁQUINA ACADEMY

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/3faf3451-79d9-432e-b180-0c104fd85928)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/12a3e17b-52bc-400a-a164-ce61a94023a5)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/777576c3-89a6-49bc-9c57-677a051061ef)

Entramos en la web (puerto 80 abierto) y no vemos nada, hacemos dirsearch para ver que nos econtramos.

![image](https://github.com/user-attachments/assets/0c176d6b-f70d-4d49-9a88-31eb0c22e5b6)

Abrimos el wordpress y nos aparece todo un poco mal, pero cuando seleccionamos cualquier cosa, abajo a la derecha nos pone conectando a academy.thl, pero cuando ponemos esto en vez de la IP, no carga, para que esto funcione hacemos lo siguiente.

Añadimos una linia con la IP de la máquina víctima junto con el academy.thl, esto lo hacemos en el /etc/hosts.

![image](https://github.com/user-attachments/assets/cfefd306-b2eb-4981-8f68-512b81d2fde6)

Ahora ya tenemos la web de wordpress cargando perfectamente.

![image](https://github.com/user-attachments/assets/6b05c547-71d8-4020-bac1-e7d9f9420623)

Y también su login

![image](https://github.com/user-attachments/assets/05bb7bb0-51c9-4f9a-9a07-e3415189810f)

Como no encontramos nada, utilizaremos wpsan para obtener información sobre la instalación de wordpress, versión, pluggins, temas instalados...

Encontramos el usuario dylan.

![image](https://github.com/user-attachments/assets/b3487d28-c057-4b03-877d-a4591793e96d)

Hacemos wpscan, para buscar la contraseña de este usuario.

![image](https://github.com/user-attachments/assets/6c3a0595-8430-48c0-9297-a285fac49f17)
![image](https://github.com/user-attachments/assets/3d306465-cd84-4db3-aea2-b850db312861)

Una vez la tenemos nos logueamos en el login de wordpress.

![image](https://github.com/user-attachments/assets/24f836e3-f546-4948-a5d5-7c60852cc003)

Una vez dentro vemos que en el plugin Bit File Manager podemos subir archivos, así que creamos un archivo malicioso llamado shell.php y lo subimos.

![image](https://github.com/user-attachments/assets/01c02df7-5f98-4632-92fb-f72b46f98223)

![image](https://github.com/user-attachments/assets/b4d89a6f-cc13-4097-8f74-31bfda6d48a4)

Una vez creado y subido podemos buscar la ruta donde se encuentra el archivo en nuestra barra de búsqueda y podremos ver que si añadimos el parámetro cmd ya podemos inyectar código.

![image](https://github.com/user-attachments/assets/b668b69f-bad3-411f-9faf-3928bd44d3ff)

Hacemos una reverse shell.

![image](https://github.com/user-attachments/assets/1374d116-a3fb-4ed1-b831-3f56501d88ba)
![image](https://github.com/user-attachments/assets/ed9cdfd4-bb3f-4f9f-a771-479a9b7dc2ea)
![image](https://github.com/user-attachments/assets/170fb72b-944f-44bd-83c5-ab75cda776a4)

Y obtenemos acceso.

![image](https://github.com/user-attachments/assets/b24f742a-0111-4c09-8424-f75b51cdede9)

Hacemos el tratamiento de la TTY como siempre.
Link: https://invertebr4do.github.io/tratamiento-de-tty/#

Con pspy64 vemos que hay una tarea cron ejecutándose en el directorio /opt de un archivo .sh

![image](https://github.com/user-attachments/assets/a4bedbde-a725-466b-8f40-74adf87d0195)

Para usar el pspy hay que ejecurtar lo siguiente:

Ejecutar este comando en mi máquina, en el directorio donde se guardó el archivo pspy64

![image](https://github.com/user-attachments/assets/af3027d6-7261-49fe-b7ec-bfe8278599a5)

Ejecutar el siguiente comando en la maquina victima, este lo ejecutaré desde el directorio /tmp

![image](https://github.com/user-attachments/assets/d3bef147-aa2f-48e3-a89f-e2f237bbc7a0)

En el directorio opt crearemos un archivo llamado backup.sh, lo creamos así porque con nano nos da problemas.

![image](https://github.com/user-attachments/assets/ae52fa5e-a91e-4a85-8f2f-834541fa5d45)

A este archivo le damos privilegios.

![image](https://github.com/user-attachments/assets/d3d08734-4afd-4986-b6d3-174c29e349d5)

Y si ejecutamos lo siguiente ya somos root.

![image](https://github.com/user-attachments/assets/599a666c-7b7d-46bb-9712-beeb212f846e)




























