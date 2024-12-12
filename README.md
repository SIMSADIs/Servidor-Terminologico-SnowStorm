# Despliegue de SnowStorm en la nube

En el presente repositorio se muestra como hacer la configuración inicial para conectarse a un servidor remoto en un Droplet de DigitalOcean, para ello se siguieron las instrucciones de este [video](https://youtu.be/dGBjBECs6m0).

Los comandos utilizados para ello fueron los siguientes.

1.- Al ingresar el comando se pide que ingreses el directorio donde se alojará la clave SSH junto a su nombre y contraseña.
```
ssh-keygen
```

2.- Entras a la raíz del directorio de tu servidor.
```
ssh root@<IP_servidor>
```

3.- Abres el archivo de configuración de la clave SSH.
```
cd .shh && sudo nano authorized_keys
```

4.- Pegas tu clave SSH, debe ser algo similar a la de abajo.
```
Paste: ssh-config AAAAC3NzaC1lZDI1NTE5AAAAIGKLHH7oTYcRYnhOkywmklnAoFFGHSXgmFoNom0Q+F USER@user
```

5.- Guardas el archivo .
```
ctrl s
```

6.- Cierras el archivo.
```
ctrl x
```

7.- Agregas usuario a la clave.
```
adduser biomedicauv
```

8.-  Entras al usuario.
```
usermod -aG sudo biomedicauv
```

Para entrar al Droplet mediante la llave SSH creada desde la terminal de Visual Studio Code, se debe instalar la extensión Remote - SSH y Remote - SSH: Editing Configuration Files, posteriormente se debe ajustar el archivo SSH  config file con los datos del servidor y la dirección de tu llave en tu dispositivo cómo se muestra en el ejemplo. 

```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host config
    HostName  IP_server
    User root
    IdentityFile ~/.ssh/key_name
```

En este ejemplo se muestra cómo entrar al archivo de configuración del host, cómo entrar al servidor y cómo navegar en los directorios del servidor.

<img src="https://github.com/SIMSADIs/Servidor-Terminologico-SnowStorm/blob/setting-cloud/enter-droplet.gif" alt="Pegar ID" width="650" height="400">


Finalmene en el terminal del droplet iniciado en Visual Studio Code se deben instalar los requerimientos para desplegar SnowStorm, se debe desplegar SnowStorm y se le deben cargar sus terminologías como se muestra en este repositorio.
