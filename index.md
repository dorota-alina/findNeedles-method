# findNeedles - ideas for improvement
>CONTENTS
>>[Slim down your loops](#slim-down-your-loops)<br>
>>[Use enhanced loops](#use-enhanced-loops)<br>
>>[Name the function](#name-the-function)<br>
>>[Add comments](#add-comments)<br>

## Slim down your loops

For improving performance and efficiency (reducing the use of CPU/memory), split `haystack` just once by moving the `split` function outside the loops.

```java
public static void findNeedles(String haystack, String[] needles) {
   if (needles.length > 5) {
       System.err.println("Too many words!");
} else {
          int[] countArray = new int[needles.length];
          String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
          for (int i = 0; i < needles.length; i++) {
              for (int j = 0; j < words.length; j++) {
```

## Use enhanced loops

For iterating over collections using loops

```bash
for (int i = 0; i < needles.length; i++) {
    for (int j = 0; j < words.length; j++) {
```

Consider using enhanced loops to save some code space:
 
```bash
for (String needle : needles) {
    for (String word : words) {
```

## Name the function

Replace the abstract (figurative) function name with an informative (speaking) name, for example

`findNeedles(haystack, needlesList)` => `countWordsInString(str, wordsList)`.

## Add comments

 Insert comments on what the function intents to accomplish and/or why.
 
 For example, `// find and count occurances of each needle in the haystack`
 
