```java
public interface DragonStrategy{
    public void executeStrategy(){
    }
}

public Class TransfigurationStrategy implements DragonStrategy{
    public void executeStrategy(){
        System.out.println("Transfiguration Strategy Applied")
    }
}

public Class CharmsStrategy implements DragonStrategy{
    public void executeStrategy(){
        System.out.println("Charms Strategy Applied")
    }
}

public Class PotionStrategy implements DragonStrategy{
    public void executeStrategy(){
        System.out.println("Potion Strategy Applied")
    }
}

public Class CareStrategy implements DragonStrategy{
    public void executeStrategy(){
        System.out.println("Care Strategy Applied")
    }
}

public class Student{
    private DragonStrategy strategy;

    public void setStrategy(DragonStrategy newStrategy){
        strategy = newStrategy;
    }
    public void executeStrategy(){
        strategy.executeStrategy();
    }
}

public class Main{
    public static void main(String args[]){
        Student harry = new Student();

        harry.setStrategy(new CharmsStrategy());
        harry.executeStrategy();
        harry.setStrategy(new CareStrategy());
        harry.executeStrategy();
        harry.setStrategy(new PotionsStrategy());
        harry.executeStrategy();
        harry.setStrategy(new TransfigurationStrategy());
        harry.executeStrategy();
         
    }
}
```