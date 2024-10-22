# RESOLUCIÓN DE LA MÁQUINA GRILLO

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/1e4d8357-defe-4a09-8cb7-35c740c178b4)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/6d24d749-84e0-4623-9116-90bf33a124fc)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/8a437bd5-8445-4aa0-9250-84a8d16b358c)

Ponemos la IP en el navegador y nos encontramos con el servicio de apache, pero al revisar el código fuente nos encontramos con esto.

![image](https://github.com/user-attachments/assets/b9f4be1a-c364-4868-b06c-4363a3d01115)

Hacemos hydra con el usuario melanie por el servicio ssh.

![image](https://github.com/user-attachments/assets/cc6bae2f-ab11-438a-84f0-8e344b9a955c)

Sabiendo el usuario: melanie y la contraseña: trustno1, entraremos por el servicio ssh.

![image](https://github.com/user-attachments/assets/d7941606-e764-4ec8-a9de-c0ac6f215081)

Y haciendo un simple ls a la ruta principal nos encontramos con la flag del usuario.

![image](https://github.com/user-attachments/assets/99a39b44-96c4-499b-9235-9745baedf2f5)

Desde el mismo directorio hacemos sudo -l para ver si hay algo para explotar.

![image](https://github.com/user-attachments/assets/9fba5f16-2f9c-4245-9f7f-735d8dcf2410)

Viendo esto, lo primero que hacemos es crear una clave SSH utilizando puttygen, una herramienta diseñada para gestionar claves SSH en diferentes formatos.
Esto genera una nueva clave privada RSA, que se almacena en el archivo id_rsa.

![image](https://github.com/user-attachments/assets/12daa8fa-2ddf-4091-925b-f360214005c1)

Con la clave privada generada, el siguiente paso es crear la clave pública correspondiente y agregarla al archivo authorized_keys del usuario root. Esto permitirá el acceso SSH sin necesidad de contraseña desde la cuenta de Melanie

![image](https://github.com/user-attachments/assets/602e6a94-9af2-4bb4-b212-134c45f11ebd)

Y por ultimo, antes de conectarnos por el servicio ssh al usuario root, modificamos los permisos de la clave privada para garantizar que solo el usuario tenga acceso de lectura.

![image](https://github.com/user-attachments/assets/d874928f-c162-4382-9d4a-e8d759c713b2)

Ejecutamos el servicio ssh para poder entrar como root, y al hacer ls vemos la flag correspondiente.

![image](https://github.com/user-attachments/assets/9d360bdd-6297-4456-9070-2c1a1f983332)




