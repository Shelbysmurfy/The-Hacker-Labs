# RESOLUCIÓN DE LA MÁQUINA GOIKO

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/33ab61ae-f087-409a-bd19-081449a750f0)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/d8bfad0a-760f-48a2-9433-85ffacbfe00b)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3a37b680-e90e-4784-bbc7-17995bb22b4e)

Ahora sabiendo que estamos tratando con sistemas SMB, usaremos enum4linux para recopilar información sobre estos.

![image](https://github.com/user-attachments/assets/abb07eb1-7870-4da5-ad68-f27b15c7d367)

Nos encontramos tanto directorios como usuarios.

![image](https://github.com/user-attachments/assets/8b8343e6-539e-41d2-84b9-52c3ca74f152)

![image](https://github.com/user-attachments/assets/94ecca78-98d6-460f-af39-0e972c57c4c3)

Ahora con el uso del comando smbclient puedo ir probando todos los directorios para ver si puedo sacar información valiosa.

Si entramos en el directorio menú y en el archivo ".cafesinleche" nos encontramos con la siguiente información: 

![image](https://github.com/user-attachments/assets/bd6b2690-6e1b-4fa8-a2d8-0a96f59cf87e)

![image](https://github.com/user-attachments/assets/08e71892-71ef-4603-a56c-3219a918ec62)

Hacemos la conexión con el servico ssh y las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/a5c10492-14a2-4429-b250-79fb33c746a9)

En el directorio /opt/porno encontramos esto: 

![image](https://github.com/user-attachments/assets/09138993-d892-4aa5-9142-cc153dbf6424)

Volvemos al usuario marmai y en el directorio ftp nos encontramos un archivo .zip

![image](https://github.com/user-attachments/assets/cb685495-0006-498d-a3b8-dd1796af5845)

Nos lo pasaremos a nuestra máquina para poder ver que contiene.

![image](https://github.com/user-attachments/assets/d301361c-32f6-4521-b379-54b09864d052)
![image](https://github.com/user-attachments/assets/71ea9042-d1f1-4fd9-95d1-13bff986774b)

Ahora haremos un zip2john para poder extraer el hash.

![image](https://github.com/user-attachments/assets/809ce061-d4ca-4d42-856e-374a07dfe121)

Y ahora con john obtendremos la password del archivo.

![image](https://github.com/user-attachments/assets/6e855741-991a-4954-9dec-6dd0612aed29)

Una vez hecho esto, hacemos un unzip del archivo pero esta vez sabiendo la contraseña.

![image](https://github.com/user-attachments/assets/b0a5da28-501a-482a-9306-da48dbe4302a)

Nos devuelve dos archivos, el users: 

![image](https://github.com/user-attachments/assets/54e29116-d868-4ba8-a4b5-58a60a47a12c)

Y el id_rsa: 

![image](https://github.com/user-attachments/assets/bf2ef7d6-463d-4411-9b73-c67b9167d56a)

Hacemos un hash del archivo id_rsa.

![image](https://github.com/user-attachments/assets/f607899e-d438-4874-827e-90e66b7b3c2a)

Y con john obtenemos una contraseña de la cual no sabemos su usario, pero si sabemos cuales pueden ser.

![image](https://github.com/user-attachments/assets/7232eec9-8ed6-41d7-b589-3680067d3ab6)

En el archivo que teníamos de usuarios le ponemos todos los usuarios posibles que tenemos.

![image](https://github.com/user-attachments/assets/2bd94ce5-0c04-4061-b2ac-d086c5d71168)

Hacemos un hydra con el archivo de los usuarios y la contraseña: babygirl

![image](https://github.com/user-attachments/assets/5cb04e48-f55d-473a-a751-aef1ab5760c0)

Ahora entramos en el servicio ssh con las credenciales nuevas obtenidas.

![image](https://github.com/user-attachments/assets/a65c4c13-66fe-4ced-ad6e-939d7026e10b)

Haciendo ls -l encontramos la primera flag, la del user.

![image](https://github.com/user-attachments/assets/28418f3c-1511-47d0-b77b-5ccba4d24a6b)

También encontramos un archivo llamado nota que dice esto: 

![image](https://github.com/user-attachments/assets/2a60bc14-dd79-4bb3-96c1-5719c9c9533a)

Por tanto vamos a entrar en la base de datos. 

![image](https://github.com/user-attachments/assets/6afbc428-1de2-41b4-97e6-e5fe625c88fb)

Investigando un poco por dentro encontramos dos usuarios y dos hashes.

![image](https://github.com/user-attachments/assets/0970a525-a57b-4b08-9f7b-ee33ac1b1fdf)

Vamos a una web para crackear el hash y uno de ellos nos da resultado.

![image](https://github.com/user-attachments/assets/50a5f930-e3e7-4df2-bbfc-f6e86694a987)

Al querer entrar con el usuario Carline no me deja por tanto voy a probar con el nika.

![image](https://github.com/user-attachments/assets/fc1e3026-4da0-4afa-9c05-cca371f823f3)

Vamos al directorio /opt/porno y ejecutamos los siguientes comandos para ser root.

![image](https://github.com/user-attachments/assets/8cfe8552-fd7e-44f9-adab-ff75cc5013fe)
















