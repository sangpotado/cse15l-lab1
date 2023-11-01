# Lab 3 Report

## Part 1 - Bugs

Chosen bugs: ArrayTests - testReverseInPlace(Array)

### 1. A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```
	@Test 
	public void SDtestReverseInPlace() {
    int[] input1 = {1,2,3,4};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{4,3,2,1}, input1);
	}
```

### 2. An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```

### 3. The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

![part1.3symtom](part1symptom.png)

### 4. The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

Before: 

```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

After: 

```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];    //change
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp; //change
    }
  }
```

![alt name](file path)