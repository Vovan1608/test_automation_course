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
import java.util.Random;

public class Task9 {

    static  Scanner scn = new Scanner(System.in);

    public static void main(String[] args) {

        StringBuilder password = new StringBuilder();

        boolean hasSpecSymbols = false;

        System.out.println("Would you like to use special symbols (!,?,#,*,@,$,%...)? Yes/No");
        System.out.println();

        String attemptSpec = scn.nextLine().toLowerCase();
        hasSpecSymbols = attemptSpec == "yes" ? true : false;

        int MIN_PASSWORD_LENGTH = 8;
        int passwordLength = 0;
        boolean flag = true;

        while (flag) {

            System.out.println("What the password length do you want? (It must be least 8 units))");
            System.out.println();

            int attempt = scn.nextInt();

            if ( attempt >= MIN_PASSWORD_LENGTH ) {
                passwordLength = attempt;
                flag = false;
            }
        }

        int BOTTOM_BOARD_UNICODE = hasSpecSymbols ? 33 : 65;
        int TOP_BOARD_UNICODE = 122;

        for(int i = 0; i < passwordLength; i += 1 ) {
            int askii = BOTTOM_BOARD_UNICODE + (int) ( Math.random() * (TOP_BOARD_UNICODE - BOTTOM_BOARD_UNICODE) );

            char ch = (char) askii;
            password.append(ch);
        }

        System.out.println(password.toString());

    }
}
```
