# Sliding Window Problem

An array or list is given. We have to find the highest sum of consecutive
elements. The size of consecutive element will be an user input.

-    let elements `{1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0}` as `arr`
     whose size is `n`.
-    and `k` size of window(consecutive element size).

## Basic Approach

-    initialize `maxSum = 0`
-    For i from `0` to `arr.length - n`
     -    initialize `sum = 0`
     -    Again For j from `i` to `i+k`
          -    `sum = sum + arr[i]`
     -    If `sum > maxSum`
          -    print `i` (starting index of window)
          -    then `maSum = sum`

> Java

```java
public static void main(String[] args) {
        int[] arr = { 1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0 };
        int k = Integer.parseInt(System.console().readLine());
        int maxSum = 0;
        for (int i = 0; i < arr.length - k; i++) {
            int sum = 0;
            for (int j = i; j < i + k; j++) {
                sum += arr[j];
            }
            if (sum > maxSum) {
                System.out.println(i + " " + sum);
                maxSum = sum;
            }
        }
        System.out.println(maxSum);
    }
```

> Typescript

```typescript
let arr: number[] = [1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0];
const k: number = 3; // User input
let maxSum: number = 0;
for (let i: number = 0; i < arr.length - k; i++) {
	let sum: number = 0;
	for (let j: number = i; j < i + k; j++) {
		sum += arr[j];
	}
	if (sum > maxSum) {
		console.log(i);
		maxSum = sum;
	}
}
console.log(maxSum);
```

## Optimized Approach

-    initialize `sum=0`
-    For i from `0` to `k` (to get the sum of first window)

     -    `sum = sum + arr[i]`

-    Now initialize `window` as `sum`
-    Traverse for i `0` to `n-k`

     -    check if `window > sum`

          -    then `sum = window`

     -    finally update the window for every step i.e sliding the window by one
          subtracting first element and adding next of last element
          `window = window - arr[i] + arr[i+k]`

> Java

```java
public static void main(String[] args) {
        int[] arr = { 1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0 };
        int k = Integer.parseInt(System.console().readLine());
        int sum = 0;
        for (int i = 0; i < k; i++) {
            sum += arr[i];
        }
        int window = sum;
        for (int i = 0; i < arr.length - k; i++) {
            if (window > sum)
                sum = window;

            window = window - arr[i] + arr[i + k];
        }
        System.out.println(sum);
    }
```

> Typescript

```typescript
let arr: number[] = [1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0];
const k: number = 4; // User input
let sum: number = 0;
for (let i: number = 0; i < k; i++) {
	sum += arr[i];
}
let wind: number = sum;
for (let i: number = 0; i < arr.length - k; i++) {
	if (wind > sum) sum = wind;
	wind = wind - arr[i] + arr[i + k];
}

console.log(sum);
```

> Python

```python
if __name__ == '__main__':
    arr: list = [1, 3, 5, 2, 7, 4, 8, 9, 5, 3, 5, 7, 9, 3, 2, 0]
    k: int = int(input('enter k '))
    var_sum: int = 0  # initialize sum as zero

    # found a sum of the first three elements
    for i in range(k):
        var_sum = var_sum + arr[i]

    window: int = var_sum  # initialize a window as sum
    for i in range(len(arr) - k):
        if window > var_sum:
            var_sum = window

        window = window - arr[i] + arr[i + k]

    print(var_sum)
```
