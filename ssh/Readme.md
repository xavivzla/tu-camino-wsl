Si quieres usar tu *.ssh* que tienes en tu maquina en el wls solo tienes que copiar la carpeta, y aplicar los cambios en los permisos.

para abrir la carpeta del wsl en windows.

```bash
    explorer.exe .
```

despues de copiar la carpeta .ssh aplicamos los permisos

```bash
    # entramos a la carpeta .ssh
    ~/.ssh/
    sudo chmod 644 id_rsa.pub
    sudo chmod 600 id_rsa
    sudo chmod 644 known_hosts
    # salimos de la carpeta y le cambiamos los permisos
    ../
    sudo chmod 700 .ssh/
    # nos autenticamos en GitHub
    ssh -T git@github.com
```