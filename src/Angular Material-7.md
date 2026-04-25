    Angular Material + Header setup
    
    Agregaremos Angular Material 'material.angular.dev' accedemos alas guias y alli veremos el 
    comando 'ng add @angular/material' este se hara en el archivo del proyecto, esto configura 
    los archivos globales. comando para agregar el material (ng add @angular/material). 
    
    por que usar Angular Material?: Obtenemos componentes de interfaces unificados, proporciona 
    accecibilidad de forma predeterminada y un sistema de diseño completo que no tenemos que inventar.

    crear componente Header (ng g c header)
    para ver los cambios usamos el comando npm run start 

```angular20html
<mat-toolbar class="main-header">
    <button matButton>
        <mat-icon aria-hidden="false" aria-label="Home" fontIcon="home"></mat-icon>
    </button>
    <span class="branding">Modern Angular</span>
    <span class="spacer"></span>
    <button matButton>Product</button>
    <button matButton>
        <mat-icon aria-hidden="false" aria-label="Cart" fontIcon="shopping_cart"></mat-icon>
    </button>
</mat-toolbar>
```
```ts
import { Component } from '@angular/core';
import { MatToolbarModule } from '@angular/material/toolbar';
import { MatButtonModule } from '@angular/material/button';
import { MatIconModule } from '@angular/material/icon';

@Component({
    selector: 'app-header',
    imports: [MatToolbarModule, MatButtonModule, MatIconModule],
    templateUrl: './header.html',
    styleUrl: './header.scss',
})
export class Header{
    
}
```
```css
.spacer{
    flex: 1 1 auto;
}
.main-header{
    padding: 0 6px;
    position: relative;
    box-shadow: 0 1px 8px rgba(0, 0, 0, .3);
    z-index: 9;
    
    .branding{
        display: flex;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        margin: auto 0;
        line-height: 50px;
        padding: 0 64px 0 8px;
    }
}

```