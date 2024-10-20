# Tarea3_SXE

***Apartados***

1. ***Descarga la imagen 'httpd' y comprueba que está en tu equipo.***

    ***Primero descargamos la imagen httpd***
    ```sh
    sudo docker pull httpd:2.4
    ```
    ***Ahora comprobamos si se instaló correctamente***
     ```sh
     sudo docker images
     ```

2. ***Crea un contenedor con el nombre 'dam_web1'.***

    ***Para crear el contenedor con el nombre tenemos que utilizar este comando***
   ```sh
   sudo docker container create -i -t --name dam-web1 httpd
   ```
   ***Comprobamos otra vez si se creó***
   ```sh
   sudo docker ps -a
   ```


3. ***Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?
Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tu elijas***

     ***Primero necesitamos instalar ssh para poder conectar con la maquina***
     ```sh
     sudo apt install openssh-server
     ```
     ***Mapeamos el puerto del contenedor al puerto del equipo***
     ```sh
     sudo docker run -d --name dam_web1 -p 8000:80 httpd:2.4
     ```
     ***Ahora podemos crear el directorio***
     ```sh
     mkdir /home/desktop/apache_host
      ```
     ***Ahora necesitamos ejecutar este comando para crear el contenedor con el directorio mapeado***
     ```sh
     sudo docker run -d --name dam_web1 -p 8000:80 -v /home/desktop/apache_host:/usr/local/apache2/htdocs httpd:2.4
   ```

4. ***Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador.***

      ***Primero creamos el archivo html, si queremos se puede crear con la nano***
      ```sh
      <html>
     <head>
         <title>Hola Mundo</title>
     </head>
     <body>
         <h1>Hola Mundo</h1>
     </body>
    </html>
   ```
      ***Después lo metemos en la carpeta y despues vamos a comprobarlo a un navegador***
      ```sh
      http://10.0.9.151:8000
      ```
5. ***Crea otro contenedor 'dam_web2' con el mismo bind mount y a otro puerto, por ejemplo 9080.***

      ***El procedimiento es el mismo, solo varían los puertos***
   
      ```sh
      sudo docker run -d --name dam_web2 -p 9080:80 -v /home/desktop/apache_host:/usr/local/apache2/htdocs httpd:2.4

      ```

      ***Comprobamos si corre***
      ```sh
   sudo docker ps```
6. ***Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador: http://localhost:9080 http://localhost:8000***

      ***Vamos a un navegador e introducimos***
      ```sh
      http://10.0.9.151:9080 
    http://10.0.9.151:8000
      ```

7. ***Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página***

      ***Nos vamos al html anterior y hacemos algun cambio***
      ```sh
   <html>
        <head>
            <title>Cambios en el hola mundo</title>
        </head>
        <body>
            <h2><strong>Se han realizado los cambios<strong></h2>
            <p style="color: blue;"Buenas tardes</p>
        </body>
    </html>
      ```
      ***Abrimos otra vez e introducimos esto***
      ```sh
       http://10.0.9.151:9080 
    http://10.0.9.151:8000
   ```

