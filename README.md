# Tarea3_SXE

***Apartados***

1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

    ***Primero descargamos la imagen httpd***
    ```sh
    sudo docker pull httpd:2.4
    ```
    ***Ahora comprobamos si se instaló correctamente***
     ```sh
     sudo docker images
     ```

2. Crea un contenedor con el nombre 'dam_web1'.

    ***Para crear el contenedor con el nombre tenemos que utilizar este comando***
   ```sh
   sudo docker container create -i -t --name dam-web1 httpd
   ```
   ***Comprobamos otra vez si se creó***
   ```sh
   sudo docker ps -a
   ```

