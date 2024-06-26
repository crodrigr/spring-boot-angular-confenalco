# List clientes

Se va crear un componente que muestre el listado de los cliente. 

## 1. Directorio para el componente cliente

Se crea un directorio **cliente** dentro **src** para construir el componente cliente, el cual, tendra toda la funcionalidad del **crud** del cliente: **listar**, **crear**, **actulizar** y **eliminar**

<br>



![image](https://user-images.githubusercontent.com/31961588/166582863-03158336-c664-42d2-be8e-75bfe80d3ebd.png)

<br>
<br>
<br>
<br>




## 2. Componente cliente

Con el comando **ng g component cliente --flat** se crea el componente de cliente que cuenta de cuatro archivos: .html, .ts, css. spec.ts 

<br>

![image](https://user-images.githubusercontent.com/31961588/166586712-f4aed45b-6996-41c3-a8ca-7d6b106c6f16.png)

Archivos que se crearon

<br>

![image](https://user-images.githubusercontent.com/31961588/166586927-dde0ca3b-eb55-4bc7-8b5a-7904c96c4d4a.png)
<br>
<br>
<br>
<br>

## 3. Modelos de cliente. 

En la parte del front vamos necesitar crear el tipo de dato clientes y regiones. Hay dos maneras: clase o interfaz. Se usa clase cuando vayamos a instanciar objetos a traves del operador new, e interfaz en caso contrario. En nuestro caso lo vamos hacer con interfaz por que tomamos la data desde el back. 

#### 3.1 Interfaz region

Primero se crea la interfaz **region**, que no tiene dependencia como **cliente** que depende de ella. 

<br>

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/bdddec82-4d3a-4e8a-b23d-744ce844df98)


Definimos los atributos de región que son los mismo atributos que la clase region del back.

<details><summary>Mostrar código</summary>
<p>


```TypeScript
export interface Region{
    id?: number;
    nombre?: string;
}
```

</p>
</details>

#### 3.2 Interfaz cliente

La interfaz **Cliente** es un espejo de la clase entity **Cliente** del **backend**, las cuales, se debe corresponder por que sus atributos de relacionan uno con el otro. 

<br>

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/a41fc0aa-ad40-4c88-bbf5-450453a2e304)

<details><summary>Mostrar código</summary>
<p>


```typescript
   import {Region} from './region';

export interface Cliente{
    id?: number;
    nombre?: string;
    apellido?: string;
    createAt?: string;
    email?: string;
    region?: Region; 
   

}
```

</p>
</details>
<br>
<br>
<br>
<br>

## 4. Crear servicio de cliente

Un servicio en angular es una clase que consumen los servicios del backed. Una clase de **service** aplica inyección de dependencia. Para crear una clase de servicio se hace a través del comando **ng g service cliente** . Crea dos archivos **cliente.service.ts** y **cliente.service.spec.ts**, este último no lo vamos a usar por que es para programar pruebas automáticas. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166608399-252d5768-76f6-40e8-aaf2-9c92369717c4.png)

Se observa que tiene decorador **@Injectable**, por lo tanto, usa inyección de dependencias, esto permite que se pueda usar desde cualquier componente. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166608638-0c88ae2a-e3ee-423b-873f-0a3ead5e1666.png)

#### 4.1 Configuración path del back del Enviroment 

Esta es una variable de entorno vamos a configurar con la path del backend. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166608812-77c55f5f-91a0-483e-bd16-5cc6b51d005d.png)

#### 4.2 HttpClient

El httpClient me permite hacer peticiones http: get, post, delete, push, en este caso se van hacer a nuestro backend. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166609142-5b31f255-530a-4c23-a64e-eed8b15960de.png)


HttpRequest,HttpEvent y HttpHeaders se importa para el manejo de los headers y request. 

**App.module.ts**

Se debe agregar en **HttpClientModule** en **app.module.ts** para que se pueda usar el **HttpClient** en el service.

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/9a658197-3b2e-41c9-ba6f-c2156cf196c7)


<br>

#### 4.3 Definimos el metodo constructor

<br>

![image](https://user-images.githubusercontent.com/31961588/166609660-31539a53-266e-4eaa-8a03-f2bbc8aa1516.png)


#### 4.4 Método getClientes

Definimos el metodo getClientes, el cual, va hacer una petición get al back para traer todos los clientes que tenemos registrados en nuestra base de datos. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166610288-b60a0fb2-add1-4dfb-9942-7ad81e75094c.png)


<details><summary>Mostrar código</summary>
<p>


