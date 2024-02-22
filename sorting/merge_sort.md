# Merge Sort

-    From main function declare `list` or `array`.
-    Call `divide` and provide `list`, `0` and `length of list - 1` as
     parameters.

## Divide(arr, st, end)

-    Check if `st < end` - then initialize `mid` by calling `partition`
     function. - recursively call Divide for `arr, st, mid` - and Divide for
     `arr, mid+1, end` - Finally call Conquer for `arr, st, end, mid`

> Java

```java
public static void divide(int[] arr, int st, int end) {
        if (st < end) {
            int midIdx = (st + end) / 2;
            divide(arr, st, midIdx);
            divide(arr, midIdx + 1, end);
            conquer(arr, st, end, midIdx);
        }

    }
```

> Typescript

```typescript
export function divide(arr: number[], st: number, end: number): void {
	if (st < end) {
		const midIdx: number = Math.floor((st + end) / 2);
		divide(arr, st, midIdx);
		divide(arr, midIdx + 1, end);
		conquer(arr, st, end, midIdx);
	}
}
```

> Python

```python
def divide(arr: list, st: int, end: int) -> None:
    if st < end:
        mid: int = (st + end) // 2
        divide(arr, st, mid)
        divide(arr, mid + 1, end)
        conquer(arr, st, end, mid)

```

## Conquer(arr, st, end, mid)

-    Now initialize new array as `newArr` which have length `(st + end)/2`.
-    Initialize 3 variables
     -    `idx1 = st` to store start index of first array to be merged
     -    `idx2 = mid + 1` to store the staring index of second array to be
          merged
     -    `x = 0` to store initial index of new array. (can be ignored in case
          of Python and Javascript)
-    Loop while `idx1 <= mid && idx2 <= end`

     -    if `arr[idx1] >= arr[idx2]`
          -    then `newArr[x] = arr[idx1]`. store the larger value in new
               array.
          -    and increment x and idx1 i.e `x++` , `idx1++`
     -    else
          -    then `newArr[x] = arr[idx2]`. store the larger value in new
               array.
          -    and increment x and idx2 i.e `x++` , `idx2++`

-    Loop while `idx1 <= mid` (if any element left in first array)
     -    then `newArr[x] = arr[idx1]`. store value in new array.
     -    and increment x and idx1 i.e `x++` , `idx1++`
-    Loop while `idx2 <= end` (if any element left in first array)

     -    then `newArr[x] = arr[idx2]`. store value in new array.
     -    and increment x and idx2 i.e `x++` , `idx2++`

-    Finally copy new array to original array.
-    initialize j as `st`
-    For `i` from `0` to `len(newArr)` - then `arr[j] = newArr[i]` - and `j++` ,
     `i++`.

> Java

```java
public static void conquer(int[] arr, int st, int end, int midIdx) {
        int[] newArr = new int[end - st + 1];
        int idx1 = st;
        int idx2 = midIdx + 1;
        int x = 0;
        while (idx1 <= midIdx && idx2 <= end) {
            if (arr[idx1] <= arr[idx2])
                newArr[x++] = arr[idx1++];
            else
                newArr[x++] = arr[idx2++];
        }
        while (idx1 <= midIdx)
            newArr[x++] = arr[idx1++];

        while (idx2 <= end)
            newArr[x++] = arr[idx2++];

        for (int i = 0, j = st; i < newArr.length; i++, j++)
            arr[j] = newArr[i];
    }

```

> Typescript

```typescript
function conquer(arr: number[], st: number, end: number, midIdx: number): void {
	let newArr: number[] = new Array<number>();
	let idx1: number = st;
	let idx2: number = midIdx + 1;

	while (idx1 <= midIdx && idx2 <= end) {
		if (arr[idx1] <= arr[idx2]) newArr.push(arr[idx1++]);
		else newArr.push(arr[idx2++]);
	}
	while (idx1 <= midIdx) newArr.push(arr[idx1++]);

	while (idx2 <= midIdx) newArr.push(arr[idx2++]);

	let x = st;
	for (let num of newArr) {
		arr[x++] = num;
	}
}
```

> Python

```python
def conquer(arr: list, st: int, end: int, mid: int) -> None:
    newArr: list = []
    idx_1: int = st
    idx_2: int = mid + 1
    x: int = 0

    while idx_1 <= mid and idx_2 <= end:
        if arr[idx_1] <= arr[idx_2]:
            newArr.append(arr[idx_1])
            idx_1 += 1
        else:
            newArr.append(arr[idx_2])
            idx_2 += 1

    while idx_1 <= mid:
        newArr.append(arr[idx_1])
        idx_1 += 1

    while idx_2 <= end:
        newArr.append(arr[idx_2])
        idx_2 += 1
    j: int = st
    for i in range(len(newArr)):
        arr[j] = newArr[i]
        j += 1

```
