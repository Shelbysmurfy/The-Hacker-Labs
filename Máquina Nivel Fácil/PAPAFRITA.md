# RESOLUCIÓN DE LA MÁQUINA PAPAFRITA

Abrimos la máquina y vemos su IP junto al login.

![image](https://github.com/user-attachments/assets/14d5f759-89c2-4dd6-a897-9ef4fc272da8)

Hacemos un nmap para poder ver los puertos que estan abiertos para la IP seleccionada.

![image](https://github.com/user-attachments/assets/dbacb29f-2988-4520-9e82-4175d842b38d)

Ahora hacemos un escaneo de los puertos que hemos visto que estan abiertos para saber servicios,versiones...

![image](https://github.com/user-attachments/assets/7f51559b-f417-4788-83f1-9a8c0fa071ab)

Entro en el puerto 80 y de inicio no veo nada raro, pero al entrar al codigo fuente me encuentro con esto:

![image](https://github.com/user-attachments/assets/a24ee050-2968-4e1d-808b-0065911683c5)

Parece ser un Brainfuck, así que abrimos el conversor para saber que dice.

![image](https://github.com/user-attachments/assets/d3edb765-bedb-42d2-9f30-f2a490b765ad)

Haciendo un dirsearch para ver que directorios estan corriendo en esta web no encontramos nada.

![image](https://github.com/user-attachments/assets/1894562b-e386-467f-b47d-4324a9aa735c)

Después de probar varias combinaciones para poder entrar en el servicio ssh con lo que nos habían dado antes.

Hemos podido entrar poniendo de usuario: abuela y de contraseña: abuelacalientalasopa

![image](https://github.com/user-attachments/assets/5168d165-b2b2-4048-9ff7-1644aa56b9e8)

Hacemos sudo -l y nos encontramos con esto:

![image](https://github.com/user-attachments/assets/805fc03a-1e60-4a8d-9ae2-17db755be8f8)

Nos vamos al GTFObins para buscar node y ejecutar los que no salga en la shell con el nombre root.

![image](https://github.com/user-attachments/assets/2011dff2-fbc9-413d-94fe-d406f5f3f0bb)

Y ya somos root.

![image](https://github.com/user-attachments/assets/046da5ab-428e-455b-af8a-5ad4ad9ebf06)








