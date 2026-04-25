    Implementando Reactividad en la interface de usuario

    Vamos a conectar las señales y mostrar la lista de productos.
    Antes de crear la señal definimos una interface para los productos esto nos seguridad de 
    tipos y mejor autocompletado del editor. Usamos el comando (ng g i products/product)
```ts
export interface Product{
    id: number;
    name: string;
    description: string;
    price: number;
    originalPrice?: number; //quiere decir el ? que es opcional solo se va a usar para los productos en oferta
}
```

```ts
import { Component, signal } from '@angular/core'; 
import {ProductCard} from '../product-card/product-card';
import {Product} from '../product';

@Component({
selector: 'app-products-grid',
imports: [ProductCard],
templateUrl: './products-grid.html',
styleUrl: './products-grid.scss',
})
export class ProductsGrid{
    protected readonly products = signal<Product[]>([
        {
            id: 1,
            name: 'Premium Wireless Headphones',
            description: 'High-quality wireless headphones with noise cancellation and premiun sound',
            price: 199.99,
            originalPrice: 249.99,
        },
        {
            id: 2,
            name: 'Smart Fitness Watch',
            description: 'Track your fitness goals with this advanced smartwatch featuring heart',
            price: 299.99,    
        },
        {
            id: 3,
            name: 'Portable Bluetooth Speaker',
            description: 'Compact speaker with powerful bass and 12 hour battery life',
            price: 79.99,
        }
    ]);
}
```

```angular20html
<div class="products-container">
    <p>Total products: {{ products().length }}</p>
    
    <div class="products-grid">
        @for (product of products(); track product.id) {
            <app-product-card />
        } @empty {
        <div class="empty-state">
            <mat-icon>invetory_2</mat-icon>
            <h3>No Products available</h3>
            <p>Check back later for new arrivals!</p>
        </div>
    }
    </div>
</div>
```
```css
.products-container{
    display: grid;
    gap: 1rem;
}
.products-grid{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 16px;
}
.empty-state{
    grid-column: 1 / -1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 4rem 2rem;
    text-align: center;
}
mat-icon{
    font-size: 4rem;
    width: 4rem;
    height: 4rem;
    color: var(--mat-sys-outline);
    margin-bottom: 1rem;
}
h3{
    margin: 0 0 0.5rem;
    color: var(--mat-sys-on-surface);
}
```