Task 1 (String, Regular Expressions)

Input two String variables. Verify if the first variable is a substring of the second variable. For
instance, if you entered &quot;SoftServe&quot; and &quot;SoftServe Academy&quot;, the expected result should be true.

Input the last name, first name, and middle name as String variables on the console. The
following outputs will be displayed on the console:
Last name and initials
First name
First name, middle name, and last name.

The task requires validation of usernames using regular expressions. The username should be
between 3 to 15 characters and can contain only Latin alphabet, numbers, and underscores. To
accomplish this, input five different usernames in the main method and output a message to the
console indicating whether each of the entered names is valid or not.

```java
import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Task1 {

    static  Scanner scn = new Scanner(System.in);

    public static void main(String[] args) {

        String USER_NAME_PATTERN = "^[a-zA-Z][a-zA-Z0-9-_\\.]{3,15}$";
        System.out.println("Enter yuor name");

        String name = scn.nextLine();

        Pattern pattern = Pattern.compile(USER_NAME_PATTERN);
        Matcher matcher = pattern.matcher(name);
        boolean matchFound = matcher.matches();

        if(matchFound) {
            System.out.println("Name " + name + " is valid");
        } else {
            System.out.println("Name " + name + " isn`t valid");
        }
    }
}
```

Task2 (Collections)

Write parameterized methods union (Set set1, Set set2) and intersect (Set set1, Set set2), realizing the operations of union and intersection of two sets. Test the operation of these techniques on two pre-filled sets.

```java
import java.io.*;
import java.util.*;

public class Task2 {

    public static void main(String args[]) {
        Set<String> set1 = new TreeSet<String>();

        set1.add("ex1");
        set1.add("ex2");
        set1.add("ex3");
        set1.add("ex4");

        Set<String> set2 = new TreeSet<String>();

        set2.add("ex3");
        set2.add("ex4");
        set2.add("ex5");
        set2.add("ex6");

        Set<String> union = new TreeSet<String>();

        union.addAll(set1);
        union.addAll(set2);

        System.out.println("Set1 : " + set1);
        System.out.println("Set2 : " + set2);
        System.out.println("Union : " + union);
        System.out.println();

        Set<String> intersection = new TreeSet<String>();

        intersection.addAll(set1);
        intersection.retainAll(set2);

        System.out.println("Intersection : " + intersection);
    }
}
```

Task3 (Collections)

Create map personMap and add to it ten persons of type <String, String> (lastName, firstName).
Output the entities of the map on the screen.
There are at less two persons with the same firstName among these 10 people?
Remove from the map person whose firstName is ”Orest” (or other). Print result.

```java
import java.io.*;
import java.util.*;

public class Task3 {

    public static void main(String args[]) {

        Map<String, String> personMap = new HashMap<String, String>();

        personMap.put("Bob", "Gray");
        personMap.put("Orest", "Red");
        personMap.put("Mik", "Gred");
        personMap.put("Loid", "Brown");
        personMap.put("Orest", "Dary");
        personMap.put("Kol", "Frey");
        personMap.put("Mlper", "Dewq");
        personMap.put("Mopb", "Uerf");
        personMap.put("Myre", "Pots");
        personMap.put("Orest", "Dot");

        for (Map.Entry<String, String> persone : personMap.entrySet()) {
            System.out.print(persone.getKey() + " ");
            System.out.println(persone.getValue());
        }
    }
}
```
