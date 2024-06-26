# Crear cliente


```mermaid
flowchart LR
    A[ComponentForm]-->C[form.component.ts]
    A-->D[form.component.html]
    A-->E[form.component.css]
    F[cliente.service.ts]:::someclass-->A
    classDef someclass fill:#f96
    G[app.module.]:::someclass1-->A
    classDef someclass1 fill:#33FF39
    H[app-routing-module]:::someclass1-->A
    classDef someclass1 fill:#33FF39 

```

El formulario para crear un cliente es un componente **form**. Todo componente tiene tres archivos: **ts**,**css** y **html**. Por otra parte, se tiene un clase que nos proporciona los servicios **cliente.service.ts** para consumir los **api's** del **backend**.

<br>

## 1. Componente form, formulario cliente

En este apartado se va crear el **componente form**, para la creación y actualización de clientes. Antes de iniciar se debe importar el **FormsModule (ngModel)** o **ReactiveFormsModule** en el **app.module** de su proyecto

![image](https://user-images.githubusercontent.com/31961588/167023791-455618b3-a761-41dc-9cda-badf03dd532d.png)

<br>

#### 1.1 Crear componente form

Se crea el componente form que va tener el formulario para la creación y actulización de clientes.

![image](https://user-images.githubusercontent.com/31961588/166971616-971546c2-3023-4f2e-9680-408f3b9f85fa.png)

<br>

#### 1.2 Librerias para form.component.ts 

En **Form.component.ts** se necesita las siguiente librerias para crear y actualizar un cliente en el formulario, por lo tanto se debe importar.

![image](https://user-images.githubusercontent.com/31961588/166972576-48537fa7-88e4-4c00-a329-e6c1918f8fa7.png)

<br>

#### 1.3 Atributos y constructor clase form.component.ts

![image](https://user-images.githubusercontent.com/31961588/166973780-cc4c8a6e-a679-4a94-ab6d-65098cd3847d.png)

<br>

#### 1.3 Método listado de regiones 

<br>

##### 1.3.1 Servicio getRegiones 

La interfaz region en **cliente.service.ts** se debe importar, ya que ahí se va construir un servicio que proporciona el listado de regiones

![image](https://user-images.githubusercontent.com/31961588/166974654-6ae4b98b-f6bb-4df0-a4a6-f863616df33b.png)


<details><summary>Mostrar código</summary>
<p>
  
```typescript
import { Region } from './region';

```
</p>
</details>

<br>

Definimos el método **getRegiones** en  **cliente.service.ts**, dicho servicio es **get**, el cual, llama al contrallador clientes e invoca el endpoint **/cliente/regiones**, que retorna el listado de todas la regiones desde la base de datos. . 

![image](https://user-images.githubusercontent.com/31961588/166975145-b758168a-1ab7-4d97-8605-571fdf74c53d.png)


<details><summary>Mostrar código</summary>
<p>

```typeScript
  getRegiones(): Observable<Region[]> {
    return this.http.get<Region[]>(this.urlApi + '/clientes/regiones');
  }
```


</p>
</details>

<br>


##### 1.3.2 Método getRegiones en el form.component.ts

En el componente del form, definimos un metodo que, traiga el back todas la regiones y las guarde en la lista regiones, este método se debe ejecutar cada vez que se carga el componente form.

En el componente **form**, se define un método que consume el servició anteriormente creado que traer del **api** la lista de regiones. Este método se debe ejecutar cada vez que termina de carga el componente, especificamente en el método **OnInit()** del ciclo de vida de **Angular**

![image](https://user-images.githubusercontent.com/31961588/166976252-7518cc50-d197-4400-b7eb-9036c10bee4a.png)

<br>

##### 1.3.4 Método crearCliente  cliente.service 

Se crea en el **cliente.service.ts** el método **create** que hace una petición post al back pasandole el objeto **cliente**. Se importa map,catchError , y tap


![image](https://user-images.githubusercontent.com/31961588/166978585-50de134c-4fb8-49e2-9bfe-f7f428572b9c.png)

<br>

**Método create cliente en el cliente.service** 

![image](https://user-images.githubusercontent.com/31961588/166979219-d41c5495-cdfe-4b10-b99c-12812c817aae.png)

<br>

##### 1.3.5 Método create en form.component.ts

![image](https://user-images.githubusercontent.com/31961588/167016136-4d7b99b1-affb-4e73-aad2-4f1924eb5927.png)

<br>

#### 1.4 Formulario html crear cliente

![image](https://user-images.githubusercontent.com/31961588/167025560-27827ddb-5b64-4681-812d-8bb84c57cf08.png)

![image](https://user-images.githubusercontent.com/31961588/167052942-3d66395e-1e76-4be4-9792-e897fe9f8bb0.png)

<br>

#### 1.5 Botón crear en la tabla clientes

En **cliente.component.html**

![image](https://user-images.githubusercontent.com/31961588/167031005-12cb0976-821b-4857-949d-1bb793e0aeea.png)

<details><summary>Mostrar código</summary>
<p>

```Html
 <div class="my-2 text-left">
         <button type="button" routerLink='/clientes/form' class="btn btn-success">Crear</button>       
      </div>
```
<br>
</p>

</details>

<br>

#### 1.6 Configurar path en **app-routing.module.ts**

![image](https://user-images.githubusercontent.com/31961588/167031216-63895837-e2fb-4e9c-8e6f-200f87446a42.png)

<details><summary>Mostrar código</summary>
<p>

```TypeScript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { ClienteComponent } from './Cliente/cliente.component';
import { FormComponent } from './Cliente/form.component';

const routes: Routes = [ 
   { path: 'clientes', component: ClienteComponent },
   { path: 'clientes/form', component: FormComponent }
   ];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```
</p>
</details>

<br>
<br>
<br>



# 2 DatePicker

Usar un componte de datePicker de **angular/material** para el formulario de cliente para la fecha.  

### 2.1 Instalación 

Se debe hacer la instalación de **@angular/material** con el siguiente comando

```cmd

ng add @angular/material

```

### 2.2 Importar componetes

En el **app.module** se importa las librerias del **datePicker**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/40e46407-3ec6-49f0-812c-5e0657cd4e06)

### 2.3 Input datePicker

En en el **form.componet.ts** se implenta el **datePicker** de angular/material

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/bc3cb85b-6712-4a36-8ef7-6539a8cbd1b2)

### 2.4 DatePicker - moment

La fecha no la esta mostrando correctamente en el formulario, a pesar que se esta guardando correctamente en la base de datos. Para dar solución a esto se va ha utilizar el **moment-adapter** con el siguiente comandos

```cmd

npm install --save @angular/material-moment-adapter

npm install --save moment

```

Se ajusta el **app.modulo.ts** se cambia el **MatNativeDateModule** por **MatMomentDateModule**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/00a402f6-3fd3-4a2d-9085-1546199fa2d7)




<br>
<br>
<br>

# 3 Código final

En este apartado final, está el código de **form.componen.ts**, **form.componente.html**, **cliente.service.ts**, los cuales le podrán ser de mucha útilidad.

##### 2.1 form.component.ts

<details><summary>Mostrar código</summary>
<p>

```typeScript

import { Component, OnInit } from '@angular/core';
import { Cliente } from '../cliente/cliente';
import { Region }  from '../cliente/region';
import { ClienteService} from 'src/app/Cliente/cliente.service';
import { Router, ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-form',
  templateUrl: './form.component.html',
  styleUrls: ['./form.component.css']
})
export class FormComponent implements OnInit {

  titulo: string="Crear Cliente";
  
  cliente: Cliente={};
  regiones: Region[]=[];  
  errores: string[]=[];

  constructor(private clienteService: ClienteService,
              private router: Router,
              private activatedRouter: ActivatedRoute) { }

  ngOnInit(): void {
    this.getRegiones();
  }

  getRegiones(): void{
    this.clienteService.getRegiones().subscribe(respuesta=>{
      this.regiones=respuesta;
    }
    )
  }

 create(): void {
    this.clienteService.create(this.cliente).subscribe({
      next: (cliente: Cliente) => {
        this.router.navigate(['/clientes']);
      },
      error: (err) => {
        this.errores=[];
        if(err.error.errors){
          this.errores = err.error.errors as string[];
        }else if(err.error.error){
          this.errores.push(err.error.mensaje);
          console.error(err.error.error); 

        }       
        console.error('Código del error desde el backend: ' + err.status);
        
      }
    });
  }



  compararRegion(o1: Region, o2: Region): boolean {
    if (o1 === undefined && o2 === undefined) {
      return true;
    }
    return o1 === null || o2 === null || o1 === undefined || o2 === undefined ? false : o1.id === o2.id;
  }
}

```



</p>
</details>


<br>

#####  2.2 form.componente.html

<details><summary>Mostrar código</summary>
<p>
  
```html

<ul class="alert alert-danger" *ngIf="errores.length > 0">
    <li *ngFor="let err of errores">
      {{ err }}
    </li>
  </ul>
  <div class="card bg-dark text-white my-2"   style="width: 50%; margin: auto auto;"> 
     <div class="card-header">{{titulo}}</div>
     <div class="card-body">
      <form #clienteForm="ngForm">
        <div class="form-group row">
          <label for="nombre" class="col-form-label colm-sm-2">Nombre</label>
           <div class="col-sm-6">            
               <input type="text" class="form-control" [(ngModel)]="cliente.nombre" id="nombre" name="nombre"  required style="width: 500px;">
            </div>
        </div>
        <div class="form-group row">
          <label for="apellido" class="col-form-label colm-sm-2">Apellido</label>
           <div class="col-sm-6"> 
             <input type="text" class="form-control" [(ngModel)]="cliente.apellido" name="apellido"  required style="width: 500px;">            
           </div>
        </div>     
        <div class="form-group row">
          <label for="email" class="col-form-label colm-sm-2">Email</label>
           <div class="col-sm-6">            
            <input type="email" class="form-control" [(ngModel)]="cliente.email" name="email"  required style="width: 500px;">          
           </div>
        </div>

        <div class="form-group row">
          <label for="createAt" class="col-form-label colm-sm-2">Fecha</label>
           <div class="col-sm-6">   
            <input [matDatepicker]="miDatepicker" class="form-control" [(ngModel)]="cliente.createAt" name="createAt"  style="display:inline; width:200px;" required>
            <mat-datepicker-toggle matSuffix [for]="miDatepicker"  matDatepickerTogglePosition="end"></mat-datepicker-toggle>            
            <mat-datepicker #miDatepicker></mat-datepicker> 
          </div>
        </div>    
        
       
        
        
  
        <div class="form-group row">
          <label for="region" class="col-form-label colm-sm-2">Región</label>
           <div class="col-sm-6">            
               <select [compareWith]="compararRegion" class="form-control" [(ngModel)]="cliente.region" name="region" style="width: 500px;">
                 <option [ngValue]="undefined">---Seleccionar una región----</option>
                 <option *ngFor="let region of regiones" [ngValue]="region">{{region.nombre}}</option>              
               </select>
           </div>
        </div>
       
        
        <div class="form-group my-3 row">
          <div class="col-sm-6">
            <button class="btn btn-primary " role="button" (click)='create()' [disabled]="!clienteForm.form.valid">Crear</button>
            <button class="btn btn-danger m-2"  role="button" routerLink='/clientes'>Cancelar</button>
          </div>
        </div>
      </form>
  
     </div>  
  </div>



```
</p>
</details>

<br>

##### 2.3 cliente.service.ts

<details><summary>Mostrar código</summary>
<p>


```typeScript
import { Injectable } from '@angular/core';
import { HttpClient, HttpRequest, HttpEvent,HttpHeaders } from '@angular/common/http';
import { environment } from 'src/environments/environment';
import { Observable, throwError } from 'rxjs';
import { map, catchError, tap } from 'rxjs/operators';
import { Cliente } from './cliente';
import { Region } from './region'

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

  getRegiones(): Observable<Region[]> {
    return this.http.get<Region[]>(this.urlApi + '/clientes/regiones');
  }

  create(cliente: Cliente): Observable<Cliente>{
    return this.http.post<Cliente>(`${this.urlApi}/clientes`, cliente).pipe(
       map((response: any)=> response.cliente as Cliente),
       catchError(e=>{
         if(e.status==400){
           return throwError(()=>e);
         }
         if(e.errors.mensaje){
           console.log(e.errors.mensaje);
         } 
         return throwError(()=>e);
       })
    );
  }

}

```
</p>
</details>

<br>

##### 2.4 app.module.ts

<details><summary>Mostrar código</summary>
<p>


```typeScript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClientModule } from '@angular/common/http';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { HeaderComponent } from './header/header.component';
import { ClienteComponent } from './cliente/cliente.component';
import { FormComponent } from './cliente/form.component';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import {MatDatepickerModule} from '@angular/material/datepicker';
import {MatInputModule} from '@angular/material/input';
import {MatFormFieldModule} from '@angular/material/form-field';
import {MatNativeDateModule} from '@angular/material/core';


@NgModule({
  declarations: [
    AppComponent,
    HeaderComponent,
    ClienteComponent,
    FormComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,
    FormsModule,
    ReactiveFormsModule,
    BrowserAnimationsModule,
    MatDatepickerModule,
    MatInputModule,
    MatFormFieldModule,
    MatNativeDateModule
    
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }


```
</p>
</details>
