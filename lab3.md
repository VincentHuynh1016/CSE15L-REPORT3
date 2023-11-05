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








