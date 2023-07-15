# Angular 

Angular es un popular framework de aplicaciones web de código abierto desarrollado y mantenido por Google. Se utiliza para construir aplicaciones web dinámicas de una sola página (SPAs) y aplicaciones web progresivas (PWAs). Angular está escrito en TypeScript, que es una superconjunto de JavaScript, y aprovecha el poder de TypeScript para proporcionar un framework robusto y escalable para construir aplicaciones complejas.

Aquí están algunas características y conceptos clave de Angular:

   1. **Arquitectura basada en componentes:** Angular sigue una arquitectura basada en componentes donde la aplicación se compone de componentes reutilizables y modulares. Los componentes son los bloques de construcción de una aplicación Angular y encapsulan el código HTML, CSS y TypeScript necesario para renderizar e interactuar con una parte específica de la interfaz de usuario.

   2. **Sintaxis de plantilla:** Angular utiliza una sintaxis declarativa de plantillas que combina la marca HTML con directivas y enlaces específicos de Angular. Esto permite a los desarrolladores definir vistas dinámicas y establecer enlaces de datos entre los datos del componente y la vista.

   3. **Inyección de dependencias:** Angular tiene un potente sistema de inyección de dependencias que ayuda a gestionar las dependencias entre diferentes componentes y servicios. Permite la creación de componentes con acoplamiento débil, lo que hace que la aplicación sea más mantenible y testeable.

   4. **Enrutamiento:** Angular proporciona un módulo de enrutador incorporado que permite la navegación entre diferentes vistas o páginas en una aplicación de una sola página. Los desarrolladores pueden definir rutas y asociar componentes con rutas específicas, lo que permite la creación de experiencias similares a múltiples páginas dentro de una aplicación de una sola página.

   5. **Programación reactiva:** Angular adopta los conceptos de programación reactiva con el uso de RxJS (Reactive Extensions para JavaScript). RxJS proporciona un conjunto poderoso de operadores y observables que permiten manejar operaciones asíncronas, flujos de eventos y manipulación de datos de manera reactiva y declarativa.

   6. **Formularios:** Angular ofrece un amplio soporte para construir formularios complejos con características como enlace de datos bidireccional, validación de formularios y manejo de envío de formularios. Proporciona tanto formularios basados en plantillas como formularios reactivos, lo que brinda a los desarrolladores flexibilidad para elegir el enfoque que mejor se adapte a sus necesidades.

   7. **Pruebas:** Angular cuenta con un sólido soporte para pruebas unitarias y pruebas de extremo a extremo. Proporciona utilidades y herramientas para escribir pruebas para componentes, servicios y otras partes de la aplicación, lo que facilita garantizar la calidad y confiabilidad del código.

Angular tiene una comunidad grande y activa, lo que significa que hay muchos recursos, tutoriales y bibliotecas de terceros disponibles para ayudar a los desarrolladores a construir aplicaciones Angular de manera eficiente. Es ampliamente utilizado en la industria y ha sido adoptado por muchas empresas para desarrollar aplicaciones empresariales a gran escala.

## 1. Ambiente de desarrollo

Para trabajar con angular se debe tener las siguientes herramientas:

  -  Visual Studio Code
  -  Git
  -  Nodejs
        - npm
  -  angular/cli

#### 1.1 Validar ambiente

Verificar que tenga todas al herramientas

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/224fa6fc-84a0-4915-a570-b543077005bd)

## 2. Crea proyecto de angular

Angular es un **framework** que ofrece varios comandos del **cli** que facilita el desarrollo de aplicaciones Web. Para crear un proyecto se hace a través del siguiente comando: **ng new <nombre-app>**. Al ejecutar este comando debe estár dentro del directorio de su area de trabajo. 

#### 2.1 ng new app

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/b0cc9510-988f-4f63-a744-5fa811107b8e)

## 3. Start up proyecto

Angular tiene un servidor web embebido el cual se inia con el comando **ng serve**

#### 3.1 ng server

Una vez se crea el proyecto debe ingresa por la terminal al directorio del proyecto creado y ejecutar el comando **ng serve**. Después de iniciado el proyecto vaya al navegado al **http://localhost:4200** 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/668acf28-04cb-4482-9e03-0c6ebb88e70b)

#### 3.2 Bienvenida de angular
![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/2760b390-1207-4028-a3fe-51b825d782fa)


## 4. Estructura de un proyecto de angular

Todo proyecto en angular va tener la siguiente estructura, la cual, tiene un directorio **src** donde están todos los archivos fuentes u otros archivos de configuración. 

#### 4.1 Directorios y archivos

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/ee6a0878-5629-4d0f-8e5e-f783616a71eb)


