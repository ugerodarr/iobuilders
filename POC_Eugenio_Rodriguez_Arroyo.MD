## Introducción

Dadas las especificaciones del POC planificaremos el desarrollo teniendo en cuenta:
- El tiempo programado (4 meses).
- Capacidad del equipo.
- Ventajas y desventajas de cada tecnología.


***


## Riesgos

- La seguridad es un factor clave a tener en cuenta, ya que estamos tratando con datos sensibles bancarios del usuario. También habría que securizar la identificación de los usuarios y las transacciones.
- Autenticación, las llamadas realizadas de la parte Frontend a la Backend deberán ser identificadas mediante tokens como OAuth2.
- Tener en cuenta las legislaciones vigentes para leyes de protección de datos, cambios de divisas etc...
- Conectividad y disponibilidad, contaremos con más de un servidor en distintos lugares con algún tipo de balanceador para distribuir el tráfico entre los distintos servidores.
- Desconocimiento de la tecnología blockchain, ya que es una tecnología poco probada e implementada y la gente tiene poca experiencia.


***


## Tecnología y arquitectura

### Arquitectura

Dado que, según las especificaciones se debe realizar una aplicación móvil, se basará en cliente-servidor.

La arquitectura que usaremos será hexagonal, con diseño DDD. Esta arquitectura facilita el mantenimiento y el desarrollo de nuevas funciones, además es altamente escalable. La meta de esta arquitectura es que los componentes sean fáciles de probar, poco acoplados e independientes. Como desventaja, el costo de creación de los componentes es mayor y aumenta la complejidad del desarrollo.

### Frontend

La aplicación movil (Frontend) será la cara visible al usuario, en ella se realizarán las solicitudes al servidor para posteriormente recibir su respuesta, es posible que se tenga que realizar alguna parte lógica, como por ejemplo las validaciones. Además, tiene que ser fácil e intuitiva de usar, y debe ser multiplataforma (iOS, Android).

Debido al tiempo del POC, creemos que no es viable afrontar un desarrollo nativo para cada uno de los sistemas operativos ya que habría que tener gente especializada en cada uno de ellos y el desarrollo tendría más costes y se alargaría en el tiempo.

Por lo tanto, para agilizar el tiempo elegiremos una tecnología híbrida como React Native. Esta tecnología está muy extendida y dispone de una comunidad muy involucrada, con muchos paquetes disponibles, además es el framework más usado para este tipo de desarrollos. Por contra, el rendimiento no será el mismo que el de una aplicación nativa y se pueden perder funcionalidades propias del sistema operativo, también la depuración es más compleja. 

Como librería de diseño hemos elegido Material UI.

Otra opción de framework sopesada ha sido Flutter, pero la hemos descartado por que su lenguaje de programación (Dart) es relativamente nuevo, y por ello su comunidad es más reducida, y se disponen de menos recursos de aprendizaje que en Javascript.

### Backend

La REST API se desarrollará usando Java con Spring-boot ya que es un framework bastante asentado, sencillo de usar y muchos desarrolladores conocen esta tecnología. El fin de esta REST API es que conecte con la aplicación móvil para usar toda su lógica de negocio. La parte de seguridad queda cubierta perfectamente por Spring Security, ya que incluye varios sistemas de autenticación.

Se ha elegido esta tecnología también porque las plataformas de cloud están preparadas para el uso de este framework.

También se adapta perfectamente a Ethereum, para ello usa la biblioteca web3j, que es ligera y reactiva.

Como desventaja, consume mas tiempo y memoria y no se tiene control sobre la recolección de basura.

La otra posibilidad que hemos valorado ha sido .NET Core, y lo hemos descartado porque es menos usado que Java y tiene menos librerías disponibles.


### Base de datos

Hemos elegido una base de datos relacional frente a una no relacional, para tener unos datos consistentes sin dar posibilidad a error. También cumple con todos nuestros requisitos, como almacenar una gran cantidad de datos y permite la conexión de un gran volumen de usuarios de forma simultánea.

La base de datos elegida es PostgreSQL, es Opensource, robusta, multiplataforma, también es sencilla de manejar porque usa SQL estándar. Como desventajas no cuenta con soporte oficial y es relativamente lento en inserciones y actualizaciones en bases de datos pequeñas.

Otra opción a valorar era MySQL, tiene características similares, pero no es tan eficiente en aplicaciones que requieran una constante modificación de escritura y suele estar enfocada a proyectos más pequeños.

### Blockchain

La plataforma elegida es Ethereum ya que su documentación es muy completa, existen muchos desarrolladores trabajando en ella y como es código libre está en continuo crecimiento.

Para desarrollar los smart contracts vamos a usar Solidity ya que es sencillo de utilizar, porque usa JavaScript que es un lenguaje bastante conocido. Solidity es rápido para poner en marcha y pueden desarrollarse test para ver el correcto funcionamiento. También dispone de un gran soporte y documentación.


### Testing y calidad de código

Para realizar las pruebas de la parte Frontend, usaremos la librería React testing libray y Jest.

En la parte Backend, usaremos Junit.

La cobertura minima de ambos test será del 50%.

Para evaluar la calidad de código usaremos la herramienta SonarQube.


***


## Equipo

- 1 Diseñador UIX, la mayor dedicación será al principio del proyecto, más tarde tendrá una dedicación del 20%.
- 1 Desarrollador Frontend Senior con experiencia en React Native.
- 1 Tech Lead Fullstack Senior que adapte sus habilidades a demanda de las necesidades del proyecto con experiencia en React Native y Java. También se encargará de liderar equipo. Se responsalizará de la calidad del producto y ofrecerá su visión técnica para conseguir los objetivos.
- 2 Desarrolladores Backend Senior, al ser el core de la aplicación consideramos que estarán durante todo el ciclo de vida del proyecto y tendrán experiencia en Java.
- 1 Desarrollador Backend Junior, el cual tenga nociones de Java.
- 1 QA, se incorporará a la mitad del proyecto y tendrá una dedicación del 50%.
- 1 Jefe de proyecto, que tendrá un 30% de dedicación y se encargará de dirigir todo el ciclo de vida de Scrum y verificar el avance del proyecto.
- 1 Experto en seguridad Senior, que sea especialista en blockchain.


***


## Cultura

### Metodología

Hemos decidido utilizar metodología Scrum ya que es adaptable, dispone de una respuesta rápida a los cambios y los clientes pueden colaborar abiertamente con el equipo.

Realizaría 8 sprints de 15 días, definiendo tareas para cada miembro del equipo y se llevarían a cabo las correspondientes daylies, sprint reviews y restrospective. 

### Valores de empresa

- Buen ambiente y comodo con ayuda constante de los compañeros.
- Trabajo en remoto de forma opcional, promoviendo ir a la oficina cada cierto tiempo para reforzar la relación de equipo.
- Horario de trabajo flexible.
- Dar oportunidades a la gente más junior.
- Promover formación para seguir aprendiendo para tener un mayor conocmiento para futuras implementaciones.


