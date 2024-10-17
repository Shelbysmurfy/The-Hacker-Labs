# RESOLUCIÓN DE LA MÁQUINA FRUITS

Abrimos la máquina y nos dan la ip, junto a un login

![image](https://github.com/user-attachments/assets/b9e6bde9-d6bd-4fe3-a2d3-bae099071c91)

Escaneo para todos los puertos

![image](https://github.com/user-attachments/assets/a5cac044-60d3-448e-a4bd-6c810a24728a)

-p- : Escaneo de todos los puertos. (65535)

-sS : Realiza un TCP SYN Scan para escanear de manera rápida que puertos están abiertos.

-sC : Realiza una escaneo con los scripts basicos de reconocimiento

-sV : Realiza un escaneo en buqueda de los servicios

–min-rate 5000: Especificamos que el escaneo de puertos no vaya más lento que 5000 paquetes por segundo, el parámetro anterior y este hacen que el escaneo se demore menos.

-n: No realiza resolución de DNS, evitamos que el escaneo dure más tiempo del necesario.

-Pn: Deshabilitamos el descubrimiento de host mediante ping.

Ponemos la ip en el buscador y nos encontramso con esto

![image](https://github.com/user-attachments/assets/0867f8d6-0543-4e8d-a005-21d317fef9ae)

Al introducir cualquier dato nunca nos devuelve nada, solo nos sale esto en la barra de búsqueda

![image](https://github.com/user-attachments/assets/5f8074bb-17bf-4bea-bff9-1520c946b115)

Esto me hace pensar que deberíamos hacer un reconocimiento para ver si encontramos mas directorios. Al ver que la web tiene php, vamos a fuzzear por extensiones que contengan php.

![image](https://github.com/user-attachments/assets/90411e2e-cc38-4abd-af0b-18438185ab76)

Pero nos encontramos con una pagina en blanco, vamos a ver si podemos encontrar algún tipo de vulnerabilidad entorno a Local FIle Inclusion, para ello vamos a fuzzear en búsqueda de códigos de estado 200 que apunten al archivo /etc/passwd.

![image](https://github.com/user-attachments/assets/c53054b8-2f5d-45d8-b3c0-7a31aa5b9208)

Hacemos fuerza bruta con hydra para sacar la contraseña del usuario que hemos encontrado.

![image](https://github.com/user-attachments/assets/47fb8c59-2ca3-43e8-b1bb-2c57dba1fd6a)

Lo ejecutamos con ssh.

![image](https://github.com/user-attachments/assets/cddbdc27-5846-428a-8538-ff3670e89a92)

Si hacemos ls encontramo la primero flag, que esta en user.txt

Seguidamente vemos que al hacer sudo-l nos sale esto.

![image](https://github.com/user-attachments/assets/040d2fd0-4f92-465e-8c38-8039db00e9e2)

Si buscamos el binario find en gtfobins encontramos como escalar los privilegios, para poder ser root.

![image](https://github.com/user-attachments/assets/1b294ede-5fe4-4899-a6b8-e14403118992)

Y ya está, somos root, hacemos ls y podemos ver la flag del usuario root.

![image](https://github.com/user-attachments/assets/852ad36d-e415-4da1-b9e2-4886ff714ac3)
