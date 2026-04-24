    Señales Computadas

    Estas nos ayudan a evitar la logica duplicada de los componentes.

```ts
import { Component, signal, computed } from '@angular/core';

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
    //agregamos una señal nueva que usa otra señal
    protected doubleCount = computed(() => this.count() * 2);
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
<h1>Count: {{ count() }}</h1>
<h1>Double: {{ doubleCount() }}</h1>
<button (click)="increateCounter()">+</button>
<button (click)="decreaseCounter()">-</button>
<button (click)="resetCounter()">Reset</button>
```