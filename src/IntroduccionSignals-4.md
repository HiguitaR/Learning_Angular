    Signal Angular Moderno

    Las señales son la base de la gestion de estados en Angular, hacen que el estado sea explicita y 
    predecible, estan diseñadas para el estado de la interface del usuario y le indica a Angular 
    cuando cambia dicho estado.

    Por que existen las señales?
    - principalmente se creo para evitar la deteccion de eventos sin tener certeza que habia ocurrido
        un evento nuevo. Se tenia una complejidad alta en codigo y codigo repetitivo.
    - Elimina el adivinar cuando hay un cambio de eventos (Zone.js).
    - Con las señales los cambio de estados son explicitos, las dependencias se rastrean automaticamente

    Diferentes tipos de señales
    - señales modificables: son solo un valor o estado que se puede cambiar directamente
    - señales calculadas: son un estado que se basa en otras señales.
    - efectos: son logica que reacciona a los cambios de señal.

```ts
import { Component, signal } from '@angular/core';

@Component({
        selector: 'app-hello',
        import: [],
        templateUrl: './hello.html',
        styleUrl: './hello.scss',
        })
export class Hello {
    
    protected title = 'Welcome to Modern Angular!'
    
    protected isDisable = false;
    
    protected onClick(){
        console.log("Button clicked")
        this.isDisable = !this.isDisable; 
    }
    //agregando una signal
    protected count = signal(0);
    // este metodo se agrega al boton + para recibir un cambio y ejecutar la logica
    protected increateCounter(){
        this.count.update(value => value + 1);
    }
    // este metodo se agrega al boton - para recibir un cambio y ejecutar la logica
    protected decreaseCounter(){
        this.count.update(value => value - 1);
    }
    // este metodo se agrega al boton Reset para recibir un cambio y ejecutar la logica
    protected resetCounter(){
        this.count.set(0);
    }
}
```

```html
<p>This is my first Angular Component!</p>

<h1>{{ title }}</h1> 

<button [disabled]="isDisable" 
        (click)="onClick()">Toggle</button> 

<!--llamando la señal-->
<h1>{{ count() }}</h1>
<button (click)="increateCounter()">+</button>
<button (click)="decreaseCounter()">-</button>
<button (click)="resetCounter()">Reset</button>
```