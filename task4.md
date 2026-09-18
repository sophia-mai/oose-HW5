# Task 4

## 1. Design Pattern

The Composite pattern allows individual objects and collections of those objects to be treated through the same interface. In this design, `DVD` and `Book` are individual products, while `Shelf` contains a collection of `Product` objects. Since `Shelf` also implements `Product`, the client can treat an individual product and a shelf of products in the same way.

- `Product` is the Component.
- `DVD` and `Book` are the Leaf objects.
- `Shelf` is the Composite object.

## 2. `price()` Implementation

Since a `Shelf` contains multiple `Product` objects, its price can be calculated by adding together the prices of all products on the shelf.

```java
@Override
public int price() {
    int totalPrice = 0;

    for (Product product : products) {
        totalPrice += product.price();
    }

    return totalPrice;
}
```

Because every object in `products` implements the `Product` interface, `Shelf` can call `price()` without needing to know whether the object is a `Book`, `DVD`, or even another `Shelf`. This also allows shelves to contain other shelves while using the same `price()` implementation.
