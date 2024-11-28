# RESOLUCIÓN DE LA MÁQUNA FINDME

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/da942aca-30ef-48ac-b62f-9ded339559d0)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/e6b64dc1-8cfa-4ae1-8547-f014b862a9b3)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/e9439e81-d609-43ea-84bf-127586146f70)
![image](https://github.com/user-attachments/assets/e2692eae-2442-485a-bb8c-145c5c867a95)
![image](https://github.com/user-attachments/assets/ee8e7b5f-1944-4f9f-88a4-caa61b4ebcaf)

Al principio hemos visto que en el servicio ftp podemos entrar a través del usuario anonymous.

![image](https://github.com/user-attachments/assets/5c63fdc8-d55f-4b5f-926f-54e79a160359)

Hacemos ls y vemos el archivo ayuda.txt, lo abrimos.

![image](https://github.com/user-attachments/assets/b8987773-c350-4bf4-8ac7-71f98768b9b1)

Sabiendo que el usuario es geralt, ahora buscaremos contraseñas que empiecen por p y acaben por a, que son las dos pistas que nos dan.

![image](https://github.com/user-attachments/assets/de3c5a67-3456-45be-b6d7-a9ba25986382)

Nos dan 5 opciones de contraseña para lo que hemos puesto, lo guardamos en un diccionario.

![image](https://github.com/user-attachments/assets/ca04488a-26e8-4d1e-8a6e-ee642e79d2f5)

Hacemos un hydra, poniendo como diccionario nuestro archivo txt, y haciendo un http-post-form con toda la información que podemos sacar del apartado de network dentro de la web.

![image](https://github.com/user-attachments/assets/5bc37175-638e-4e8d-aca1-8ff7d0f40c5d)

Sabiendo las credenciales las usamos en el login del jenkins.

![image](https://github.com/user-attachments/assets/7c60e898-996f-4480-b2df-44a46b01b6bb)

Vamos al apartado de script console, para hacer una reverse shell, esto lo sabemos gracias a hacktricks.

![image](https://github.com/user-attachments/assets/5e9fab82-e4f6-4736-a379-f0522b6ca9ad)

Hay una parte que esta encodeada en base64, la decodeamos para saber que es.

![image](https://github.com/user-attachments/assets/ea2c3986-d4ef-4dd1-8adc-5c3a603b6202)

Como es la reverse shell, vamos a la web y creamos nosotros una con nuestras credenciales, la ponemos en base64, y la cambiamos por la que había. 

![image](https://github.com/user-attachments/assets/3acc2af4-a184-406c-b9b8-f62bede4b4a0)

Nos ponemos en escucha con netcat, y conseguimos acceso.

![image](https://github.com/user-attachments/assets/db215ca6-31d5-4cb0-bcd1-cc03749fbbcc)

Listamos binarios que tengan el SUID activo, y los que no tengan permisos que se vayan al /dev/null

![image](https://github.com/user-attachments/assets/c4f76119-68c6-4ae2-af17-b6a0c09192d3)

Vemos uno de ellos, el php8.2, vamos a buscar en GTFObins información sobre el php, en el aprtado SUID.

![image](https://github.com/user-attachments/assets/e13fba8b-5ce9-4bea-8005-568ee71d6da9)

Nos dice que si ejecutamos eso podemos obtener acceso como root.

![image](https://github.com/user-attachments/assets/0ed492ed-3a2f-4c26-9194-cb627dff51a4)
![image](https://github.com/user-attachments/assets/d6be1c7b-ca00-46a2-9ccd-ccfeb22957d8)

Ya somos root.

![image](https://github.com/user-attachments/assets/68e85132-0525-4366-9102-3aa7250386f0)
















