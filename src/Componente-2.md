    Componentes:

    En angular los componentes son los bloques de construccion principal desde la aplicacion.
    los componentes son autonomos, es explicito sobre sus dependencias osea todo lo que necesita
    este componente lo importa explicitamente al componente.

    Para consultar todos los componentes del CLI de angular vamos ala pagina web angular.dev y 
    buscamos en la barra del menu lateral 'Reference' alli accesamos 'CLI Reference' y obtenemos 
    un listado. 'ng generate': este comando puede generar o modificar cualquier archivo basado en 
    un esquema. El comando en Terminal es: 'ng g ng<schematic> [option]'.
    ejemplo: ng g component hello -> esto crea un componente llamado 'hello' con sus respectivas
        carpetas.

    Para consultar la guia de estilo de angular igualmente accesamos al web Angular.dev buscamos
    'Angular coding style guide' leer como debemos integrarlo a nuestro proyecto.

    A la hora de empezar a crear el proyecto debemos tener encuenta que cada componente es independiente
    de otros componentes si los queremos utilizar en otros componentes debemos importarlos donde queremos
    utilizarlos. 
    
```ts
import { Component } from '@angular/core';

@Component({
        selector: 'app-hello',
        import: [],
        templateUrl: './hello.html',
        styleUrl: './hello.scss',
        })
export class Hello{

}
```
```html
<p>This is my first Angular Component!</p>
```
    Para realizar un test en mis proyectos despues de agregar un componente o modificarlo en la 
    Terminal escribimos el siguiente comando: 'npm run' este realiza un test completo.
