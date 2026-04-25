    Productos grid
    para crear el componente products-grid usamos el mondo (ng g c products/products-grid)
    este comando crea otra carpeta products y alli crea el componente products-grid.

```ts
import { Component } from '@angular/core'; 
import {ProductCard} from '../product-card/product-card';

@Component({
selector: 'app-products-grid',
imports: [ProductCard],
templateUrl: './products-grid.html',
styleUrl: './products-grid.scss',
})
export class ProductsGrid{
}
```
```angular20html
<div class="grid">
    <app-product-card />
    <app-product-card />
    <app-product-card />
    <app-product-card />
    <app-product-card />
    <app-product-card />
</div>
```
```css
.grid{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 16px;
}
```

    Crearemos otro componente para las cards de la pagina usamos el comando 
    (ng g c products/product-card)
```ts
import { Component } from '@angular/core';

@Component({
selector: 'app-product-card',
imports: [MatCardModule, MarButtonModule],
templateUrl: './product-card.html',
styleUrl: './product-card.scss',
})
export class ProductCard{
}
```

```angular20html
<mat-card class="product-card">
    <mat-card-header>
        <mat-card-title>Product Name</mat-card-title>
        <mat-card-subtitle>Category</mat-card-subtitle>
    </mat-card-header>
    
    <mat-card-content>
        <p>Product description goes here.</p>
    </mat-card-content>
    
    <mat-card-actions>
        <button matButton>Add to Cart</button>
    </mat-card-actions>
</mat-card>
```
```css
.product-card{
    height: 100%;
    display: flex;
    flex-direction: column;
}
mat-card-content{
    flex: 1;
}
```

    asi va el componente app que es el main del proyecto: 
```angular20html
<app-header />
<main class="page">
    <app-products-grid />
</main>
```
```ts
import {Component, signal} from '@angular/core';
import {RouterOutlet} from '@angular/router';
import {Header} from './header/header';
import {ProductsGrid} from './products/products-grid/products-grid';

@Component({
    selector: 'app-root',
    imports: [RouterOutlet, Header, ProductsGrid],
    templateUrl: './app.html',
    styleUrl: './app/scss'
})
export class App{
    protected readonly title = signal('modern-angular');
}
```
```css
.page{
    padding: 16px;
    max-width: 1200px;
    margin: 0 auto;
}
```