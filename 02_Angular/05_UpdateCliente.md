# Actualizar cliente

<br>
<br>

## 1. GetCliente por Id

Es necesario tener un método que traiga la información del cliente desde el back para llenar el formulario con los datos del cliente y sobre ellos modificar los
campos necesarios. Recuerde que se debe crear un servicio en **cliente.service.ts** que trae un **observable** y este método se va llamar desde el **form.component.ts**

Antes se declara el router para usarlo en el método getCliente, esto va permitir reenviar al componente cliente una vez trae el cliente del back

<br>

#### 1.1 Importar Router

![image](https://user-images.githubusercontent.com/31961588/167054250-5f66079f-073e-4c6e-a9ce-a797799ee9ab.png)

<br>

#### 1.2 Método getCliente.

![image](https://user-images.githubusercontent.com/31961588/167054156-536f0f32-75fe-4bf0-9610-4d4d3d183901.png)

<br>
<br>
<br>

## 2. Update cliente 

En **cliente.service.ts** se crea un método **update** cliente, el cual, comsume el **api** que actuliza el cliente en la base de dato. 

<br>

![image](https://user-images.githubusercontent.com/31961588/167055487-067ab694-a453-44c7-956a-d347d1157d6f.png)

<br>
<br>
<br>

## 3. Update cliente form.component.ts

En el **form.compoente.ts** se crea un méto **update** cliente para que sea llamado desde el botón guarda. 

![image](https://user-images.githubusercontent.com/31961588/167056018-629c315d-a082-4993-b516-2afbe4e90ba2.png)

<br>
<br>
<br>

## 4. Botón de editar cliente y path  

### 4.1 Configuración app-routing.module.ts

![image](https://user-images.githubusercontent.com/31961588/167056922-85916b46-6952-400f-afa3-7aa46c5209a9.png)

<br>
<br>
<br>

### 4.2 Botón editar cliente en cliente.component.html

![image](https://user-images.githubusercontent.com/31961588/167057207-0b2b88e4-b4a1-4bae-9065-6937c4e30d9d.png)

<br>
<br>
<br>

### 4.3 Obtener cliente en formulario

Obtener un cliente al cargar un formulario desde el botón actulizar. 

![image](https://user-images.githubusercontent.com/31961588/167057830-3c644bc7-320b-477a-af52-6d207e4ca0a7.png)

<br>

![image](https://user-images.githubusercontent.com/31961588/167058376-42ed0348-4391-468a-a8df-f07a9143faf9.png)

<br>

![image](https://user-images.githubusercontent.com/31961588/167058449-a7fe7657-ce8d-4b39-a732-c45be2b4dced.png)






