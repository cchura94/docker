# Instalción Docker en Ubuntu 22.04
 
- Antes de continuar con la instalación limpia de Docker, se recomienda eliminar cualquier paquete conflictivo: 
```
sudo apt-get remove docker docker-engine docker.io docker-doc docker-compose podman-docker containerd runc

sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
```

- Además, las imágenes, contenedores, volúmenes, archivos de configuración personalizados, etc. no se eliminan automáticamente. Para eliminarlos:
```
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```
## Installation
- Actualice el índice del paquete: 

```
sudo apt-get update
```
- Instale los paquetes necesarios para permitir el acceso a los repositorios de Docker a través de HTTPS:

```
sudo apt-get install apt-transport-https ca-certificates curl gnupg software-properties-common
```
- Agregue la clave GPG oficial de Docker para garantizar la autenticidad e integridad de los paquetes de Docker:
```
sudo mkdir -p /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
- Agregue el repositorio de Docker a la lista de fuentes del administrador de paquetes:
```
echo \
"deb [arch="$(dpkg --print-architecture)" \
signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
"$(. /etc/os-release && echo "$UBUNTU_CODENAME")" stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- Actualice el índice del paquete local:
```
sudo apt-get update
```

- Instalar Docker::
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin docker-compose
```

- Compruebe si Docker se está ejecutando:
```
sudo systemctl status docker
```