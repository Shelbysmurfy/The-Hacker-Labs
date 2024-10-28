# RESOLUCIÓN DE LA MÁQUINA PIZZAHOT

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/9a99c23b-f0bb-4759-98c8-48ee9ad1308b)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/8010bf5d-fff2-4adb-8318-ac60c9443a43)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/4bca728b-ea61-4651-afdc-23c72e6aa5de)

Puerto 80, abrimos la página web.

![image](https://github.com/user-attachments/assets/9b83a45a-4f66-4f99-8001-59f408439344)

Abrimos el código fuente de la web y nos encontramos esto: 

![image](https://github.com/user-attachments/assets/8866bebb-e453-4c5c-a429-2f7493ac2555)

Hacemos un hydra para saber la contraseña.

![image](https://github.com/user-attachments/assets/cc11ff49-4710-4f3f-a6f8-003bc738d1a2)

Entramos desde el login de la máquina con las credenciales obtenidas.

![image](https://github.com/user-attachments/assets/897681d1-1a8a-4822-9bf3-f602b8028ba3)

Encontramos otro usuario: pizzasinpiña , en el cual encontramos la primera flag, la de usuario.

![image](https://github.com/user-attachments/assets/8f0d7c3e-2256-42ca-aaec-e83748237419)

Desde este usuario hacemos sudo -l y vemos esto: 

![image](https://github.com/user-attachments/assets/0ac42011-3032-4770-a423-6f3b4d8b37d4)

Vamos al GTFObins y ponemos lo que nos dicen.

![image](https://github.com/user-attachments/assets/f3f49158-9540-4e36-b5f5-dc14ba6c9ad0)

Y ya somos root.

![image](https://github.com/user-attachments/assets/83fb9128-e984-4c27-95f3-2efd32fee663)

