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

3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?
Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tu elijas

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
