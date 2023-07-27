# Factory Pattern

## High Level Definition
- Design Pattern which allows you to create an object, without specifying the exact class of the object that will be instantiated
- Provides you an interface to create an object but allows subclasses to alter the type of object that will be created

## Why do you need Factory Pattern?
- To define an interface or an abstract class with a method to create an object : (FACTORY OR CREATOR)
- Then, letting subclasses implement the method on how to create that class : (CONCRETE FACTORY)

## Code in Python
```python
# Product interface (or abstract class)
class Product:
    def create(self):
        pass

# Concrete product classes
class ConcreteProductA(Product):
    def create(self):
        return "Product A"

class ConcreteProductB(Product):
    def create(self):
        return "Product B"

# Factory (Creator) class
class ProductFactory:
    def create_product(self, product_type):
        if product_type == "A":
            return ConcreteProductA()
        elif product_type == "B":
            return ConcreteProductB()
        else:
            raise ValueError("Invalid product type.")

# Client code
factory = ProductFactory()
product_type = "A"
product = factory.create_product(product_type)
print(product.create())  # Output: "Product A"
```

## Code in Java
```java
// Product interface
interface Product {
    void create();
}

// Concrete product classes
class ConcreteProductA implements Product {
    public void create() {
        System.out.println("Product A");
    }
}

class ConcreteProductB implements Product {
    public void create() {
        System.out.println("Product B");
    }
}

// Factory (Creator) class
class ProductFactory {
    public Product createProduct(String productType) {
        if (productType.equals("A")) {
            return new ConcreteProductA();
        } else if (productType.equals("B")) {
            return new ConcreteProductB();
        } else {
            throw new IllegalArgumentException("Invalid product type.");
        }
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        ProductFactory factory = new ProductFactory();
        String productType = "A";
        Product product = factory.createProduct(productType);
        product.create();  // Output: "Product A"
    }
}

```

