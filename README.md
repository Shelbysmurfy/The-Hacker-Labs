# RESOLUCIÓN DE LA MÁQUINA MORTADELA

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/660d950b-f2a1-4158-8757-eb8fee92cf3c)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/ec55f765-1bd5-4724-a8cb-01b3b688b703)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/ed271fb1-5e4c-43cb-a91f-8f86d225d389)

Abrimos la máquina y como no vemos nada importante hacemos fuzzing, y encontramos el payload wordpress.

![image](https://github.com/user-attachments/assets/5179f8c9-3174-445a-aa74-83b6d61bca3a)

Lo ponemos en la url y vemos esto.

![image](https://github.com/user-attachments/assets/6130b60d-d3c3-42f1-82c0-f33573ff3f46)

Vemos que en esta máquina esta funcionando el php por detrás, hacemos gobuster con busqueda para php.

Nos salen diferentes urls, entre ellas la de wp-admin, pero ninguna de ellas tiene información relevante.

![image](https://github.com/user-attachments/assets/973502f5-3009-4beb-924e-1dee57f30fba)

Como no encontramos nada, utilizaremos wpsan para obtener información sobre la instalación de wordpress, versión, pluggins, temas instalados...

![image](https://github.com/user-attachments/assets/32c73451-8b18-41d2-ae48-d2e8a0a528a0)

Encontramos el usuario mortadela

![image](https://github.com/user-attachments/assets/1a6029ed-b50c-4ec1-be78-f6259510b2d5)

Hacemos wpscan y hydra para este usuario y no encontramos nada.

También probamos de hacer hydra para el usuario root, por si existe, por mysql. Y este si nos devuelve una contraseña.

![image](https://github.com/user-attachments/assets/a6cefdd8-e295-49ce-b71a-aa6e188a9087)

Entramos por mysql con este comando, añadimos el --skip_ssl al final porque nos salia un error.

![image](https://github.com/user-attachments/assets/538abde3-9baf-4e8c-9ea8-64953ae4cfc7)

A partir de esto nos podemos mover por las bases de datos que encontremos y así poder encontrar información confidencial sobre usuarios, contraseñas...

Encontramos de nuevo el usuario: mortadela con su contraseña: Juanikokukunero8

![image](https://github.com/user-attachments/assets/1bd23591-ae1f-4e01-968c-cab7f818d530)

Entramos con el servicio ssh con los datos encontrados.

![image](https://github.com/user-attachments/assets/566d7003-e170-438b-92a0-9337ca808518)

Hacemos ls y encontramos la flag del user, que se encuentra en el archivo user.txt

Nos vemos al directorio principal, es decir hacemos cd .. para ir para atras varias veces.

![image](https://github.com/user-attachments/assets/81e61e9e-dbeb-4689-a950-c2aa10f7a7ec)

Al ver esto entramos en varios directorios, y en el /opt encontramos un archivo .zip que no podemos abrir.

![image](https://github.com/user-attachments/assets/ac0ed3b0-65a3-4f73-98cb-a6818d92df34)

Entonces lo que hacemos es iniciar un servidor con python 3 para poder obtener ese archivo desde mi máquina principal.

![image](https://github.com/user-attachments/assets/f232ff33-44bb-4b3b-91fe-f6ea9ece1900)

Desde mi maquina principal lo cojo.

![image](https://github.com/user-attachments/assets/97ded6d6-aca2-4ada-88e2-03b122419c9e)

Usamos zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/226782d0-aa19-45c7-a6b2-0d2cdd668c54)

Y ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/df6435ae-e224-44c4-8611-e1f4f514ac42)

Una vez hecho esto, hacemos un unzip del archivo pero esta vez sabiendo la contraseña, esto nos devuelve dos archivos, uno de ellos el archivo KeePass.

Definición: KeePass Password Safe es un gestor de contraseñas que permite proteger las distintas contraseñas de forma segura.​

![image](https://github.com/user-attachments/assets/af23648a-a12a-4800-bc5b-dc80e2440050)

Usaremos un exploit para saber que contraseña esta utilizando para la base de datos. 

Para ello usamos un repositirio de github que nos clonaremos a nuestro equipo.

![image](https://github.com/user-attachments/assets/742dfb1a-63d9-4251-9c23-951fa79a84ec)

En la contraseña podemos ver que la primera letra no la sabemos pero lo que tiene mas lógica es que sea una "M".

![image](https://github.com/user-attachments/assets/b82294ad-804f-4f06-a05e-a248220aca66)

Sabiendo la contraseña inicializaremos el keepassxc desde nuestra consola.

![image](https://github.com/user-attachments/assets/860d53d9-44f0-4b99-9484-da2742d034c1)

De esta manera podemos entrar y nos encontramos con la contraseña del usuario root.

![image](https://github.com/user-attachments/assets/e475ce53-e32d-4ae4-a620-6f5278f5ab36)

Entramos con el servicio de ssh como usuario root y encontramos su flag.

![image](https://github.com/user-attachments/assets/8ccbe533-a9a0-42b6-8778-8b3c42f24728)





































