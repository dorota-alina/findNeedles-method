# findNeedles - ideas for improvement

For more efficicient processing, an array of text (haystack) is created only once:

```bash
public static void findNeedles(String haystack, String[] needles) {
int[] counter = new int[needles.length];
String[] words = haystack.toLowerCase().split("[ .,:;\"\'\t\n\b\f\r]", 0);
for (int i = 0; i < needles.length; i++) {
   for (int j = 0; j < words.length; j++) {
      if (needles[i].equals(words[j])) {
        counter[i]++;
        }
      }
  }
for (int j = 0; j < needles.length; j++) {
    System.out.println(needles[j] + ": " + counter[j]);
    }
}
```

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
