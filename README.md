# docker-compose-sqlserver-2019
Configuración básica de SQLServer 2019 sobre una imagen de Ubuntu 18.04

Recomendable agregar los permisos correspondientes al directorio donde se guardaran los datos, en caso que utilices linux el comando es:

> mkdir /path/directorio/donde/guardar/datos
> 
> sudo chgrp -R 0 /path/directorio/donde/guardar/datos
> 
> sudo chmod -R g=u /path/directorio/donde/guardar/datos

### Comando para ejecutar el contenedor
> docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=1234567890a' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-CU3-ubuntu-18.04 -v /path/directorio/donde/guardar/datos:/var/opt/mssql

### Comando para iniciar los contenedores a través de Docker Compose

Una vez creado el volumen ya podemos ejecutar el contenedor usando Docker Compose. Ubicate en el directorio donde se encuentra el archivo docker-compose.yml y ejecuta

> docker-compose up -d

### Comando para finalizar los contenedores a través de Docker Compose
> docker-compose down

### Datos de acceso a SQLServer 2019

Puedes utilizar [DBeaver](https://dbeaver.io/) o SQL Server Management Studio para conectarse a la base de datos.

| Parámetro | Valor |
| --- | --- |
| databasename | master |
| Authentication Type | Sql Login |
| Usuario | sa |
| Contraseña | 1234567890a o el valor personalizado |
| Guardar Password | Si |