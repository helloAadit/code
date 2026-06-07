# code
1) A customer database contains duplicate customer IDs due to repeated registrations. Write a Java program using HashSet to remove duplicate IDs and display the unique customer IDs.

-> import java.util.*;

public class Q1 {
    public static void main(String[] a) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of customer IDs: ");
        int n = sc.nextInt();

        Set<Integer> s = new HashSet<>();

        System.out.println("Enter " + n + " customer IDs:");
        for (int i = 0; i < n; i++)
            s.add(sc.nextInt());

        System.out.println("Unique IDs: " + s);
    }
}

2) A digital library stores book titles entered by users. Determine the number of unique titles available in the system using a HashSet.
-> import java.util.*;

public class Q2 {
    public static void main(String[] a) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of book titles: ");
        int n = sc.nextInt();
        sc.nextLine();

        Set<String> s = new HashSet<>();

        System.out.println("Enter " + n + " book titles:");
        for (int i = 0; i < n; i++)
            s.add(sc.nextLine());

        System.out.println("Unique titles: " + s);
        System.out.println("Count: " + s.size());
    }
}


3) A password validation system requires all characters in a password to be unique. Write a Java program using HashSet to determine whether a given password contains duplicate characters.
-> import java.util.*;

public class Q3 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter password: ");
        String password = sc.next();

        Set<Character> set = new HashSet<>();
        boolean duplicate = false;

        for (char ch : password.toCharArray()) {
            if (!set.add(ch)) {
                duplicate = true;
                break;
            }
        }

        System.out.println(
            duplicate ? "Duplicate chars found"
                      : "All characters are unique"
        );
    }
}


4) identify first repeating characters
-> import java.util.*;

public class Q4 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter message: ");
        String msg = sc.nextLine();

        Set<Character> set = new HashSet<>();
        char repeat = '\0';

        for (char ch : msg.toCharArray()) {
            if (!set.add(ch)) {
                repeat = ch;
                break;
            }
        }

        if (repeat != '\0')
            System.out.println("First repeat: " + repeat);
        else
            System.out.println("No repeat found");
    }
}


5) import java.util.*;

public class Q5 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter message: ");
        String str = sc.nextLine();

        Map<Character, Integer> map = new LinkedHashMap<>();

        for (char ch : str.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        char result = '\0';

        for (char ch : map.keySet()) {
            if (map.get(ch) == 1) {
                result = ch;
                break;
            }
        }

        System.out.println("First non-repeating: " + result);
    }
}


6) import java.util.*;

public class Q6 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter document text: ");
        String text = sc.nextLine();

        Set<String> words =
                new HashSet<>(Arrays.asList(text.split(" ")));

        System.out.println("Unique words: " + words);
        System.out.println("Count: " + words.size());
    }
}


7) import java.util.*;

public class Q7 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of IDs in set 1: ");
        int n1 = sc.nextInt();

        Set<Integer> s1 = new HashSet<>();
        System.out.println("Enter IDs for set 1:");
        for (int i = 0; i < n1; i++) {
            s1.add(sc.nextInt());
        }

        System.out.print("Enter number of IDs in set 2: ");
        int n2 = sc.nextInt();

        Set<Integer> s2 = new HashSet<>();
        System.out.println("Enter IDs for set 2:");
        for (int i = 0; i < n2; i++) {
            s2.add(sc.nextInt());
        }

        System.out.println("s2 subset of s1 ? " + s1.containsAll(s2));
    }
}


8) import java.util.*;

public class Q8 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of IDs in department 1: ");
        int n1 = sc.nextInt();

        Set<Integer> d1 = new HashSet<>();
        System.out.println("Enter IDs:");
        for (int i = 0; i < n1; i++) {
            d1.add(sc.nextInt());
        }

        System.out.print("Enter number of IDs in department 2: ");
        int n2 = sc.nextInt();

        Set<Integer> d2 = new HashSet<>();
        System.out.println("Enter IDs:");
        for (int i = 0; i < n2; i++) {
            d2.add(sc.nextInt());
        }

        Set<Integer> common = new HashSet<>(d1);
        common.retainAll(d2);

        System.out.println("Common IDs: " + common);
    }
}


9) import java.util.*;

public class Q9 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Set<Integer> d1 = new HashSet<>(Arrays.asList(101,102,103,104));
        Set<Integer> d2 = new HashSet<>(Arrays.asList(103,104,105,106));

        Set<Integer> common = new HashSet<>(d1);
        common.retainAll(d2);

        Set<Integer> onlyD1 = new HashSet<>(d1);
        onlyD1.removeAll(d2);

        Set<Integer> onlyD2 = new HashSet<>(d2);
        onlyD2.removeAll(d1);

        System.out.println("Common: " + common);
        System.out.println("Only in d1: " + onlyD1);
        System.out.println("Only in d2: " + onlyD2);
    }
}


10) import java.util.*;

public class Q10 {

    static class Stack<T> {
        List<T> list = new ArrayList<>();

        void push(T item) {
            list.add(item);
        }

        T pop() {
            return list.isEmpty() ? null
                                  : list.remove(list.size() - 1);
        }

        T peek() {
            return list.isEmpty() ? null
                                  : list.get(list.size() - 1);
        }
    }

    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println("Peek: " + stack.peek());
        System.out.println("Pop: " + stack.pop());
        System.out.println("Pop: " + stack.pop());
    }
}
