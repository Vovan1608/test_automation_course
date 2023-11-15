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
