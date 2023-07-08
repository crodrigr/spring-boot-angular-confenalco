# Relaciones en spring data jpa

[Documentación relaciones spring data jpa](https://www.adictosaltrabajo.com/2020/04/02/hibernate-onetoone-onetomany-manytoone-y-manytomany/)

# 1. Región y cliente. 

Una región tiene uno o muchos clientes y un cliente pertenece a una única región. Por parte de la región no nos interesa obtener los clientes por región. Por lo tanto, se convierte e una relación unidireccional desde cliente que si nos interesa saber a que región pertenece.  

![image](https://user-images.githubusercontent.com/31961588/156847559-791a4e02-125d-402e-925a-27cd0be338e9.png)

# 2. Se crea la entidad región

Se crea la entidad región dentro del paquete de entities. 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/49ace39b-6b91-4890-a09e-55948fdfb2cb)

# 3. Se construye la relación entre cliente y región. 

Esta relación es una relación **ManytoOne** en una sola direción, y va estar al lado del cliente. Se debe crear el atributo Region con sus métodos getter y setter.

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/9fd40234-a99f-46f8-b595-5ae24b90f96a)
