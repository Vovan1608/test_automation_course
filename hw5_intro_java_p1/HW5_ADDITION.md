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
import java.util.regex.Matcher;
import java.util.regex.Pattern;
import java.util.Arrays;

class Task1 {

    public static boolean isCompareTwoStrings (String str1, String str2) {
        boolean compareResult = str1.toLowerCase().equals(str2.toLowerCase());

        return compareResult;
    }

    public static String makeSubstring (String str, int startIndex, int endIndex) {
        String subString = str.substring(startIndex, endIndex);

        return subString;
    }

    public static int checkSubstringInString (String str, String subStr) {
        int index = str.indexOf(subStr);

        return index;
    }

    public static String replaceallOccurrencesOfOneSubstringWithAnother (String str, String subStrYouWant, String subStrInStr) {
        String resStr = str.replaceAll(subStrYouWant, subStrInStr);

        return resStr;
    }

    public static boolean hasStringDigits (String str) {
        Pattern pattern = Pattern.compile("\\d", Pattern.CASE_INSENSITIVE);
        Matcher matcher = pattern.matcher(str);
        boolean matchFound = matcher.find();

        return matchFound;
    }

    public static String removeAllLeadingAndTrailingSpaces (String str) {
        String trimStr = str.trim();

        return trimStr;
    }

    public static String[] splitString (String str, String delimiter) {
        String[] splitString = str.split(delimiter);

        return splitString;
    }

    public static void main (String[] args) {

        boolean res1 = Task1.isCompareTwoStrings("Vova", "Sasha");

        System.out.println("Result of task1: " + res1);
        System.out.println();

        String res2 = Task1.makeSubstring("SoftSrve", 3, 8);

        System.out.println("Result of task2: " + res2);
        System.out.println();

        int res3 = Task1.checkSubstringInString("SoftServe", "Serve");

        System.out.println("Result of task3: " + res3);
        System.out.println();


        String str1 = "SoftServeSoftServSoftServe";
        String resStr =  Task1.replaceallOccurrencesOfOneSubstringWithAnother(str1, "Sof", "Fas");
        System.out.println(resStr);
        System.out.println();

        String str2 = "Soft22Serve";
        boolean res4 = Task1.hasStringDigits(str2);
        System.out.println("Result of task4: " + res4);
        System.out.println();

        String res5 = Task1.removeAllLeadingAndTrailingSpaces("    SoftServe        ");
        System.out.println("Result of task5: " + res5);
        System.out.println();

        String text = "FIFA will never regret it";
        String[] res6 = Task1.splitString(text, " ");
        System.out.println("Result of task6: " + Arrays.toString(res6));
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

Task4 (OOP, Collections)

Write class Student that provides information about the name of the student and his course. Class Student should consists of

1. properties for access to these fields
2. constructor with parameters
3. method printStudents (List students, Integer course), which receives a list of students and the course number and prints to the console the names of the students from the list, which are taught in this course (use an iterator)
4. methods to compare students by name and by course
5. In the main() method:
   - declare List students and add to the list five different students
   - display the list of students ordered by name
   - display the list of students ordered by course.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Student {

    private String studentsName;
    private int courseNumber;

    public Student (String studentsName, int courseNumber) {
        this.studentsName = studentsName;
        this.courseNumber = courseNumber;
    }

    public String getStudentsName() {
        return studentsName;
    }

    public void setStudentsName(String studentsName) {
        this.studentsName = studentsName;
    }

    public int getCourseNumber() {
        return courseNumber;
    }

    public void setCourseNumber(int courseNumber) {
        this.courseNumber = courseNumber;
    }

    static void printStudents (ArrayList<Student> students, int courseNumber) {

        for(Student st : students){

            if (st.getCourseNumber() == courseNumber) {
                System.out.println(st.getStudentsName());
            }
        }
    }

    public void compare () {

    }

    public static void main(String[] args) {

        ArrayList<Student> myArrayList = new ArrayList<Student>();
        myArrayList.add(new Student("Oper", 1));
        myArrayList.add(new Student("Oper", 2));
        myArrayList.add(new Student("Mik", 1));
        myArrayList.add(new Student("Kol", 2));
        myArrayList.add(new Student("Kile", 3));

        Student.printStudents(myArrayList, 1);
    }
}
```
