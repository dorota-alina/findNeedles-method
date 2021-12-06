# findNeedles - ideas for improvement

## Split just once

For efficicient processing and reducing CPU/memory usage, `haystack` is split into words just once.

```java
public static void findNeedles(String haystack, String[] needles) {
   if (needles.length > 5) {
       System.err.println("Too many words!");
} else {
          int[] countArray = new int[needles.length];
          String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
          for (int i = 0; i < needles.length; i++) {
              for (int j = 0; j < words.length; j++) {
                  if (words[j].compareTo(needles[i]) == 0) {
                      countArray[i]++;
                }
            }
        }
        for (int j = 0; j < needles.length; j++) {
            System.out.println(needles[j] + ": " + countArray[j]);
        }
    }
}
```

## Use enhanced nested loops

```bash
for (int i = 0; i < needles.length; i++) {
    for (int j = 0; j < words.length; j++) {
```

 ```bash
 || || || || || || || || || || || || || || ll
 \/ \/ \/ \/ \/ \/ \/ \/ \/ \/ \/ \/ \/ \/ \/
 ```
 
```bash
for (String needle : needles) {
for (String word : words) {
```

## Function name

Replace the abstract figurative function name with an informative speaking name, for example

`findNeedles(haystack, needlesList)` => `countWordsInString(str, wordsList)`

### Logic behind

```java
public static void findNeedles(String haystack, String[] needles) {
   if (needles.length > 5) {
       System.err.println("Too many words!");
   } else {
       int[] countArray = new int[needles.length];
       for (int i = 0; i < needles.length; i++) {
           String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
           for (int j = 0; j < words.length; j++) {
               if (words[j].compareTo(needles[i]) == 0) {
                    countArray[i]++;
                }
            }
        }
        for (int j = 0; j < needles.length; j++) {
            System.out.println(needles[j] + ": " + countArray[j]);
        }
    }
}
```

### Operational sequence

1. `findNeedles` checks if the size of the `needles` array is greater than five.
   * If greater than five, it output an error message and exites.
   * If smaller or equal five, it proceeeds to step 2.
2. `findNeedles` uses the `split` function to divide the input string using the following literals: `"`, `'`, `t`, `n`, `b`, `f`, `r`. The `haystack` string is split into words, which constitute the `words` array.
3. `findNeedles` compares each element of the `needles` array to each element of the `words`array.
4. If a `needle` occurs within the `words` array, the count for this `needle` is launched.
5. With the search and all the counts completed, `findNeedles` outputs a list of matched `needles` with their occurence count results.
