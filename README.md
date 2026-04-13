1. Configuración de la Red Base (VPC)
Para asegurar que el proyecto se ejecuta en un entorno de red aislado y controlado, creamos una VPC (Virtual Private Cloud) personalizada en AWS. Dentro de esta VPC, configuramos subredes (subnets) para estructurar nuestra red y definimos una tabla de enrutamiento (Route Table), asegurándonos de conectar un Internet Gateway para que el entorno tenga acceso a Internet.

2. Despliegue del Servidor (Amazon EC2)
Una vez preparada la red, lanzamos una instancia EC2 utilizando Ubuntu como sistema operativo.
A nivel de conectividad, esta instancia cuenta con dos direcciones:

IP Privada: Asignada automáticamente por la VPC al crear la instancia, utilizada para la comunicación interna segura dentro de nuestra red de AWS.

IP Pública: Asignada para poder acceder al servidor desde el exterior (vía SSH) y para servir la aplicación. (Esto se configuró habilitando la opción de "Auto-assign public IP" durante el lanzamiento de la instancia, aunque también se puede lograr asociando una IP elastica).

3. Vinculación con GitHub y Descarga del Proyecto
Una vez dentro del servidor Ubuntu, preparamos el entorno para traer el código fuente.

Dado que GitHub requiere el uso de Tokens en lugar de contraseñas tradicionales por motivos de seguridad, configuramos Git para que recuerde nuestras credenciales. Entonces vamos a utilizar el gestor de credenciales de Git ejecutando el comando:
git config --global credential.helper store

Tras configurar esto, utilizamos git clone e introducimos nuestro usuario y el Token. Gracias al comando anterior, el token de GitHub quedó guardado de forma segura en el servidor, permitiéndonos hacer futuros git pull o actualizaciones sin tener que volver a introducir la clave cada vez.
