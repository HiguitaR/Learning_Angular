    Plantillas de Componentes y la interaccion con la interface

```ts
import { Component } from '@angular/core';

@Component({
        selector: 'app-hello',
        import: [],
        templateUrl: './hello.html',
        styleUrl: './hello.scss',
        })
export class Hello {
    // variable que se sube al contexto html como interpolacion
    // protected es para proteger el atributo al contexto de este componente(html,ts,css)
    // private solo lo puede usar dentro de esta clase el componente queda excluido su acceso (ts)
    protected title = 'Welcome to Modern Angular!'
    
    //propiedad para controlar la IU de manera explicita
    protected isDisable = false;
    
    //Metodo para ser escuchado en el boton del html
    protected onClick(){
        console.log("Button clicked")
        this.isDisable = !this.isDisable; //cuando le de click cambia su estado false-true 
    }
}
```

```html
<p>This is my first Angular Component!</p>

<h1>{{ title }}</h1> <!-- interpolacion de variables -->

<button [disabled]="isDisable"
    (click)="onClick()">Toggle</button> <!--El boton esta siendo controlado por una propiedad en (ts)-->
```