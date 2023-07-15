# Elminar cliente

<br>
<br>

## 1. Delete cliente.service.ts

Crear el método delete en **cliente.service.ts**. Este método consume del **api** delete que borra un cliente de la base de datos.

![image](https://user-images.githubusercontent.com/31961588/167059473-2ecb6524-d6a4-483f-9058-890354d247ed.png)

<br>
<br>
<br>
<br>

## 2.Delete  cliente.component.ts

 Crear el método delete en el **cliente.component.ts**, por que desde la tabla de clientes se va tener un botón de elminar cliente, que toma el id del cliente y llama a este método que asu vez llama a método delete del **cliente.service**

![image](https://user-images.githubusercontent.com/31961588/167059864-4ec8dc51-5f88-40d0-9672-ce40d0a34579.png)


## 3. Crear el botón delete en cliente.component.html

![image](https://user-images.githubusercontent.com/31961588/167059924-02aa9241-c6a4-472b-bf59-8bf1c1c53ef1.png)



## Error

![image](https://user-images.githubusercontent.com/31961588/167060267-1ec92350-84eb-432a-b6cd-fbf4da4f6cf5.png)

Modifcamos el tsconfig.json el strict lo colocamos en false

![image](https://user-images.githubusercontent.com/31961588/167060381-7ec7816f-7ef3-41e3-b2d1-00ea092ff721.png)


