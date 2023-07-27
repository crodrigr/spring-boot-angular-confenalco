# Módulo para crear la factura

```mermaid
flowchart LR
    A[ComponentFactura]-->C[factura.component.ts]
    A-->D[factura.component.html]
    A-->E[factura.component.css]
    A-->G[Models]
    G-->H[Producto.ts]
    G-->J[ItemFactura.ts]
    G-->I[Factura.ts]
    A-->M[Services]
    M-->S[factura.servies.ts]
    Z[app.module.]:::someclass1-->A
    classDef someclass1 fill:#33FF39
    X[app-routing-module]:::someclass1-->A
    classDef someclass1 fill:#33FF39 

```

## 1. Componentes de modulo de factura

Crear el directorio para los componentes de modulo de factura

<br>

### 1.1 Directorio de facturas

![image](https://user-images.githubusercontent.com/31961588/168698817-655be536-dc8e-45f0-8e7b-d337a5886505.png)

<br>
<br>
<br>
<br>

## 2. Modelos de facturas


Se crea los modelos del módulo de facturas, el cual, debe ser un espejo al modelo que está definido en el backend.  Los modelos se agrupan dentro del directorio **models** que esta dentro de **factura**.

<br>

#### 2.1 Clase producto

![image](https://user-images.githubusercontent.com/31961588/168699078-b91944a5-4f73-4170-b2e6-b890d4a631ea.png)

<br>

<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript
export class Producto {
    id: number;
    nombre: string;
    precio: number;
  }
```

</p>
</details>

<br>

#### 2.2 Clase item-producto

![image](https://user-images.githubusercontent.com/31961588/168699435-9315a172-c61d-4077-80ec-92319fa80e86.png)

<details><summary>Mostrar código</summary>
<p>

```TypeScript
import { Producto } from './producto';

export class ItemFactura {
  producto: Producto;
  cantidad: number = 1;
  importe: number;

  public calcularImporte(): number {
    return this.cantidad * this.producto.precio;
  }
}
```
</p>
</details>


<br>

#### 2.3  Clase factura

![image](https://user-images.githubusercontent.com/31961588/168699564-00e4af0e-838b-4b48-b821-0c35dcc4f448.png)

<details><summary>Mostrar código</summary>
<p>


```TypeScript
import { ItemFactura } from './item-factura';
import { Cliente } from '../../cliente/cliente';

export class Factura {
  id: number;
  descripcion: string;
  observacion: string;
  items: Array<ItemFactura> = [];
  cliente: Cliente;
  total: number;
  createAt: string;

  calcularGranTotal(): number {
    this.total =0 ;
    this.items.forEach((item: ItemFactura) => {
      this.total += item.calcularImporte();
    });
    return this.total;
  }


}
```
</p>
</details>

<br>
<br>
<br>

## 3  Directorio service

Dentro del directorio factura se crea un directorio **service**

![image](https://user-images.githubusercontent.com/31961588/168700317-5684997a-6487-4364-99fc-3436ea9004ff.png)

<br>

#### 3.1  Clase factura.services.ts

![image](https://user-images.githubusercontent.com/31961588/168706744-52e67ee1-8acc-40c7-8d37-568b75dddec6.png)




<br>

#### 2.5 Servicios del modulo de factura

Se define los servicios que se van a llamar al back para modulo de factura

- **getFactura(id: number):** obetner una factura por su id
- **delete(id: number):** eliminar factura por su id
- **create(factura: Factura):** crear factura
- **filtrarProductos(term: string):** filtrar productos por nombre

![image](https://user-images.githubusercontent.com/31961588/168706822-b50f347d-d6f6-4088-9437-a976ff8b2d72.png)

<details><summary>Mostrar código</summary>
<p>


```TypeScript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';
import { Factura } from '../models/factura';
import { Producto } from '../models/producto';
import { environment } from 'src/environments/environment';

@Injectable({
  providedIn: 'root'
})
export class FacturaService {

  private urlApi: string ="";

  constructor(private http: HttpClient) {
     this.urlApi = environment.apiUrl+'/api';
   }

   getFactura(id: number): Observable<Factura> {
    return this.http.get<Factura>(`${this.urlApi}/facturas/${id}`);
  }

  delete(id: number): Observable<void> {
    return this.http.delete<void>(`${this.urlApi}/facturas/${id}`);
  }

  filtrarProductos(term: string): Observable<Producto[]> {
    return this.http.get<Producto[]>(`${this.urlApi}/facturas/filtrar-productos/${term}`);
  }

  create(factura: Factura): Observable<Factura> {
    return this.http.post<Factura>(this.urlApi+'/facturas', factura);
  }


}
```
</p>
</details>

<br>
<br>
<br>

## 4  Factura componente 

Se crea el componente **factura** dentro del directorio de factura. Esto se hace a través del comando **ng g c facturas --flat**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/494feb31-cb21-4ad1-8459-300a3b851bc6)

<br>

### 4.1 Importa  librerias

Se importa las librerias a usar en el componente de **facturas**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/8e7ee2f8-6a88-443c-b017-da3ad21af32c)

<details><summary>Mostrar código</summary>
    
<p>

```typescript
import {FormControl} from '@angular/forms';
import {Observable} from 'rxjs';
import {map, flatMap,startWith} from 'rxjs/operators';
import { Factura } from './models/factura';
import { ClienteService } from  '../cliente/cliente.service'
import { ActivatedRoute, Router } from '@angular/router';
import { FacturaService } from './services/factura.service';
import { Producto } from './models/producto';
import { ItemFactura } from './models/item-factura';
import swal from 'sweetalert2';

```

</p>
</details>

<br>

### 4.2 Definición atributos 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/d275df6f-b83b-4843-aae8-3a84b8e5f531)

<details><summary>Mostrar código</summary>
<p>

```typescript

  titulo: string = 'Nueva Factura';
  factura: Factura = new Factura();
  autocompleteControl = new FormControl();
  productosFiltrados: Observable<Producto[]>;

```

</p>
</details>

<br>

### 4.3 Método constructor

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/db2819f5-fe13-4147-95d4-8e270b56deef)


<details><summary>Mostrar código</summary>
<p>

```typescript

 constructor(private clienteService: ClienteService,
    private facturaService: FacturaService,
    private router: Router,
    private activatedRoute: ActivatedRoute) { 
    
  }

```

</p>
</details>

<br>

### 4.4 Formulario reactivo


<br>

En Angular, `FormControl` es una clase del módulo `@angular/forms` que representa un control de formulario individual en un formulario reactivo. Los formularios reactivos te permiten construir formularios complejos y dinámicos con un mayor control sobre la validación del formulario, el manejo de la entrada del usuario y el envío del formulario.

`FormControl` se utiliza para administrar el estado y la validación de un control de formulario individual, como un campo de entrada, casilla de verificación, botón de opción, etc. Proporciona propiedades y métodos para rastrear y actualizar el valor y el estado de validación del control de formulario.

<details><summary>Ver más</summary>
<p>

Aquí te muestro cómo crear y utilizar un `FormControl` en un componente de Angular:

1. Importa los módulos necesarios en tu componente:

```typescript
import { Component } from '@angular/core';
import { FormControl } from '@angular/forms';
```

2. Crea una nueva instancia de `FormControl` en la clase del componente:

```typescript
@Component({
  selector: 'app-mi-componente',
  templateUrl: './mi-componente.component.html',
})
export class MiComponente {
  miFormControl: FormControl = new FormControl();
}
```

3. Conecta el `FormControl` al control de formulario en el archivo de la plantilla:

```html
<!-- mi-componente.component.html -->
<input [formControl]="miFormControl" type="text" />
```

En este ejemplo, hemos creado un `FormControl` llamado `miFormControl` y lo hemos vinculado a un campo de entrada en la plantilla mediante la directiva de enlace `[formControl]`. Ahora, cualquier cambio realizado en el campo de entrada se reflejará en el `FormControl`, y viceversa.

También puedes establecer un valor inicial para el `FormControl` pasándolo como argumento al crear la instancia:

```typescript
// Estableciendo un valor inicial
miFormControl: FormControl = new FormControl('Valor inicial');
```

Además, `FormControl` proporciona diversos métodos y propiedades para manejar la validación y obtener información sobre el estado del control de formulario. Por ejemplo:

```typescript
// Comprobando la validez del control de formulario
if (this.miFormControl.valid) {
  // El control de formulario es válido
} else {
  // El control de formulario es inválido
}

// Obteniendo el valor actual del control de formulario
const valor = this.miFormControl.value;

// Restableciendo el control de formulario a su estado inicial
this.miFormControl.reset();
```

Con `FormControl`, tienes un mayor control sobre la lógica y la interacción en los formularios de tu aplicación Angular.


<br>

</p>
</details>


### 4.5 Crear factura

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/7f9c26a0-28c9-4cc5-9c57-03fb62cd6603)



<details><summary>Mostrar código</summary>
<p>

```typescript



```

</p>
</details>


![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/7f9c26a0-28c9-4cc5-9c57-03fb62cd6603)



<details><summary>Mostrar código</summary>
<p>

```typescript



```

</p>
</details>




