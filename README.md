# Talent Fest Laboratoria 2022-1 - Hypatia
![Logo IBM Hypatia](https://i.imgur.com/KoqmDEW.png)


Reto propuesto por la empresa **IBM** y desarrollado por el grupo de frontend developers: 

* [Lizeth Del Rio](https://github.com/Liz-14)
* [Alejandra Arevalo](https://github.com/entarwen7)
* [Jessica Toro](https://github.com/ToroAlejandra)
* [Leidy Acevedo](https://github.com/leidyaJ)
* [Gabriela Paez](https://github.com/gabiinicial)
* [Adriana Soto](https://github.com/adriana17soto)

## Contexto

Hypatia es una plataforma que busca facilitar el proceso de seguimiento en el aprendizaje de los practicantes de IBM, de igual manera, busca facilitar el registro de avance alcanzado diariamente por parte de los aprendices, otorgando una vista general y específica del estado de aprendizaje tanto de los IBMers como de los líderes y supervisores.

## Reto

* La plataforma debe tener un sistema de logueo que debe permitir al usuario líder ingresar y ver lista de aprendices junto a sus MVPs asignados respectivamente.
* La plataforma debe permitir al usuario líder asignar, editar y retirar a un aprendiz de un MVP.
* La plataforma debe permitir ver el avance de un aprendiz en cuanto al porcentaje de formación realizada hasta la fecha respecto a la duración total de horas del path, además de MVPs asignados y demás datos que se mostrarán en el mockup 2.
* Generar y descargar un reporte PDF que evidencie toda la información del punto anterior.


## Reglas Hackathon

El reto se desarrollara en un tiempo maximo de 28 horas.

## Mockups
###### *Mockup 1. Pantalla de inicio de Hypatia para el lider o supervisor*
![mockup 1](https://i.imgur.com/d5hHNFC.png)

###### *Mockup 2. Pdf que se desea obtener.*
![mockup 2](https://i.imgur.com/X068sCI.png)



## Solución

### Herramientas
* [Angular 12](https://angular.io/)
* [Firebase](https://firebase.google.cn/)
* [jsPdf](https://www.npmjs.com/package/jspdf)
* [html2Canvas](https://www.npmjs.com/package/html2canvas)
* [ng circle progress](https://www.npmjs.com/package/ng-circle-progress)
* [Bootwatch](https://bootswatch.com/)

### Componente Login
Haciendo uso de [Firebase Authentication](https://firebase.google.com/products/auth?gclid=CjwKCAiAlrSPBhBaEiwAuLSDUP-apFpcYDuYwedvkDdbZIbOnemM-yn5DtWFhzo2yOTskQy1FkpunRoC3JIQAvD_BwE&gclsrc=aw.ds) se creó el sistema de autenticación por medio de correo y contraseña, además de asignar las credenciales de 'líder' por medio de [Cloud Firestore](https://firebase.google.com/products/firestore?hl=es-419&gclid=CjwKCAiAlrSPBhBaEiwAuLSDUDiuvmBL7N4jPe5wTT36rxeqUBuIBV-9UL-XFp7PE7DtdeLzwvN6vxoCFd0QAvD_BwE&gclsrc=aw.ds)

También se hizo uso de formularios reactivos para el control de errores y validaciones de los inputs del formulario de logueo.

### Componente Learners

Inicialmente se crearon las diferentes colecciones en [Cloud Firestore](https://firebase.google.com/products/firestore?hl=es-419&gclid=CjwKCAiAlrSPBhBaEiwAuLSDUDiuvmBL7N4jPe5wTT36rxeqUBuIBV-9UL-XFp7PE7DtdeLzwvN6vxoCFd0QAvD_BwE&gclsrc=aw.ds) que contiene los mocks de las bases de datos originales de Hypatia. Dichas colecciones son:

* **usuarios**: Contiene lista de aprendices con sus respectivos campos de perfil, en los que destaca y son mayormente relevantes para este ejercicio: nombre, email, array de ids de los MVPs a los que se encuentra vinculado el aprendiz y horas realizadas del path.
* **proyectos**: Contiene lista de MVPs con sus respectivos campos los cuales son: nombre del proyecto y array de ids de aprendices que están vinculados a dicho proyecto.
* **paths**: Colección de documentos que contiene información tal como: nombre del path, horas que requiere las diferentes etapas del path, fecha de inicio del path y fecha final en la que se debe terminar, array de id de cursos vinculados a dicho path y finalmente un array de ids de aprendices vinculados al path.
* **listados**: Colección de cursos que contiene: nombre del curso, id del aprendiz que lo realizó, fecha en la que el aprendiz lo realizó, horas de duración del curso y horas reales que el aprendiz invirtió realizando el curso.

Luego se creó la home page que contiene el botón que permite ver una tabla con la lista de aprendices junto con su respectivo email y MVPs asociados, además de los botones añadir y eliminar, que permiten añadir o eliminar un MVP al aprendiz asociado manteniendo el estado en pantalla sincronizado. Finalmente se encuentra el botón que lo redirige a la vista de report.

Dicho consumo de datos y estado de pantalla sincronizado se hizo por medio de un servicio, además de hacer uso de los decoradores input y output.

### Componente Report

Consumiendo la data por medio de un servicio, se muestra por pantalla el consolidado de información  mostrado en las colecciones de *usuarios*, *paths* y *listado*, en cuanto a los avances del path y MVPs asociados al aprendiz. Además, haciendo uso del componente [ng circle progress](https://www.npmjs.com/package/ng-circle-progress) se muestra el porcentaje de formación realizada hasta la fecha. Luego al final de la vista se encuentran dos botones que permiten tanto descargar la información en un pdf como regresar a la vista learners respectivamente.

La funcionalidad de la descarga de pdf se hizo mediante de las bibliotecas [jsPdf](https://www.npmjs.com/package/jspdf) y [html2Canvas](https://www.npmjs.com/package/html2canvas)

## Resultados

### Link a la página web

[Hypatia](https://hypatia-147b1.web.app/)

### Credenciales de logueo

* > Usuario: `lider@gmail.com`
* > Contraseña: `123456789`


