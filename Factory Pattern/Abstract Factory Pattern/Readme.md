# Abstract Factory Pattern

## What is abstract factory pattern?
- The idea of abstract factory pattern is to put all the object creation logic within a set of related factory interfaces 

Imagine you have a toy factory that makes different kinds of toys, like stuffed animals and wooden puzzles. You use a "Factory Machine" to make each toy.

The Factory Pattern is like using one machine to make one type of toy. So, if you want a stuffed animal, you press a button on the "Stuffed Animal Machine," and it gives you a stuffed animal. If you want a wooden puzzle, you press a button on the "Wooden Puzzle Machine," and it gives you a wooden puzzle.

Now, sometimes you get an order for a whole set of toys, like a "Zoo Animals Set" that includes a stuffed lion and a wooden puzzle with a lion picture. With the Factory Pattern, you would need two separate machines to make both toys, and you have to remember which machines to use.

But the "Abstract Factory Pattern" is like having a "Magic Machine" that knows how to make different sets of toys. When you say, "Magic Machine, give me the Zoo Animals Set," it knows to make both the stuffed lion and the wooden lion puzzle together. It takes care of everything, and you don't need to worry about using two different machines.

So, the Abstract Factory Pattern helps us make groups of related toys that go together nicely, and we don't have to remember which machine to use for each toy set. It's like having a magical helper to make the toys that belong together!

```java
// Toy interface (Product interface)
interface Toy {
    void play();
}

// StuffedAnimal (Concrete Product)
class StuffedAnimal implements Toy {
    public void play() {
        System.out.println("Hugging and Squeaking...");
    }
}

// WoodenPuzzle (Concrete Product)
class WoodenPuzzle implements Toy {
    public void play() {
        System.out.println("Assembling and Solving...");
    }
}

// Abstract Factory interface
interface ToyFactory {
    Toy createStuffedAnimal();
    Toy createWoodenPuzzle();
}

// ZooAnimalsFactory (Concrete Factory)
class ZooAnimalsFactory implements ToyFactory {
    public Toy createStuffedAnimal() {
        return new StuffedAnimal();
    }

    public Toy createWoodenPuzzle() {
        return new WoodenPuzzle();
    }
}

// Client code using Abstract Factory pattern
public class Main {
    public static void main(String[] args) {
        ToyFactory zooAnimalsFactory = new ZooAnimalsFactory();

        Toy stuffedAnimal = zooAnimalsFactory.createStuffedAnimal();
        stuffedAnimal.play();  // Output: "Hugging and Squeaking..."

        Toy woodenPuzzle = zooAnimalsFactory.createWoodenPuzzle();
        woodenPuzzle.play();  // Output: "Assembling and Solving..."
    }
}
```