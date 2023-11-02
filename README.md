# AYGO lab1
## Descripción
El taller consiste en diseñar una aplicación web ligera usando Spark
java (http://sparkjava.com/). Luego se utiliza docker para contenerizar la aplicación y poder desplegarla. A partir de este contenedor se creará
una imagen que se almacenará en DockerHub para usarla durante el despliegue a AWS

## Arquitectura utilizada
La arquitectura de la aplicación se compone de una instancia de EC2 en la cual se ejecuta un container
de Docker que representa un servidor web el cual se accede mediante el dns publico de la instancia y el puerto `42000`. A continuación se presenta un diagrama con la arquitectura.
![docker1.png](img%2Fdocker1.png)
## Pre-requisitos
* [Docker](https://www.docker.com/) - Administrador de contenedores
* [Maven](https://maven.apache.org/) - Administrador de dependencias
* [Git](https://git-scm.com/) - Sistema de control de versiones
* [Java 8](https://www.java.com/) - Tecnología para el desarrollo de aplicaciones

## Instrucciones de construcción y ejecución

1. **Construir la aplicación**: Desde la raíz del proyecto compilar la aplicación

``mvn clean install``

2. **Crear la imagen** : Desde la raíz del proyecto, ejecutar el siguiente comando de docker para
   construir la imagen de la aplicación usando los archivos generados anteriormente:

``docker build --tag dockersparkprimer .``

3. **Ejecutar la aplicación**

**Java:** Para ejecutar la aplicación localmente **SIN** usar contenedores se debe ejecutar el siguiente comando:

``java -cp "target/classes:target/dependency/*" co.edu.escuelaing.SparkWebServer``

La aplicación se podrá acceder utilizando la siguiente URL http://localhost:4567/hello

**Docker:** Para ejecutar la aplicación utilizando contenedores utilice el siguiente comando:

``docker run -d -p 34000:6000 dockersparkprimer``

La aplicación se podrá acceder utilizando la siguiente URL http://localhost:34000/hello


## Resultados del despliegue
A continuación se muestran evidencias de la ejecución de la aplicación una vez desplegada en la
máquina de EC2 creada.
### Instancia EC2 activa
![ec2.png](img%2Fec2.png)
### Ejecución del container con la imagen creada
![docker.png](img%2Fdocker.png)
### Resultado del endpoint al consultar la instancia a través de internet
![web.png](img%2Fweb.png)