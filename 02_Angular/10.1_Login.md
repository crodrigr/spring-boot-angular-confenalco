# Modulo de autenticación de usuarion en el front.


<br>
<br>

## 1. Se crea el directorio usuario

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171073600-d37ab714-88fd-4f11-86fd-c23e797511f0.png)

## 2. Se crea la clase usuario.ts

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171073721-9c4c8361-8436-4bc2-819e-ed717dea6f0a.png)

<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript
export class Usuario {
    id: number;
    username: string;
    password: string;
    nombre: string;
    apellido: string;
    email: string;
    roles: string[]=[];    
  }
```

</p>
</details>

<br>
<br>

## 3. Se crea el servicio auth.service.ts

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171073953-ea48ebc5-35f3-4b4d-ae89-e4b6ffb992d3.png)

<br>
<br>

## 4. Importar las librerias necesarias del auth.services.ts

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171074065-c95e5f97-1a36-4318-8f5a-213f170a0f81.png)


<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript

import { Observable } from 'rxjs';
import { HttpClient, HttpHeaders } from '@angular/common/http';
import { Usuario } from './usuario';
import { environment } from 'src/environments/environment';

```

</p>
</details>

<br>
<br>

## 5. Definimos las siguientes variables

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171074207-2271099a-57bc-4073-8d13-1d4d7f7c7f15.png)


<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript
  private _usuario: Usuario;
  private _token: string
```

</p>
</details>

<br>
<br>

## 6. Inyección de dependencia del HttpCliente y se crea el método login

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171074366-132d025d-13fc-47b6-9e8e-1a3d7fbf0809.png)

<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript

constructor(private http: HttpClient) { 
  }

 login(usuario: Usuario): Observable<any> {
    const urlEndpoint = environment.apiUrl+'/oauth/token';

    const credenciales = btoa('angularapp' + ':' + '12345');

    const httpHeaders = new HttpHeaders({
      'Content-Type': 'application/x-www-form-urlencoded',
      'Authorization': 'Basic ' + credenciales
    });

    let params = new URLSearchParams();
    params.set('grant_type', 'password');
    params.set('username', usuario.username);
    params.set('password', usuario.password);
    console.log(params.toString());
    return this.http.post<any>(urlEndpoint, params.toString(), { headers: httpHeaders });
  }

```

</p>
</details>

<br>
<br>

## 7. Se crea los métodos obtenerDatos y guardarUsuario

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171074669-17b0f65c-b461-4f01-acc1-acac575f3b94.png)

<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript
obtenerDatosToken(accessToken: string): any {
    if (accessToken != null) {
      return JSON.parse(atob(accessToken.split(".")[1]));
    }
    return null;
  }


  guardarUsuario(accessToken: string): void {
    let payload = this.obtenerDatosToken(accessToken);
    this._usuario = new Usuario();
    this._usuario.nombre = payload.nombre;
    this._usuario.apellido = payload.apellido;
    this._usuario.email = payload.email;
    this._usuario.username = payload.user_name;
    this._usuario.roles = payload.authorities;
    sessionStorage.setItem('usuario', JSON.stringify(this._usuario));
  }



```

</p>
</details>

<br>
<br>



## 8. Se crean los metodos getUsuario y getTokent

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171076194-f8d35322-7256-420f-9789-434487f25df5.png)

**Código usurio.ts**
```TypeScript
export class Usuario {
    id: number;
    username: string;
    password: string;
    nombre: string;
    apellido: string;
    email: string;
    roles: string[]=[];

    
  }
