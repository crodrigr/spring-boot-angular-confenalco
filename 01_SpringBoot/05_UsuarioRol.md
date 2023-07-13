# Usuario y Roles

## 1. Crear entity Role

Se crea la clase Role de tipo Entity. Tiene dos atributos. 

```mermaid
classDiagram
    User "1..*" <--> "1..*" Role
    User : -Long id
    User : -String username
    User : -String password
    User : -Boolean enable
    User : -String nombre
    User : -String apellido
    User : -String email
    User: +getter()
    User: +setter()
    class Role{
        -Long id
        +String nombre
        +getterSetter()        
    }
    
```


![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/970d7e93-0c26-4795-ae4e-f0c94fea4d87)

## 2. Crear entity Usuario

Se crea la clase Usuario de tipo Entity

### 2.1 Atributos
![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/488f355e-6bd4-47fb-ad7c-c0716da7d5e9)

### 2.2 Getter y Setter

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/72cbe6e0-fb77-4878-a61b-87cf37a844ed)

## 3. Insert de usuario y roles

En el archivo import.sql se adiciona los scripts para insertar roles, usuarios, usuarios y roles. Esto a que es una relación muchos a muchos

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/52fdd256-c60e-4cf8-8e36-7b0f383dd574)
