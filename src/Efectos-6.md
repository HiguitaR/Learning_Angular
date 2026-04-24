    Efectos

    En aplicaciones reales a veces debemos reaccionar a los cambio de estado, como ejemplo la
    llamada a un API imperativa, esto es un efecto secundario cosas que van mas alla del calculo
    de un valor y esto es exactamente de por que existen los efectos.
    Un Efecto es una funcion que se ejecuta siempre que cambia una de las señales que lee.
    Angular lo hara automaticamente cuando cambien sus dependencias. 

    Cual sera la diferencia entre un efecto y una señal computada?
    Una señal computada representa un estado derivado, devuelve un valor. Estas deben ser puras y sin
    efectos secundarios.
    Los Efectos por el contrario reacionan alos cambios de estado y no devuelven valores. Estos no 
    estan pensados para cambiar la logica empresarial. Se puede pensar como un puente entre estado
    reactivo y el mundo exterior. Para tener cuidado no actualizar las señales dentro de los efectos
    evitar la logica dentro de los efectos.

```ts
import { Component, signal, computed, effect } from '@angular/core';

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
    
    protected count = signal(0);
    
    protected doubleCount = computed(() => this.count() * 2);
    
    //agregando efecto: solo se vera en la consola de la pagina
    private readonly countLog = effect(() => {
        console.log('Count change: ', this.count())
    });
    
    protected increateCounter(){
        this.count.update(value => value + 1);
    }
    
    protected decreaseCounter(){
        this.count.update(value => value - 1);
    }
    
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