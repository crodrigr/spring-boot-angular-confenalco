# Crear el componente header 

Antes de iniciar con la construcción de nuestra aplicación web se va hacer la instalación de **Boostrap**. Este **Framework** de **css** nos va ayudar con los estilos. 



## 1. Instalación de Boostrap

**Boostrap** tiene varias formas de instalar. En este caso lo vamos hacer por medio de **CDN**. En la pagina oficial de **Boostrap** están las instrucciones. 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/595086d3-7b36-49da-b555-aeb8b7bf345a)

En el **index.html** colocamos los **scripts** de **boostrap** y de los icon.

#### 1.2 Los scripts CDN

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/d7cb1073-34e7-4ee5-b908-942193424e75)

<details><summary>Mostrar código</summary>
<p>

**Codigo de index.html**

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>AppInvoice</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
  <link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
</head>
<body>
  <app-root></app-root>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-geWF76RCwLtnZ8qwWowPQNguL3RmwHVBC9FhGdlKrxdiJJigb/j/68SIy3Te4Bkz" crossorigin="anonymous"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.min.js" integrity="sha384-fbbOQedDUMZZ5KreZpsbe1LCZPVmfTnH7ois6mU1QK+m14rQ1l2bGBq41eYeM/fS" crossorigin="anonymous"></script>
</body>
</html>
```

</p>
</details>

## 2. Estilos globales

En el archivos **styles.css** se configura los estilos globales, es decir, acá se define los estilos que aplican para toda la aplicación. Cada **componente** tiene su propio archivo de **css**

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/5e710b0b-2644-4e1b-a9d4-be19237807e2)

<details><summary>Mostrar código</summary>
<p>

**Styles.css**

```css
  /* You can add global styles to this file, and also import other style files */

html, body { height: 100%; }
body { margin: 0; font-family: Roboto, "Helvetica Neue", sans-serif; }
```

</p>
</details>

## 3. Probar estilos

Angular se basa en componentes, y el componente por defecto que tiene todo proyecto es el **app.componente**, entonces en el archivo **app.component.html** borramos todo y colocamos **Hola mundo** 

#### 3.1 Hola mundo 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/269c5509-ebd3-422e-af63-44ffb2149a8b)

#### 3.2 Visualizar 

![image](https://github.com/crodrigr/spring-boot-angular-confenalco/assets/31961588/878596e2-6583-41a8-b162-3c5b6e465975)

## 4. Crear componente header

![image](https://user-images.githubusercontent.com/31961588/164358080-d3ec885d-1ac7-4fdf-ac94-46511bbad1f7.png)

En la terminal del directorio creado **header** y a través del comando **ng generate component header** se crea el componente header. El **--flat** es para que no cree un directorio header, no es necesario, se hizo de forma manual y ya esta creado, si no se coloca el **--flat** se creara el header dentro de otro directorio header

![image](https://user-images.githubusercontent.com/31961588/164358535-867a652b-25e6-4b83-af2f-6a7580f0f512.png)

Se crean tres archivos: header.component.html, header.component.spec.ts, header.component.ts, header.component.css y actuliza el app.module.ts. Un **componente** en angular tiene estos cuatro archivos por defecto. Y todo componente debe estar registrado en el **app.modules.ts**

![image](https://user-images.githubusercontent.com/31961588/164358790-e8b3fa19-17bd-4a8a-8537-3823f5091bcd.png)

## 5. Nav bar en el header

Se busca un ejemplo de un nav bar en boostrap y lo copiamos

![image](https://user-images.githubusercontent.com/31961588/164359439-5deb4691-3578-41a2-b1e6-d16600afd9b9.png)

![image](https://user-images.githubusercontent.com/31961588/164359638-2f4c7bf2-4868-4122-8e98-e4b918d79530.png)

<details><summary>Mostrar código</summary>
<p>


```html
   <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">Disabled</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
```
</p>
</details>


## 6 Implentar el header

En **app.componente.html** se hace la implementación del componente **header** a través del **selector**
  
  ![image](https://user-images.githubusercontent.com/31961588/164360228-0f8961fc-d3bd-46ec-8a9b-0874d2480999.png)

  ![image](https://user-images.githubusercontent.com/31961588/164360297-e3130834-7a91-4f9a-8dbc-e651988c5bf4.png)

<details><summary>Mostrar código</summary>
<p>


```Typescript
  <app-header></app-header>
<div class="container">
  <router-outlet></router-outlet>
</div>
```

</p>
</details>


