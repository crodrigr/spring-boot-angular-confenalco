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

### 3.1 Authorization Server

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/39af06cd-95cf-4fe8-9426-c4b42bbfd87a)

<br>

### 3.2 Resource Server

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/28fc066f-8fb1-4e8b-96f4-81777310ea14)


## 4. Dependencias

<br>

### 4.1 Version spring

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/78c988a5-8146-4759-b45d-36b6781165e7)

<br>

### 4.2 Dependencias oauth

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/2cfe4160-5524-47c0-932d-a6d283577020)

<br>

### 4.3 Jakarta a javax

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/10f2fe27-16ce-4eea-a0ff-5879e14a1e48)

<br>

<details><summary>Mostrar código</summary>

<p>   
    
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.7.4</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.demo</groupId>
	<artifactId>demo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>demo</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>	      
		<!-- https://mvnrepository.com/artifact/mysql/mysql-connector-java -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    </dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.security.oauth</groupId>
			<artifactId>spring-security-oauth2</artifactId>
			<version>2.5.2.RELEASE</version>
		</dependency>
			<dependency>
			<groupId>org.springframework.security</groupId>
			<artifactId>spring-security-jwt</artifactId>
			<version>1.0.9.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>javax.xml.bind</groupId>
			<artifactId>jaxb-api</artifactId>
		</dependency>		
		
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>


```

</p>
</details>

<br>
<br>
<br>

## 5. Usuario 

### 5.1 UsuarioService 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/ad57fc04-f86b-490d-82a3-70617b2545bc)

<details><summary>Mostrar código</summary>

<p>   
    
```java

package com.demo.demo.services;

import com.demo.demo.repository.entities.Usuario;

public interface UsuarioService {

    
	public Usuario findByUsername(String username);
	
	public void delete(Usuario Usuario);


}


```

</p>
</details>

<br>

### 5.2 UsuarioRepository

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/5f16822c-a2d6-435e-88c5-6ff0fc2e9fb9)


<details><summary>Mostrar código</summary>

<p>   
    
```java
package com.demo.demo.repository;

import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.CrudRepository;

import com.demo.demo.repository.entities.Usuario;

public interface UsuarioRepository  extends CrudRepository<Usuario,Long> {

    public Usuario findByUsername(String username);
	
	@Query("select u from Usuario u where u.username=?1")	
	public Usuario findByUsername2(String username);
    
}


```

</p>
</details>

<br>

### 5.3 UsuarioServiceImpl

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/3aafa639-d97a-4bcb-bae9-cc44ff8a6b8a)


<details><summary>Mostrar código</summary>

<p>   
    
```java

package com.demo.demo.services.impl;

import java.util.List;
import java.util.stream.Collectors;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.UsernameNotFoundException;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.core.authority.SimpleGrantedAuthority;

import com.demo.demo.repository.UsuarioRepository;
import com.demo.demo.repository.entities.Usuario;
import com.demo.demo.services.UsuarioService;

@Service
public class UsuarioServiceImpl implements UsuarioService, UserDetailsService {
	
	private Logger logger = LoggerFactory.getLogger(UsuarioServiceImpl.class);

	@Autowired
	private UsuarioRepository usuarioDao;
	
	@Override
	@Transactional(readOnly=true)
	public Usuario findByUsername(String username) {
		return usuarioDao.findByUsername(username);
	}
	@Override
	@Transactional
	public void delete(Usuario usuario) {
		usuarioDao.delete(usuario);
		
	}

	@Override
	@Transactional(readOnly=true)
	public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
		
		Usuario usuario=usuarioDao.findByUsername(username);
		
		if(usuario==null){
		  logger.error("Error en el login: no existe el usuario "+username+" en el sistema!");
		  throw new UsernameNotFoundException("Error en el login: no existe el usuario " +username+ " en el sistema!");
		}
		
		List<GrantedAuthority> authorities = usuario.getRoles()
				.stream()
				.map(role-> new SimpleGrantedAuthority(role.getNombre()))
				.peek(authority-> logger.info("Role: "+authority.getAuthority()))
				.collect(Collectors.toList());
		
		return new User(usuario.getUsername(),usuario.getPassword(),usuario.getEnabled(),true,true,true,authorities);
		
		
	}

}

```

</p>
</details>

Este fragmento de código corresponde a la implementación del método `loadUserByUsername` de una clase de servicio en Spring Boot que implementa la interfaz `UserDetailsService`. Este método se utiliza para cargar los detalles del usuario durante el proceso de autenticación en Spring Security. Aquí está la explicación paso a paso del código:

1. **Método `loadUserByUsername`**: Este método se anota con `@Override`, lo que significa que está sobrescribiendo el método de la interfaz `UserDetailsService`.

2. **Buscar el usuario en la base de datos**: Se utiliza el `usuarioDao` (que es una instancia de `UsuarioRepository`) para buscar un usuario en la base de datos a partir del nombre de usuario proporcionado.

3. **Comprobación de existencia del usuario**: Si no se encuentra ningún usuario con el nombre de usuario proporcionado, se lanza una excepción `UsernameNotFoundException`. Esto ocurre cuando un usuario intenta autenticarse con un nombre de usuario que no existe en el sistema.

4. **Mapeo de roles a authorities**: Si el usuario es encontrado en la base de datos, se procede a obtener sus roles y mapearlos a objetos `GrantedAuthority`. Cada rol del usuario se transforma en un `SimpleGrantedAuthority` y se agrega a una lista de `authorities`. Los `GrantedAuthority` representan los permisos o roles que un usuario tiene en el sistema y se utilizan para controlar el acceso a recursos y funcionalidades.

5. **Logging**: Se utilizan registros (logs) para registrar información relevante sobre los roles del usuario. Cada rol se registra utilizando el `logger`.

6. **Creación del objeto `User`**: Finalmente, se crea un objeto `User` que implementa la interfaz `UserDetails`, que representa al usuario autenticado. Se utilizan varios atributos del usuario, como el nombre de usuario, contraseña, estado de cuenta y la lista de authorities (roles), para construir el objeto `User`.

7. **Retorno del objeto `User`**: El objeto `User` construido se devuelve como resultado del método. Es utilizado por Spring Security para llevar a cabo el proceso de autenticación y autorización.

En resumen, este método carga los detalles del usuario durante el proceso de autenticación y devuelve un objeto `User` que representa al usuario autenticado, incluyendo sus roles que se utilizarán para controlar el acceso en la aplicación protegida por Spring Security.

<br>
