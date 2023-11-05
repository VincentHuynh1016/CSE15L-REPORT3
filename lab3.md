# Part 1 (Bugs):

#### A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown):
```
@Test
  public void testReverse(){
    int[] input1 = {1,2,3,4};
    int[] expected = {4,3,2,1};

    assertArrayEquals(expected, ArrayExamples.reversed(input1));
  }
```

#### An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown):

```
@Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```

#### The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above):

<img width="514" alt="image" src="https://github.com/VincentHuynh1016/CSE15L-REPORT3/assets/114731503/610846ef-50bd-4a3d-ad23-c920212e9cc7">

#### The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown):

#### Before:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

#### After:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
<img width="193" alt="image" src="https://github.com/VincentHuynh1016/CSE15L-REPORT3/assets/114731503/41a13ee8-8a8c-40cf-b623-143383ebb6ea">

It looks like the values in the new reversed array are not being updated correctly. In order to fix this issue, we should update the newArray and not the original. And also return the newArray

# Part 2 (Researching Commands):

#### grep -r:

```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r "base pair" technical/plos/ > plos-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc plos-sizes.txt
  3  48 412 plos-sizes.txt
```
```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -r "base pair" technical/biomed/ > biomed-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc biomed-sizes.txt
  226  2326 22534 biomed-sizes.txt
```
It looks like the `grep -r` command searches for the specified pattern ("base pair") in all files within the given directory and its subdirectories. The `grep -r` command is important because it allows you to perform a recursive search for specific text patterns within files and directories. 

#### grep -l:

```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -l "base pair" technical/plos/* > plos-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc -l plos-sizes.txt
2 plos-sizes.txt
```
```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -l "base pair" technical/biomed/* > biomed-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc -l biomed-sizes.txt
74 biomed-sizes.txt
```
It looks like the `grep -l` is used to print only the names of files that contain the specified text pattern ("base pair"). This is important because it changes the behavior of grep to only list the names of files that contain the specified text pattern, without showing the actual matching lines.

#### grep -rv:

```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -rv "base pair" technical/plos/ > plos-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc plos-sizes.txt
  38078  446279 4352999 plos-sizes.txt
```
```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -rv "base pair" technical/biomed/ > biomed-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ wc biomed-sizes.txt
  490447  3925577 44062361 biomed-sizes.txt
```
It looks like the `-r` option tells grep to perform a recursive search, and the `-v` option inverts the match, meaning it will display lines that do not contain the text "base pair." This is important for conducting a recursive search within directories and their subdirectories to find files that do not contain a specific text pattern. 

#### grep -rl:

```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -rl "base pair" technical/plos/ > plos-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ cat plos-sizes.txt
technical/plos/journal.pbio.0020190.txt
technical/plos/journal.pbio.0020223.txt
```

```
vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ grep -rl "base pair" technical/biomed/ > biomed-sizes.txt

vince@DESKTOP-Q15CO19 MINGW64 ~/OneDrive/Documents/GitHub/docsearch (main)
$ cat biomed-sizes.txt
technical/biomed/1471-2091-3-4.txt
technical/biomed/1471-2105-2-8.txt
technical/biomed/1471-2105-2-9.txt
technical/biomed/1471-2105-3-18.txt
technical/biomed/1471-2105-3-2.txt
technical/biomed/1471-2105-3-24.txt
technical/biomed/1471-2105-4-27.txt
technical/biomed/1471-2121-1-2.txt
technical/biomed/1471-2121-3-10.txt
technical/biomed/1471-213X-1-4.txt
technical/biomed/1471-2156-2-17.txt
technical/biomed/1471-2156-2-3.txt
technical/biomed/1471-2156-2-7.txt
technical/biomed/1471-2156-3-16.txt
technical/biomed/1471-2156-3-4.txt
technical/biomed/1471-2164-2-1.txt
technical/biomed/1471-2164-2-4.txt
technical/biomed/1471-2164-2-7.txt
technical/biomed/1471-2164-3-13.txt
technical/biomed/1471-2164-3-31.txt
technical/biomed/1471-2164-3-35.txt
technical/biomed/1471-2164-3-6.txt
technical/biomed/1471-2164-3-7.txt
technical/biomed/1471-2164-4-14.txt
technical/biomed/1471-2164-4-16.txt
technical/biomed/1471-2164-4-2.txt
technical/biomed/1471-2164-4-21.txt
technical/biomed/1471-2164-4-25.txt
technical/biomed/1471-2180-1-12.txt
technical/biomed/1471-2180-1-31.txt
technical/biomed/1471-2180-1-34.txt
technical/biomed/1471-2180-2-13.txt
technical/biomed/1471-2180-2-38.txt
technical/biomed/1471-2180-3-13.txt
technical/biomed/1471-2180-3-15.txt
technical/biomed/1471-2199-2-12.txt
technical/biomed/1471-2199-2-5.txt
technical/biomed/1471-2199-3-17.txt
technical/biomed/1471-2202-2-12.txt
technical/biomed/1471-2202-3-16.txt
technical/biomed/1471-2202-3-7.txt
technical/biomed/1471-2210-2-14.txt
technical/biomed/1471-2229-2-3.txt
technical/biomed/1471-2334-3-12.txt
technical/biomed/1471-2350-2-2.txt
technical/biomed/1471-2350-2-8.txt
technical/biomed/1471-2377-3-4.txt
technical/biomed/1471-2458-3-5.txt
technical/biomed/1471-2474-2-1.txt
technical/biomed/1472-6750-1-13.txt
technical/biomed/1475-4924-1-5.txt
technical/biomed/1477-7827-1-23.txt
technical/biomed/ar297.txt
technical/biomed/ar409.txt
technical/biomed/ar774.txt
technical/biomed/bcr570.txt
technical/biomed/bcr571.txt
technical/biomed/bcr602.txt
technical/biomed/bcr631.txt
technical/biomed/gb-2000-1-1-research002.txt
technical/biomed/gb-2001-2-12-research0054.txt
technical/biomed/gb-2001-2-3-research0008.txt
technical/biomed/gb-2001-2-4-research0010.txt
technical/biomed/gb-2001-2-4-research0011.txt
technical/biomed/gb-2001-2-4-research0014.txt
technical/biomed/gb-2001-2-6-research0021.txt
technical/biomed/gb-2001-2-7-research0025.txt
technical/biomed/gb-2001-2-8-research0027.txt
technical/biomed/gb-2002-3-10-research0053.txt
technical/biomed/gb-2002-3-12-research0079.txt
technical/biomed/gb-2002-3-12-research0083.txt
technical/biomed/gb-2002-3-6-research0029.txt
technical/biomed/gb-2003-4-4-r24.txt
technical/biomed/rr196.txt
```
It looks like the `grep -rl` command performs a recursive search within the directory and its subdirectories for files that contain the text "base pair." The -r option enables recursive search, and the -l option instructs grep to list only the names of files containing the specified pattern. This is important because it is a valuable tool for conducting efficient and recursive searches within directories and subdirectories to identify and list files that contain a specific text pattern.




