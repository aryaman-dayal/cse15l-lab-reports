# Lab Report 3
## Part 1

Failure Inducing JUnit Test:
```
@Test
  public void testReverseFailure() {
    int[] input1 = {1, 2, 3, 4, 5, 6};
    int[] expectedOutput = {6, 5, 4, 3, 2, 1};

    ArrayExamples.reverseInPlace(input1);

    assertArrayEquals(expectedOutput, input1);
  }
```
Non-Failure Inducing JUnit Test:
```
@Test
  public void testReverseSuccess() {
    int[] input1 = {1};
    int[] expectedOutput = {1};

    ArrayExamples.reverseInPlace(input1);

    assertArrayEquals(expectedOutput, input1);
  }
```
Running the two tests:

![Image](TestFailure.png)

![Image](TestSuccess.png)


Code Before Fix:

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      int[] tempArr;
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

Code After Fix:

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int arr2 = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = arr2;
    }
  }
```

This fix addresses the issue because by iterating only to the halfway point of the array, hence the `i < arr.length / 2` condition in the `for` loop, thus ensuring that the method doesn't undo its previous work of swapping positions after this halfway point. Next, the `temp` variable to store the value at a position previously while that position is given the new reversed value is necessary in order to replace that old value in its new position, otherwise it would be overwritten without its value able to be recalled to be repositioned to its reversed position later, which was the issue with the original method before the fix.

## Part 2
1) `-i`
This command makes the grep search for the lines that contain the string in quotes case insensitive, thus ignoring the difference between upper and lowercase letters for the string in quotes.

`grep -i "temperate and nearly cloudless" ./technical/911report/chapter-1.txt`

This command searches for the lines in the file `chapter-1.txt` that contain `temperate and nearly cloudless` regardless of upper or lowercase in said argument.

OUTPUT: `Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.`

`grep -i "dEcLaRaTioN" ./technical/911report/chapter-2.txt`

This command searches for the lines in the file `chapter-2.txt` that contain `dEcLaRaTioN` regardless of upper or lowercase in said argument.

OUTPUT: `A DECLARATION OF WAR
                declaration was only the latest in the long series of his public and private calls
                the time he issued his February 1998 declaration of war, Bin Ladin had nurtured that
                for the countryside, expecting U.S. retaliation. Declarations taking credit for the`

2) `-rl`
This command lists all the names of files in the specified directory and its subdirectories that contains the string in quotes.

`grep -rl "WE HAVE SOME PLANES" ./technical`

This command lists all the names of files in `./technical` and its subdirectories that contains `WE HAVE SOME PLANES`.

OUTPUT: `docsearch/technical/911report/chapter-1.txt`

`grep -rl "Older adults are frequently counseled to lose weight" ./technical`

This command lists all the names of files in `./technical` and its subdirectories that contains `Older adults are frequently counseled to lose weight`.

OUTPUT: `docsearch/technical/biomed/1468-6708-3-1.txt`

3) `-r`
This command makes the grep search recursive, meaning it searches for the lines that contain the string in quotes through every file in the directory and its subdirectories.

`grep -r "INSIDE THE FOUR FLIGHTS" ./technical`

OUTPUT: `docsearch/technical/911report/chapter-1.txt:INSIDE THE FOUR FLIGHTS`

This command searches for the lines that contain `INSIDE THE FOUR FLIGHTS` through every file in the directory `./technical` and its subdirectories.

`grep -r "In February 1998" ./technical`

This command searches for the lines that contain `In February 1998` through every file in the directory `./technical` and its subdirectories.

OUTPUT: `docsearch/technical/911report/chapter-2.txt:            In February 1998, the 40-year-old Saudi exile Usama Bin Ladin and a fugitive Egyptian`

4) `-v`
This command shows lines in the file that do not contain the specified string in quotes.

`grep -v "a" ./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt`

This command shows lines in the file that do not contain `a`.

OUTPUT: 
```
UNITED STATES COURT OF APPEALS

FOR THE FOURTH CIRCUIT
SERVICES OF SOUTHWEST VIRGINIA, INCORPORATED,
� No. 00-1901
v.
Judge. (CA-00-33-2)
Decided: June 25, 2001
Senior Circuit Judge.
opinion.
O'DONNELL v. EIDLEMAN

COUNSEL


OPINION
PER CURIAM:
I.
O'DONNELL v. EIDLEMAN
on the merits.
II.
v. Ash, 422
O'DONNELL v. EIDLEMAN
III.
with instructions to dismiss.
VACATED AND REMANDED WITH INSTRUCTIONS
Corp., 940 F.2d 685, 697
```


`grep -v "e" ./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt`

This command shows lines in the file that do not contain `e`.

OUTPUT: 
```
UNITED STATES COURT OF APPEALS

FOR THE FOURTH CIRCUIT
SERVICES OF SOUTHWEST VIRGINIA, INCORPORATED,
� No. 00-1901
v.
opinion.
O'DONNELL v. EIDLEMAN

COUNSEL


OPINION
PER CURIAM:
I.
O'DONNELL v. EIDLEMAN
II.
v. Ash, 422
O'DONNELL v. EIDLEMAN
III.
with instructions to dismiss.
VACATED AND REMANDED WITH INSTRUCTIONS
Corp., 940 F.2d 685, 697
```

## [SOURCE USED](https://www.gnu.org/software/grep/manual/html_node/index.html)




