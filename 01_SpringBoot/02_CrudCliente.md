# Crue de Cliente

## Diseño paquetes proyecto producto

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/2f8079f1-a291-4d31-b36f-b14b47bce0dd)

## Proyecto su paquetes

El proyecto de productos debe tener tres paquetes donde se van agrupar nuestras clases en java

- controller: todas las clases de tipo controlador, las que tiene las anotación **@RestController**
- services: todas las clases de servicio, es como la capa de dominio, las funcionalidad de nuestro api.
- repositories: todo lo relacionado con la capa de persistencias nuestras clases repository y entity.

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/8d0f7a42-debb-41c3-b46a-0efdfa6aa217)

## Dependencia

Para usar la capa de persistencia se debe tener las depencias de **spring data jpa** y la del driver de conexión para el motor de base de datos con el que se va a trabajar, en este caso se va usar **Mysql** por lo tanto colocamos la dependencia correspondiente en el archivo **pom.xml**

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a2e99c71-40bc-49fc-b074-109095a31b1d)

## Configuración de la base de datos 

En el archivo **application.propreties** se debe configurar las credenciales de conexión a la base de datos, en este caso nuestra base de datos en mysql se llama **db_invoice_confenalco** la cual, debe estar creada previamente. 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/8bf16f69-1363-4a1c-98b1-f22ab7173bab)



# 1 Entities

## 1.1 Clase entity de cliente

Esta clase tiene la anotación Entity, la cual, marca la clase de tipo entidad que se va ha mapear con base de datos. Estas son algunas anotaciones:

- @Entity: define la clase de tipo entitie
- @Table: configuración que debe tomar la clase entity en relación a la tabla de base datos
- @Id: definie el atributo que va hacer la llave primaria en la tabla de la base de datos

En el siguiente documento puede ver un articulo del uso de las clases entity y sus anotaciones en spring boot 

[Documentación - Definición JPA Entity](https://www.baeldung.com/jpa-entities)

Esta clase se crea dentro del paquete **entities** dentro del paquete **repositories**

En esta clase Cliente se define los siguientes atributos. Son private por que se aplica **encapsulamiento**

- private Long id
- private String nombre
- private String apellido
- private String email
- private Date createAt

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/4dcdeab8-f08a-40be-ae51-e8b546eb73e7)

Continuación con los métodos getter and setter

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/6fe7dfee-8356-47c7-805b-6b6b904110b5)


Las clases entity deben implementar la insterface Serailizable:

En Java, la interfaz Serializable se utiliza para marcar una clase y permitir que sus objetos sean convertidos en una secuencia de bytes. Esto facilita la serialización de objetos, lo que significa que se pueden almacenar en archivos, enviar a través de redes o guardar en bases de datos.

# 2. Repository

Dentro del paqute **repositories** se denfine las interfaces repositories, las cuales, van ha heredar de la clase **CrudRepository** todos los métodos básicos del crud:

- findAll
- save
- findById
- Delete

Estos métodos van actuar sobre la clase entity que se defina, en este caso **Cliente** y también se pasa cual es el tipo de dato de la llave primaria de dicha clase, en este caso **Long**. 

**Nota**: esta interfaz al heredar de CrudRepository que es un clase de tipo repository es un tipo de clase bean que el contenedor de spring boot se encarga de gestionar, por lo tanto, permite que se haga inyección de dependencia. 

[Documentación spring jpa repository](https://www.baeldung.com/spring-data-read-only-repository)

## 2.1 Interfaz RepositoryCliente

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/dda9a5e5-b94f-4005-8066-37ccea35b6f7)


# 3. Services

En la capa de services, es donde se definie la logica del negocio. Son los servicios que van ha ser consumidos por los controladores. Se define una interfaz con los servicio, en este caso **ClienteService** y dentro del paquete **impl** se define la clase **ClienteServiceImpl**, dicha clase va la definición de los métodos de clarados en la interfaz **ClienteService**


## 3.1 Interfaz ClienteService

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/8d6449a4-c066-4f13-93e2-58f42d45d2f6)

## 3.2 Clase ClienteServiceImpl

Esta clase es una clase de tipo Servicio por eso tiene la anotación **@Service** dicha anotación hace que esta clase sea especial y sea un bean el cual va permitir hacer inyección de dependencia. 

Por otra parte, hace la inyección de dependencia de **RepositoryCliente**, que proporciona los métodos que van interactuar con la base de datos. 

Cuando se aplica la anotación @Transactional a un método o clase, Spring intercepta las llamadas a ese método y se encarga de iniciar, comprometer o revertir automáticamente las transacciones según sea necesario. Esto significa que si una excepción ocurre durante la ejecución del método anotado, Spring se asegurará de que se realice un rollback (reversión) de la transacción, lo que garantiza la integridad de los datos.

[Documenetación spring-transaction-read-only](https://www.baeldung.com/spring-transactions-read-only)

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/8fdb8f3d-b263-4d3d-a7b4-7b6fe600e743)


# 4. Controller

Se definie la clase de tipo controller.Es la que está expuesta a atender al llamado de las peticiones que le hacen al api. La anotación **@RestController**

La anotación **@RestController** en Spring Boot se utiliza para marcar una clase como un controlador (controller) de API REST. Esta anotación combina las anotaciones **@Controller** y **@ResponseBody**, lo que significa que la clase anotada con **@RestController** es capaz de manejar las solicitudes HTTP y devolver directamente objetos serializados como respuestas en formato JSON o XML.

Al utilizar la anotación @RestController, no es necesario anotar cada método individualmente con @ResponseBody, ya que la anotación @RestController se encarga de eso automáticamente para todos los métodos del controlador.

## 4.1 ClienteController

![image](https://github.com/crodrigr/microservicios-spring-boot-confenalco/assets/31961588/a77973e7-d902-4b7b-870a-0b30d2d3abb9)
