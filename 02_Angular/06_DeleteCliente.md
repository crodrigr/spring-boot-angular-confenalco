# Elminar cliente

```mermaid
flowchart LR   
    Z[ClienteComponent]-->B[cliente.componente.ts]
    Z-->C[cliente.componente.html]
    Z-->D[cliente.componente.css]
    F[cliente.service.ts]:::someclass-->Z
    classDef someclass fill:#f96
```
 


<br>
<br>

## 1. Delete cliente.service.ts

Crear el método delete en **cliente.service.ts**. Este método consume del **api** delete que borra un cliente de la base de datos.

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/d83d68fe-0908-42d1-8b88-f209156726e9)


<details><summary>Mostrar código</summary>
<p>
 
```typescript
delete(id: number): Observable<any>{
  return this.http.delete<any>(`${this.urlApi}/cliente/${id}`).pipe(
    catchError(e=>{
       if(e.error.mensaje){
         console.error(e.error.mensaje);
       }
       return throwError(()=>e);
    })
  );
}
```
</p>
</details>

<br>
<br>
<br>
<br>

## 2.Delete  cliente.component.ts

 Crear el método delete en el **cliente.component.ts**, por que desde la tabla de clientes se va tener un botón de elminar cliente, que toma el id del cliente y llama a este método que asu vez llama a método delete del **cliente.service**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/d039ffe0-f26e-4113-8020-5e2e86bc3bdd)


<details><summary>Mostrar código</summary>
<p>

```typescript
 delete(cliente: Cliente): void{
   if(cliente.id!=undefined){
    this.clienteService.delete(cliente.id).subscribe({
      next: ()=>{
        this.clientes = this.clientes.filter(cli=>cli!==cliente)
      }
    })
  }  
 }
```
</p>
</details>

<br>
<br>
<br>
<br>

## 3. Botón delete cliente.component.html

![image](https://user-images.githubusercontent.com/31961588/167059924-02aa9241-c6a4-472b-bf59-8bf1c1c53ef1.png)

<details><summary>Mostrar código</summary>
<p>

```typescript

<td><button type="button" (click)='delete(cliente)' class="btn btn-danger" >Elminar</button></td>

```
</p>
</details>

<br>
<br>
<br>
<br>

## Error

![image](https://user-images.githubusercontent.com/31961588/167060267-1ec92350-84eb-432a-b6cd-fbf4da4f6cf5.png)

Modifcamos el tsconfig.json el strict lo colocamos en false

![image](https://user-images.githubusercontent.com/31961588/167060381-7ec7816f-7ef3-41e3-b2d1-00ea092ff721.png)


