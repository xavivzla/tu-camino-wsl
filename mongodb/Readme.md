instalar mongodb en wsl2 debian 10 / ubuntu 20.04 LTS


puedes descargar los paquetes y instalar los que requieras.

* Debian 10/Buster :
    * [mongodb-org](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org_4.4.1_amd64.deb)
    * [mongodb-org-server](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org-server_4.4.1_amd64.deb)
    * [mongodb-org-shell](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org-shell_4.4.1_amd64.deb)
    * [mongodb-org-mongos](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org-mongos_4.4.1_amd64.deb)
    * [mongodb-org-tools](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org-tools_4.4.1_amd64.deb)
    * [mongodb-org-database-tools-extra](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-org-database-tools-extra_4.4.1_amd64.deb)
    * [mongodb-database-tools](http://repo.mongodb.org/apt/debian/dists/buster/mongodb-org/4.4/main/binary-amd64/mongodb-database-tools_100.2.0_amd64.deb)
* Ubuntu 20.04 LTS (Focal Fossa):
    * [mongodb-org](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org_4.4.1_amd64.deb)
    * [mongodb-org-server](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org-server_4.4.1_amd64.deb)
    * [mongodb-org-shell](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org-shell_4.4.1_amd64.deb)
    * [mongodb-org-mongos](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org-mongos_4.4.1_amd64.deb)
    * [mongodb-org-tools](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org-tools_4.4.1_amd64.deb)
    * [mongodb-org-database-tools-extra](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-org-database-tools-extra_4.4.1_amd64.deb)
    * [mongodb-database-tools](http://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/4.4/multiverse/binary-amd64/mongodb-database-tools_100.2.0_amd64.deb)

    # O

    puedes instalar todo desde el repositorio.

    primeros necesitamos agregar la llave 

   ```bash
    wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
  ```

  creamos el archivo para añadir el repositorio

 ```bash
    #ubuntu
    echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list

```

actualizamos

```bash
sudo apt-get update
```
ahora instalamos el mongodb

```bash
    sudo apt-get install -y mongodb-org
```

ahora aqui es donde viene el problema en wsl por que no agrega el servicio.

descargamos el init.d de los servicios y lo agregamos a nuestros servicios

```bash
    sudo curl -o /etc/init.d/mongod https://raw.githubusercontent.com/mongodb/mongo/master/debian/init.d
```

ahora le damos permiso


```bash
    sudo chmod +x /etc/init.d/mongod
```

ahora puedes ejecutar

```bash
sudo service mongod start|stop|restart
```



