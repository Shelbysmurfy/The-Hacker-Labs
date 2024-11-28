# RESOLUCIÓN DE LA MÁQUINA AVENGERS

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/ae8909c7-855f-4ec5-ae67-92d878ff3f61)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/c36f2411-1913-4aa6-8432-515293b0d2a4)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/fd818f2e-a5c4-489f-a453-ea61c139b428)
![image](https://github.com/user-attachments/assets/a05fac87-2ad3-4e77-b92f-ab725edfd92e)

Vemos que el servicio ftp tiene activo el usuario anonymous, dentro de este encontramos un .zip, que no podemos descomprimir.

![image](https://github.com/user-attachments/assets/99faeb72-bfb2-4a28-9a37-8780c001b612)

En el servicio http, vemos que tenemos el robots activo.

![image](https://github.com/user-attachments/assets/42e7520c-6851-436f-aea5-ca0297ebdd88)

En el directorio de mysql encontramos una contraseña en base64.

![image](https://github.com/user-attachments/assets/5b21f71f-1ae8-4bd6-8c3d-1d98934bdd46)

La decodeamos varias veces y obtenemos la contraseña.

![image](https://github.com/user-attachments/assets/33f30bdf-6098-4577-a2ef-496ffd38d81f)

Y entrando en el directorio de webs, hay el directorio secret.html que te permite buscar información, donde introducimos la contraseña encontrada y nos muestra el usuario correspondiente.

![image](https://github.com/user-attachments/assets/fc9717d7-6d03-4499-b1f7-a4f297f4e6f5)

Vamos a entrar al servicio ssh con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/f6caccec-8f9c-48a0-b0f6-ddef5a327d20)

Encontramos la manera de poder decodear el zip que hemos encontrado antes en el servicio ftp.

![image](https://github.com/user-attachments/assets/5d9afb01-0908-4108-a704-9e371662edae)

Así que hacemos un unzip de el archivo que queremos descomprimir y ponemos la credencial "shit_how_they_did_know_this_password". 

![image](https://github.com/user-attachments/assets/d9f984cf-b82c-4c1c-b4c9-baac8b6afa3b)

Abrimos el archivo txt.

![image](https://github.com/user-attachments/assets/5c2369d3-7cc3-4063-9329-74c4a9cadffc)

Usamos mp64 para que nos muestre todas las combinaciones posibles para los 4 carácteres después de fuerzabruta.

![image](https://github.com/user-attachments/assets/ac8d3d4e-07b4-43da-bb50-b391e5d066e6)

Una vez guardado en un archivo.txt, haremos un hydra con el usuario hulk y como contraseña el diccionario passwordsHulk.txt

![image](https://github.com/user-attachments/assets/5d296e7f-ffa6-41e3-90f7-e6563cb4a662)

Ahora entraremos al servicio mysql con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/637b0d33-ded3-4d7b-a315-21eb1e4cda4b)

Encontramos una lista de usuarios.

![image](https://github.com/user-attachments/assets/665fa161-58bb-42f5-b7be-df48d54804f2)
![image](https://github.com/user-attachments/assets/a0a98095-be36-4fd4-91dc-1624b6406117)

Entramos con el usuario stif.

![image](https://github.com/user-attachments/assets/4aea9aa9-e4d2-4c85-af22-3b6fad8614a0)

Al hacer sudo -l nos muestra lo siguiente: 

![image](https://github.com/user-attachments/assets/ff5f920f-39a7-4ff1-aaf3-451d42bb8dc6)

Así que hacemos un sudo bash y ganamos acceso como root.

![image](https://github.com/user-attachments/assets/95731ed8-926d-4d55-97fe-c0251e5755cd)
