```

## 9. Se crean los métodos guardarToken, isAuthenticated, hasRole, logout

<br>
<br>

![image](https://user-images.githubusercontent.com/31961588/171075920-9e50511b-8176-4a6b-a4da-43442de0882b.png)


<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript
 public get usuario(): Usuario {
    if (this._usuario != null) {
      return this._usuario;
    } else if (this._usuario == null && sessionStorage.getItem('usuario') != null) {
      this._usuario = JSON.parse(sessionStorage.getItem('usuario')) as Usuario;
      return this._usuario;
    }
    return new Usuario();
  }
  
  public get token(): string {
    if (this._token != null) {
      return this._token;
    } else if (this._token == null && sessionStorage.getItem('token') != null) {
      this._token = sessionStorage.getItem('token');
      return this._token;
    }
    return null;
  }


  guardarToken(accessToken: string): void {
    this._token = accessToken;
    sessionStorage.setItem('token', accessToken);
  }

  isAuthenticated(): boolean {
    let payload = this.obtenerDatosToken(this.token);
    if (payload != null && payload.user_name && payload.user_name.length > 0) {
      return true;
    }
    return false;
  }

  hasRole(role: string): boolean {
    if (this.usuario.roles.includes(role)) {
      return true;
    }
    return false;
  }
  
  logout(): void {
    this._token = null;
    this._usuario = null;
    sessionStorage.clear();
    
  }



```

</p>
</details>

<br>
<br>

## 10 Codigo

<br>
<br>

<details><summary>Mostrar código</summary>

<p>   
    
```TypeScript

import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import { HttpClient, HttpHeaders } from '@angular/common/http';
import { Usuario } from './usuario';
import { environment } from 'src/environments/environment';

@Injectable({
  providedIn: 'root'
})
export class AuthService {

  private _usuario: Usuario;
  private _token: string

  constructor(private http: HttpClient) { 
  }

  login(usuario: Usuario): Observable<any> {
    const urlEndpoint = environment.apiUrl+'/oauth/token';

    const credenciales = btoa('angularapp' + ':' + '12345');

    const httpHeaders = new HttpHeaders({
      'Content-Type': 'application/x-www-form-urlencoded',
      'Authorization': 'Basic ' + credenciales
    });

    let params = new URLSearchParams();
    params.set('grant_type', 'password');
    params.set('username', usuario.username);
    params.set('password', usuario.password);
    console.log(params.toString());
    return this.http.post<any>(urlEndpoint, params.toString(), { headers: httpHeaders });
  }

  obtenerDatosToken(accessToken: string): any {
    if (accessToken != null) {
      return JSON.parse(atob(accessToken.split(".")[1]));
    }
    return null;
  }


  guardarUsuario(accessToken: string): void {
    let payload = this.obtenerDatosToken(accessToken);
    this._usuario = new Usuario();
    this._usuario.nombre = payload.nombre;
    this._usuario.apellido = payload.apellido;
    this._usuario.email = payload.email;
    this._usuario.username = payload.user_name;
    this._usuario.roles = payload.authorities;
    sessionStorage.setItem('usuario', JSON.stringify(this._usuario));
  }

  public get usuario(): Usuario {
    if (this._usuario != null) {
      return this._usuario;
    } else if (this._usuario == null && sessionStorage.getItem('usuario') != null) {
      this._usuario = JSON.parse(sessionStorage.getItem('usuario')) as Usuario;
      return this._usuario;
    }
    return new Usuario();
  }
  
  public get token(): string {
    if (this._token != null) {
      return this._token;
    } else if (this._token == null && sessionStorage.getItem('token') != null) {
      this._token = sessionStorage.getItem('token');
      return this._token;
    }
    return null;
  }


  guardarToken(accessToken: string): void {
    this._token = accessToken;
    sessionStorage.setItem('token', accessToken);
  }

  isAuthenticated(): boolean {
    let payload = this.obtenerDatosToken(this.token);
    if (payload != null && payload.user_name && payload.user_name.length > 0) {
      return true;
    }
    return false;
  }

  hasRole(role: string): boolean {
    if (this.usuario.roles.includes(role)) {
      return true;
    }
    return false;
  }
  
  logout(): void {
    this._token = null;
    this._usuario = null;
    sessionStorage.clear();
    
  }





}


```

</p>
</details>
