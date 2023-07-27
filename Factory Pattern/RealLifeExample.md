
## Real Life Example of Factory Pattern

Let's say that we are designing a GUI Button.
Now, the button can be of many types. For example: It can be of Linux Button, MacOS Button, Windows Style Button in my GUI

So, instead of adding if, else cases in my codebases. I can create an interface which implements rendering a button, like this:

```java
public interface Button(){
    public render(){

    }
}
```

Now, we add concrete implementations which implement the interface
```java
public class LinuxButton implements Button(){
    public void render(){
        System.out.println("Creating a Linux Button");
    }
}
public class MacButton implements Button(){
    public void render(){
        System.out.println("Creating a Mac Button");
    }
}
public class WindowsButton implements Button(){
    public void render(){
        System.out.println("Creating a Windows Button");
    }
}
```

Now, coming to our Button, when we want to create it, we will not contact the concrete implementations. Rather, we would contact the Button Factory. Therefore, we should create a Button Factory

```java
public class ButtonFactory(){
    public Button createButton(String buttonType){
        if(buttonType == "Linux Button"){
            return LinuxButton();
        } else if(buttonType == "Mac Button"){
            return MacButton();
        } else if(buttonType == "Windows Button"){
            return WindowsButton();
        } else {
            throw InvalidButtonTypeException;
        }
    }
}
```

So, at runtime, let's say we need a button. We will go to the main function and call this button factory

```java
public class MyButton{
    public static void main(String args[]){
        ButtonFactory factory = new ButtonFactory();
        Button macButton = factory.createButton("Mac Button");
        macButton.render();
    }
}
```