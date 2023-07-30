# Spring Securiyt


![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/31a02210-3c5f-4c1b-a55f-60033a4f4fba)

<br>
<br>
<br>

## 1 Authorization Server

<br>

En el contexto de Spring Boot y la seguridad de aplicaciones web, un "Authorization Server" (Servidor de Autorización) es un componente que se encarga de emitir tokens de acceso y validar las solicitudes de autorización realizadas por aplicaciones cliente. Este servidor juega un papel crucial en la implementación del flujo de OAuth 2.0, un protocolo de autorización ampliamente utilizado para proteger recursos y permitir que las aplicaciones accedan a ellos en nombre de los usuarios.

El Authorization Server es responsable de autenticar a los usuarios y de emitir tokens de acceso (tokens de acceso OAuth 2.0) que representan los derechos de acceso del usuario a recursos protegidos. Estos tokens de acceso son utilizados por las aplicaciones cliente para acceder a recursos protegidos en nombre del usuario autenticado, sin que las aplicaciones tengan que solicitar las credenciales del usuario en cada solicitud.

En una arquitectura típica de OAuth 2.0, el Authorization Server trabaja junto con otros componentes clave, como:

1. **Resource Server (Servidor de Recursos)**: Es el servidor que almacena y protege los recursos a los que se accede mediante tokens de acceso. El Resource Server utiliza el token de acceso para validar las solicitudes de las aplicaciones cliente y proporcionar acceso a los recursos solicitados si el token es válido y autorizado.

2. **Client Application (Aplicación Cliente)**: Es la aplicación que solicita el acceso a los recursos protegidos en nombre del usuario. La aplicación cliente obtiene el token de acceso del Authorization Server y lo envía junto con las solicitudes al Resource Server para acceder a los recursos.

En el ecosistema de Spring Boot, puedes implementar un Authorization Server utilizando Spring Security OAuth 2.0, que proporciona una amplia gama de características y opciones para gestionar la seguridad y la autorización en tu aplicación. Spring Security OAuth 2.0 facilita la configuración de un Authorization Server personalizado y te permite controlar el proceso de emisión y validación de tokens de acceso.

Es importante entender que la implementación de un Authorization Server debe realizarse con especial cuidado, ya que la seguridad y la protección de los recursos de los usuarios dependen de su correcto funcionamiento y configuración. Por lo tanto, siempre es recomendable seguir las mejores prácticas de seguridad y utilizar bibliotecas y herramientas probadas para asegurar la robustez de tu Authorization Server y tu aplicación en general.

<br>
<br>
<br>

## 2. Resource Server

<br>

En el contexto de seguridad de aplicaciones web y OAuth 2.0, un "Resource Server" (Servidor de Recursos) es el componente que almacena y protege los recursos a los que se accede mediante tokens de acceso emitidos por el Authorization Server (Servidor de Autorización).

En el flujo de OAuth 2.0, una vez que un usuario ha sido autenticado y autorizado por el Authorization Server, este emite un token de acceso al cliente (aplicación cliente). El cliente utiliza este token de acceso para acceder a los recursos protegidos en nombre del usuario en el Resource Server.

El Resource Server tiene la responsabilidad de validar el token de acceso recibido de la aplicación cliente y, si el token es válido y autorizado, permitir el acceso a los recursos solicitados. Los recursos pueden ser datos, servicios o cualquier otra información protegida que el usuario haya permitido que la aplicación cliente acceda.

El Resource Server debe asegurarse de que el token de acceso es válido, no ha caducado y que la aplicación cliente tiene los permisos adecuados para acceder a los recursos solicitados. Además, puede aplicar políticas de autorización adicionales para determinar si el cliente tiene el derecho de acceder a recursos específicos.

En una arquitectura típica de OAuth 2.0, el Resource Server trabaja junto con otros componentes clave, como:

1. **Authorization Server (Servidor de Autorización)**: Es el servidor que emite los tokens de acceso después de autenticar y autorizar al usuario. El Authorization Server y el Resource Server pueden ser el mismo servidor en algunos casos.

2. **Client Application (Aplicación Cliente)**: Es la aplicación que solicita el acceso a los recursos protegidos en nombre del usuario. La aplicación cliente obtiene el token de acceso del Authorization Server y lo envía junto con las solicitudes al Resource Server para acceder a los recursos.

El Resource Server juega un papel importante en la implementación de la seguridad y la protección de recursos en aplicaciones distribuidas y sistemas que utilizan el protocolo OAuth 2.0 para gestionar el acceso a recursos protegidos. Al validar los tokens de acceso y aplicar políticas de autorización, el Resource Server garantiza que solo las aplicaciones autorizadas y autenticadas pueden acceder a los datos y servicios protegidos.

<br>
<br>
<br>

## 3. Proceso autenticación

<br>

Detalle del proyeceso de autenticación. Lo que ocurre detras de escena. 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/39af06cd-95cf-4fe8-9426-c4b42bbfd87a)

