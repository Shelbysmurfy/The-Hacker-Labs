# RESOLUCIÓN DE LA MÁQUINA MICROCHOFT

Abrimos la máquina víctima y seguidamente en la nuestra ejecutamos un arp-scan para saber su IP.

![image](https://github.com/user-attachments/assets/f04e8703-66cb-45ce-abe9-9f44fc05e688)

Nos salen todas estas IP's y como nuestra máquina víctima es un windows haremos pings hasta que veamos que en una de ellas sale que el ttl = 128

![image](https://github.com/user-attachments/assets/b4feda52-9b62-49d4-a62b-b183bd0d82ef)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/c4d6cb33-a265-4aad-bfea-87b3177a97fc)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...
Los puertos que estan abiertos pero no tienen un servicio especificado de momento no los miraremos.

![image](https://github.com/user-attachments/assets/4957abd5-75ef-4687-af59-4998d8a858ad)

Como podemos ver en los resultados del comando que hemos ejecutado, en el puerto 455/tcp, el sistema operativo es Windows 7 Home Basic Service Pack 1 y está configurado en el grupo de trabajo WORKGROUP. Este sistema, con el puerto 445 abierto, es particularmente preocupante ya que es vulnerable a la famosa vulnerabilidad EternalBlue.

Además este puerto es utilizado para compartir archivos y otros recursos en redes Windows mediante el protocolo SMB (Server Message Block).

EternalBlue, que afecta versiones de Windows no actualizadas, explota una vulnerabilidad crítica en el protocolo SMBv1, lo que podría permitir la ejecución remota de código y, en consecuencia, el control completo del sistema afectado.

Aún así ahora ejecutaremos este comando para estar seguros de que es vulnerable.

![image](https://github.com/user-attachments/assets/c695e973-c9f1-470e-9a77-fb348ef5fa72)

Como podemos ver si es vulnerable, y por tanto ahora lo que haremos será explotarla a través de la herramienta metasploit.

![image](https://github.com/user-attachments/assets/68f51127-b274-4d8f-8adf-057858428e7c)

![image](https://github.com/user-attachments/assets/241bad09-a1e5-4971-bbfe-d188c6673e56)

Viendo esto lo que haremos será targetear el segundo, ya que es donde tenemos el Windows 7 de máquina víctima, que es lo que buscamos.

![image](https://github.com/user-attachments/assets/4755320c-99c0-4119-9fe9-6977691b4a64)

Y una vez dentro lo que hacemos es configurar los los parámetros necesarios para que pueda saber cual es la máquina víctima (RHOSTS), y la mia (LHOST)

![image](https://github.com/user-attachments/assets/5da2d5e5-055b-4be3-81d2-8dfe3b209db6)

Una vez configurados los parámetros ejecutamos el exploit.

![image](https://github.com/user-attachments/assets/9f5cc1ee-9604-42cb-9ed5-9e6fec9fd4ba)

Vamos al directorio raiz y hacemos ls.

![image](https://github.com/user-attachments/assets/f2332466-7af2-4b0b-ba79-bbfb0077dc6d)

Vemos el directorio Users, nos metemos.

![image](https://github.com/user-attachments/assets/26f71058-e849-4fa9-bde0-1a42566901ce)

Dentro de este directorio encontramos el usuario Admin y Lola, que es donde encontraremos las flags que buscamos.







