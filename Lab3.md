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
