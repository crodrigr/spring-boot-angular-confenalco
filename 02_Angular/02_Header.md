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


