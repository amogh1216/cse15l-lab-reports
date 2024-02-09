# Lab Report 3
This lab report is about debugging and new command-line commands.

## Part 1 - Bug in the filter method of ListExamples.java
The `filter(List<String> list, StringChecker sc)` method traverses a list and adds items that return true by my `StringChecker` object to a new list, which is returned by the method. The filter should maintain the order of the original list.

Below is my implementation of the `StringChecker` class, where the `checkString(String s)` method returns true if the String contains an a.
```java
class Checker implements StringChecker {
    public boolean checkString(String s){
            return s.contains("a");
    }
}
```

### Failure Inducing Input
My input was the list `[all, court, ape]` and the output was `[ape, all]`. The expected output was `[all, ape]`.
```java
@Test
public void testFilter(){
    ArrayList<String> input = new ArrayList<String>();
    input.add("all");
    input.add("court");
    input.add("ape");

    ArrayList<String> expected = new ArrayList<>();
    expected.add("all");
    expected.add("ape");

    ArrayList<String> filtered = (ArrayList) ListExamples.filter(input, new Checker());

    assertEquals(expected, filtered);
}
```

### Test that Passes
My input was the list `[bring, take, potion, trench]` and the output was `[take]`. The expected output was `[take]`.
```java
@Test
public void testFilter(){
    ArrayList<String> input = new ArrayList<String>();
    input.add("bring");
    input.add("take");
    input.add("potion");
    input.add("trench");

    ArrayList<String> expected = new ArrayList<>();
    expected.add("take");

    ArrayList<String> filtered = (ArrayList) ListExamples.filter(input, new Checker());

    assertEquals(expected, filtered);
}
```

### Symptom (Output of both JUnit Tests)
![Image]()

### Bug

Before:

```java
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s); // here is the error
      }
    }
    return result;
  }
```

After:

```java
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s); // the change from prepending to appending
      }
    }
    return result;
  }
```

This fix addresses the issue because before, items that passed the string check were prepended to the resulting list. This meant that the order of the original list wasn't preserved, and was in fact reversed. By changing the method call from `add(int index, E element)` to `add(E element)`, the element is added to the end of the list and the order of the list is preserved.

## Part 2 - Researching the Grep command
