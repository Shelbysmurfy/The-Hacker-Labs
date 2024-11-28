# RESOLUCIÓN DE LA MÁQUINA SAL Y AZÚCAR

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/bf7d5bf4-3d63-4bfa-a94b-a636b3939d2b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/e9dc1bd9-b550-4a9f-ae94-68c5b6bed853)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/e2c711b8-a76a-4e32-9596-40236ddea91b)

Abro el puerto 80 y veo un panel de apache por defecto, assí que lo que hacemos es hacer fuzzing.

![image](https://github.com/user-attachments/assets/ca9463fe-c0bb-4fe7-9dab-53d29a45afd7)

En el nos encontramos un directorio summary, y dentro de el un archivo html.

![image](https://github.com/user-attachments/assets/cadf7fda-6e47-4012-9590-e2a5bf9e6179)

![image](https://github.com/user-attachments/assets/467c3f26-b00f-485b-baf5-8a2644b69b43)

No tenemos ni usuarios ni contraseñas, así que haremos hydra atacando al servicio ssh, buscando por una lista de usuarios y contraseñas.

![image](https://github.com/user-attachments/assets/da0c2935-8a23-49c6-a9f8-8637e55f627a)

Sabiendo el usuario y la contraseña. entraremos con el servicio ssh.

![image](https://github.com/user-attachments/assets/a3dab97e-e3a0-418a-9676-c7bf0068122a)

Y si vamos al usuario info y hacemos ls, ya tenemos la flag del usuario.

![image](https://github.com/user-attachments/assets/78bca9d1-111e-478c-b7a9-47c77adc961b)

Si hacemos sudo -l vemos esto: 

![image](https://github.com/user-attachments/assets/64a3d03f-dd73-425e-a5eb-2ce29b39d775)

Ejecutamos estos dos comandos para poder ver la flag del usuario root, y seguidamente decodearla con base64.

![image](https://github.com/user-attachments/assets/a994aa8d-a0c8-45ca-be87-a8403b4b686b)











