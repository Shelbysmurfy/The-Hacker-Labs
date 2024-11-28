# RESOLUCIÓN DE LA MÁQUINA "CAN YOU HACK ME ?"

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/46d8fb97-e4f0-4590-946c-8576109c3d4a)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/7394616f-5156-4541-90ff-a84a1f4a3cfa)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/3de1bf75-7691-471e-bfa1-0e44a77344cb)

Entramos al puerto 80, para ello antes tendremos que añadir la ruta de la web en /etc/hosts.

![image](https://github.com/user-attachments/assets/a4c80b07-ec88-40b7-9fa2-5b9c05aa89bf)

Abrimos el código fuente y vemos un mensaje donde sale un posible usuario.

![image](https://github.com/user-attachments/assets/dda814f1-075c-4c7b-8256-1495088ab5f1)

Hacemos hydra para saber la contraseña de este usuario.

![image](https://github.com/user-attachments/assets/8a1fbdf3-f8db-4c1f-9003-cbca267b16f7)

Entramos al servicio ssh con las credenciales obtenidas. Al abrirlo te muestra la flag del user.

![image](https://github.com/user-attachments/assets/2b50e438-9a77-4681-bab9-1fcaca0ec6ab)

Hacemos id y vemos que el usuario juan pertenece al grupo docker.

![image](https://github.com/user-attachments/assets/cf1a1916-d61a-4b9a-a772-b343d8b5fa24)

Vamos a hacktricks y vemos esto: 

![image](https://github.com/user-attachments/assets/961f56bd-45ee-4e06-9de8-8007834a3fd8)

Seguimos los pasos que nos dice y conseguimos acceso como root.

![image](https://github.com/user-attachments/assets/40b6dd2a-7de8-4d41-99b1-6781e5f75d24)




