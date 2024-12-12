# Despliegue de SnowStorm en la nube

En el presente repositorio se muestra como hacer la configuración inicial para conectarse a un servidor remoto en un Droplet de DigitalOcean, para ello se siguieron las instrucciones de este [video](https://youtu.be/dGBjBECs6m0).

Los comandos utilizados para ello fueron los siguientes.

1.-
```
ssh-keygen
```

2.-
```
ssh root@137.184.182.23
```

3.-
```
cd .shh && sudo nano authorized_keys
```

4.-
```
Paste: ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGRw7LylFN5MOfcRYnhOqZOVhroISrZoXgmFoNom0Q+F ferna@Fxrni
```

5.-
```
ctrl s
```

6.-
```
ctrl x
```

7.-
```
adduser biomedicauv
```

8.-
```
usermod -aG sudo biomedicauv
```

Para  entrar al Droplet mediante la llave SSH creada se hace mediante Visual Studio Code, se debe instalar la extensión Remote - SSH y Remote - SSH: Editing Configuration Files, posteriormente se debe ajustar el archivo SSH  config file con los datos del servidor y la dirección de tu llave en tu dispositivo cómo se muestra en el ejemplo. 

```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host config
    HostName 137.184.182.23
    User root
    IdentityFile ~/.ssh/id_config

```
Finalmene en el terminal del droplet iniciado en Visual Studio Code se deben instalar los requerimientos para desplegar SnowStorm, se debe desplegar SnowStorm y se le deben cargar sus terminologías como se muestra en este repositorio.