```typescript
import { Injectable } from '@angular/core';
import { HttpClient, HttpRequest, HttpEvent,HttpHeaders } from '@angular/common/http';
import { environment } from '../../environments/environment';
import { Observable, throwError } from 'rxjs';
import { Cliente } from './cliente';

@Injectable({
  providedIn: 'root'
})
export class ClienteService {

  private urlApi: string ="";

  constructor(private http: HttpClient){
     this.urlApi = environment.apiUrl+'/api';
   }

  getClientes(): Observable<Cliente[]> {
    return this.http.get<Cliente[]>(this.urlApi + '/clientes');
  }
}
```

</p>
</details>

<br>
<br>
<br>
<br>


## 5. Crear una table que muestre el listado de clientes

#### 5.1 cliente.component.ts

El cliente.component.ts se define la lógica del componente, en este caso, los métodos que vamos a usar para llamar al backend para traer todos los registros de nuestros clientes y mostrarlos en nuestra tabla de clientes. 

<br>

![image](https://user-images.githubusercontent.com/31961588/166611612-030a1146-efd5-4c32-b990-6d5162a4778e.png)


<details><summary>Mostrar código</summary>
<p>


```typescript
  
import { Component, OnInit } from '@angular/core';
import { ClienteService } from './cliente.service';
import { Cliente } from './cliente';

@Component({
  selector: 'app-cliente',
  templateUrl: './cliente.component.html',
  styleUrls: ['./cliente.component.css']
})
export class ClienteComponent implements OnInit {

  title = 'Cliente';     
  clientes: Cliente[]=[];

  constructor(private clienteService: ClienteService) { }

  ngOnInit(): void {
    this.getClientes();
  }

  getClientes(): void{    
    this.clienteService.getClientes().subscribe(response => {
       this.clientes = response; 
    });


  }

}

```

</p>
</details>





#### 5.2 cliente.component.html

<br>

![image](https://user-images.githubusercontent.com/31961588/166612680-976a55c6-058d-4070-b1ae-f065c942ed50.png)

<br>

![image](https://user-images.githubusercontent.com/31961588/166612745-442691b0-7bbb-4a0e-8dee-a42405e4ed6b.png)


<details><summary>Mostrar código cliente.componente.html</summary>
<p>


```html
  <div class="card border-primary mb3">
    <div class="card-header">Clientes</div>
    <div class="card-body text-primary">
       <h5 class="card-title">Listado de clientes</h5>
      <div class="my-2 text-left">       
      </div>
      <div *ngIf="clientes?.length==0" class="alert alert-info">
       No hay registros en la base de datos!
      </div>
      <table class="table table-border table-hover text-primary">
        <thead>
           <tr>
              <th></th>
              <th>#</th>
              <th>Nombre</th>
              <th>Apellido</th>
              <th>Email</th>
              <th>Fecha</th>
              <th>Crear factura</th>
              <th>Actualizar</th>
              <th>Eliminar</th>
           </tr>
        </thead>
        <tbody>      
            <tr *ngFor="let cliente of clientes">
            <td><button type="button" class="btn btn-info" >Ver</button></td>
            <td>{{cliente.id}}</td>
            <td>{{cliente.nombre}}</td>
            <td>{{cliente.apellido}}</td>
            <td>{{cliente.email}}</td>
            <td>{{cliente.createAt}}</td>
            <td><button type="button" class="btn btn-secondary"  >Crear factura</button></td>
            <td><button type="button" class="btn btn-success" >Actualizar</button></td>
            <td><button type="button" class="btn btn-danger" >Elminar</button></td>
           </tr>
        </tbody>
      </table>
      
    </div>
    </div>
```

</p>
</details>






#### 5.3 Configurar routing y app.module
<br>
![image](https://user-images.githubusercontent.com/31961588/166614536-0468932a-998f-4824-8834-a6c9897b6603.png)

<details><summary>Mostrar código app.module</summary>
<p>


```typescript
 import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClient } from '@angular/common/http';
import { HttpClientModule } from '@angular/common/http';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { HeaderComponent } from './header/header.component';
import { ClienteComponent } from './cliente/cliente.component';

@NgModule({
  declarations: [
    AppComponent,
    HeaderComponent,
    ClienteComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule 
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

</p>
</details>


<br>

![image](https://user-images.githubusercontent.com/31961588/166614577-313848e4-3b2f-4bdb-ab42-db3235a8d715.png)

<details><summary>Mostrar código app-routing.module.ts</summary>
<p>



```TypeScript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { ClienteComponent} from '../app/cliente/cliente.component'

const routes: Routes = [ 
  { path: 'clientes', component: ClienteComponent }
  ];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

</p>
</details>

#### 5.4 Cargando el listado del cliente

<br>

![image](https://user-images.githubusercontent.com/31961588/166614790-35746e68-648c-48f2-8ee6-cd2b536a62c9.png)
