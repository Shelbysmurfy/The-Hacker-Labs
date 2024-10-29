# RESOLUCIÓN DE LA MÁQUINA JAULACON

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/f21f72f2-fadc-4608-9d9f-e94ee7005286)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/cfc81bfa-c701-4771-b8a2-cbd17ba5d1c0)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/63e9c121-499f-4586-8dce-6a657378f255)

Puerto 80, abrimos la página web.

![image](https://github.com/user-attachments/assets/9fad252d-fdd6-4542-89fc-eb6c2010cf02)

Haciendo gobuster vemos el directorio /cgi-bin/, este es un directorio que, al verlo, puede ser factible testear un ShellShock. 

![image](https://github.com/user-attachments/assets/2d5490e3-4b63-4346-b6b6-b023ef11859f)

Al verlo ejecutamos otro gobuster pero añadiendo el /cgi-bin/ y filtrando por (pl, sh y cgi), en este nuevo comando tendremos que añadir el diccionario lowercase-2.3-big.txt, con el diccionario que estabamos usando antes no encontraremos nada.

![image](https://github.com/user-attachments/assets/349dbdf1-edc5-436a-b9b6-cbe767bfb3ef)

Al abrir el archivo vemos que tenemos conexión. Así que vamos a realizar un ataque Shellshock.

![image](https://github.com/user-attachments/assets/c3c811b9-6f37-47aa-864f-df385778de80)

Para ello buscamos en internet como se hace este ataque.

Y es que se envia un curl a la url vulnerable, en el que al User-Agent, le ponen lo que podéis ver en la imagen, que es básicamente una llamada recursiva que se llama a sí misma múltiples veces, y que puede llegar a colapsar el sistema.

![image](https://github.com/user-attachments/assets/25c684fb-97f4-4934-9a19-a16b96bfd366)

![image](https://github.com/user-attachments/assets/7bb94dbf-ab0f-40ed-984f-40f5bfb16123)

Vamos a ejecutar un comando para ganara acceso a la máquina, para eso tenemos de ponernos en escucha a la vez con netcat.

![image](https://github.com/user-attachments/assets/6ce40c8f-df11-4292-9ca4-cf506b523457)

Vamos al directorio opt y ejecutamos el comando ls -la y vemos unas credenciales.

![image](https://github.com/user-attachments/assets/c2c82df1-950e-4e27-aeea-11bb11e55b6d)

Las introcimos en el login que teníamos en el puerto 3333, y accedemos.

![image](https://github.com/user-attachments/assets/5c4a796b-fe66-4fbf-b355-ed063e0eabe0)

Una vez dentro si le damos a download nos devuelve que no somos admin.

![image](https://github.com/user-attachments/assets/492a917b-43a1-4227-8531-0e9f1753093b)

Llevo intentando cosas varias horas pero no se como hacerlo para que no me muestre que no soy admin.

![image](https://github.com/user-attachments/assets/3c7e5928-684e-42ad-b3b3-13979fd78b0a)
![image](https://github.com/user-attachments/assets/6ac528d5-0e67-40e2-a8e2-31bf83eeb3b3)











