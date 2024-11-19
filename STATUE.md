# RESOLUCIÓN DE LA MÁQUINA STATUE

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/692a5c13-3748-43ef-8c24-2727ebcf77f8)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/20aff697-ec84-4a16-bed6-f1a9bb7377c6)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/e7d40305-9475-488d-a8cf-35aa9a0397bc)

Abrimos el puerto 80 y no hay nada.

![image](https://github.com/user-attachments/assets/4a94de49-52a7-4877-8b8e-ccc0dd06b7fb)

Nos vamos al /etc/hosts y añadimos la IP de la máquina víctima junto a "statue.thl", que es su nombre.

![image](https://github.com/user-attachments/assets/232a2caf-f415-4de8-bfca-2a3d668d7d1f)

Abrimos la web con esta nueva dirección.

![image](https://github.com/user-attachments/assets/71976eb0-25cb-4f12-8629-fa338bdec1ef)

Hacemos fuerza bruta con gobuster con la dirección de la máquina, el diccionario para buscar directorios o archivos y el de extensiones.

![image](https://github.com/user-attachments/assets/15e9e447-816c-4f8c-b0c2-ac62a79e3bbe)
![image](https://github.com/user-attachments/assets/964777aa-b323-444b-907b-64f1e470a697)

Encontramos el archivo README.md, que contiene un código en base64.

![image](https://github.com/user-attachments/assets/f194ee9b-1dde-40fe-9fc3-d656446534e6)

Lo decodeamos con ciberchef.

![image](https://github.com/user-attachments/assets/03ee62d8-4598-4517-9160-35bd2c5d1183)

Usamos la credencial que nos ha dado para ver si podemos loguearnos desde el login.php

![image](https://github.com/user-attachments/assets/35ec1ae4-232a-4406-8760-f1bf36fe7bbf)

![image](https://github.com/user-attachments/assets/bd7aeeac-3336-4442-a150-386e2b2efab5)

Dentro encontramos un sitio donde podemos subir archivos.

![image](https://github.com/user-attachments/assets/28c73b4b-ca7a-41f7-8617-1ef53df7aced)

Antes hemos buscado la versión que nos salia en el login del pluck, la 4.7.18, esta es vulnerable a la subida de archivos zip con un php dentro.

![image](https://github.com/user-attachments/assets/d842ce4b-e300-4a65-9e10-7c0de05fd8ec)

![image](https://github.com/user-attachments/assets/404d0cc8-aa40-46ca-9c3a-51d4cebfdf8b)

Una vez creado correctamente, vamos a subirlo.

![image](https://github.com/user-attachments/assets/4dffccf8-3191-476e-b447-774a57a91a4e)

En el github que nos explica el proceso, nos dice donde va el archivo cuando lo subimos.

![image](https://github.com/user-attachments/assets/f5150079-2fe4-4988-a673-3233af76743d)

Vamos al /data/modules, y ya tenemos el archivo subido.

![image](https://github.com/user-attachments/assets/90453df4-4317-4da7-b20e-bf19fc85508d)

Lo abrimos y ya podemos ejecutar codigo.

![image](https://github.com/user-attachments/assets/d2daab22-70f6-4d2c-beda-a53b4d352256)

Vamos a hacer una reverse shell.

![image](https://github.com/user-attachments/assets/9eaa9b74-55db-4f91-94bb-6ff19834c8e2)

Encontramos dos usuarios.

![image](https://github.com/user-attachments/assets/9d3d8419-8183-4b17-b1d3-005d62fd32eb)

Encontramos una clave, que parece ser la del usuaerio Charles, pero esta encodeada en base64.

![image](https://github.com/user-attachments/assets/1566706e-1e2b-479a-a2c1-418fe4867af8)

La Key la decodeamos con ciberchef.

![image](https://github.com/user-attachments/assets/88ef25cc-a95c-47ce-9762-186031f1d5ee)

Buscamos información sobre Charles Wheatstone, ya que parace ser el nombre de alguien.

![image](https://github.com/user-attachments/assets/ee42d6d1-84e5-4114-80d4-f1943d12a74c)

Vemos que fué el creador de una técnica de encriptación llamada Playfair.

Usamos las credenciales que hemos obtenido, tanto la Pass como lo que hemos decodeado anteriormente.

![image](https://github.com/user-attachments/assets/e6d3788d-5dbf-490a-badd-12985b5f96b5)

Nos conectamos como usuario charles con la contraseña "incomprensible".

![image](https://github.com/user-attachments/assets/f9f051f8-1329-4044-ac33-274cb3274e1c)

Vemos un archivo llamado binario.

![image](https://github.com/user-attachments/assets/878e2e43-d332-4904-a3ca-5159ae6c5cb9)

Si hacemos uso del parámetro strings nos muestra cadenas legibles.

![image](https://github.com/user-attachments/assets/36d1da92-2207-431a-a5ab-42a8637fb2ea)

En el vemos el usuario juan seguido de la palabra generador.

Si nos intentamos loguear con estas credenciales obtenemos acceso como el usuario juan.

![image](https://github.com/user-attachments/assets/881c2bf0-d127-4223-a9ad-c81a472e6c71)

Si hacemos ls obtenemos la primera flag, la de usuario.

![image](https://github.com/user-attachments/assets/62e7b856-8851-4130-aee2-acbdeaa0c18a)

Buscamos permisos SUID y capabilities y encontramos python3.12

![image](https://github.com/user-attachments/assets/95ab1a1a-b3ee-4cff-82c5-c8ceddfb4a05)

Vamos al GTFObins y seguimos los pasos que nos dice el apartado de SUID.

![image](https://github.com/user-attachments/assets/0f7b693c-4bcb-4d29-b7cd-7e4e4a09c496)

Conseguimos acceso como usuario root.

![image](https://github.com/user-attachments/assets/49eac941-833b-4a06-8f21-25cb64bd10fc)










