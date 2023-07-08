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

# 4. Se agrega regiones en Import.sql

En el archivo de import.sql se hace el insert de las regiones, con id, para relacionarlo con los clientes.

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/406a118f-c8d1-4d25-acdf-954ae2a353d8)

# 5. Crear un endpoint o servicio para listar las regiones

Este servicio se va asignar al ClienteController para no crear un serivicio completo y exclusivo para regiones, desde la capa de repositories. Por lo tanto, en el ClienteRepoistory se adiciona un método con una consulta personalizada para que traiga el listado de regiones. 

## 5.1 Consulta personlizada para regiones

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/5d237557-80f3-4322-866e-11d596ba1eda)

## 5.2 Se adiciona un método en la interfaz ClienteService

El nuevo método va trae el listado de regiones. 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/45473eb3-8b96-484f-9723-9b0d82a4bcfb)

## 5.3 Se crea el método findAllRegiones en ClienteServiceImpl

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/2434d757-5786-4de9-b664-3925b03a85c8)

## 5.4 Agregar un endpoin /cliente/regiones en ClienteController  

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/f411a96c-4c56-47e6-a770-58006a6a2ba0)

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/838b3245-cd76-4809-bc4b-2ea983f9f813)
