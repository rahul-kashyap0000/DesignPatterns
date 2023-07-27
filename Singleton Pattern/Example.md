```java
public class KeeperOfForbiddenSpells {
    private static KeeperOfForbiddenSpells instance;
    private List<String> grantedPermissions;

    private KeeperOfForbiddenSpells() {
        grantedPermissions = new ArrayList<>();
    }

    public static synchronized KeeperOfForbiddenSpells getInstance() {
        if (instance == null) {
            instance = new KeeperOfForbiddenSpells();
        }
        return instance;
    }

    public void grantPermission(String studentName, String spellName) {
        String permission = studentName + " - " + spellName;
        grantedPermissions.add(permission);
    }

    public void showGrantedPermissions() {
        System.out.println("Granted Permissions:");
        for (String permission : grantedPermissions) {
            System.out.println(permission);
        }
    }
}

public class HogwartsMain {
    public static void main(String[] args) {
        KeeperOfForbiddenSpells keeper = KeeperOfForbiddenSpells.getInstance();

        // Granting permission to students
        keeper.grantPermission("Harry Potter", "Avada Kedavra");
        keeper.grantPermission("Hermione Granger", "Expecto Patronum");
        keeper.grantPermission("Draco Malfoy", "Cruciatus Curse");

        // Displaying granted permissions
        keeper.showGrantedPermissions();
    }
}

```