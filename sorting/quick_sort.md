# Quick Sort

-    From main function declare `list` or `array`.
-    Call `quickSort` and provide `list`, `0` and `length of list - 1` as
     parameters.

## swap(array, i, j)

-    Swapping of elements between indexes.

> Java

```java
public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
```

> Typescript

```typescript
function swap(arr: number[], i: number, j: number) {
	var temp: number = arr[i];
	arr[i] = arr[j];
	arr[j] = temp;
}
```

> Python

```python
def swap(arr: list, i: int, j: int):
    arr[i], arr[j] = arr[j], arr[i]
```

## partition(arr, stIdx, endIdx)

-    Select a `pivot` element.(in this case last element)

-    initialize `i` as start index i.e `stIdx` and `j` as `i-1`.

-    Traverse between `i` to `end-1`

     -    If `arr[i] <= pivot`
     -    then increment `j` by `1` and swap `i` and `j` index

-    Finally again increment `j` by `1` and swap `j` and `endIdx` i.e end index
     > Java

```java
public static int partition(int[] arr, int start, int end) {
        int pivot = arr[end];
        int j = start - 1;
        for (int i = start; i < end; i++) {
            if (arr[i] < pivot) {
                j++;
                swap(arr, i, j);
            }
        }
        j++;
        swap(arr, j, end);
        return j;
    }
```

> Typescript

```typescript
function partition(arr: number[], start: number, end: number): number {
	const pivot = arr[end];
	var j = start - 1;
	for (let i: number = start; i < end; i++) {
		if (arr[i] <= pivot) {
			j++;
			swap(arr, i, j);
		}
	}
	j++;
	swap(arr, j, end);
	return j;
}
```

> Python

```python
def partition(arr, st, end) -> int:
    pivot: int = arr[end]
    j = st - 1
    for i in range(st, end):
        if arr[i] <= pivot:
            j += 1
            swap(arr, i, j)

    swap(arr, j + 1, end)
    print(arr)
    return j + 1

```

## quickSort(arr, stIdx, end)

-    Mention the base case i.e `stIdx < endIdx`
-    If `stIdx < endIdx`
     -    then initialize `pivot` from `partition` function.
     -    call `quickSort` for element `before` partition.
     -    call `quickSort` for element `after` partition.

> Java

```java
public static void quickSort(int[] arr, int start, int end) {
        if (start < end) {
            int pivot = partition(arr, start, end);
            quickSort(arr, start, pivot - 1);
            quickSort(arr, pivot + 1, end);
        }
    }
```

> Typescript

```typescript
function quickSort(arr: number[], start: number, end: number): void {
	if (start < end) {
		const pivotIdx: number = partition(arr, start, end);
		quickSort(arr, start, pivotIdx - 1);
		quickSort(arr, pivotIdx + 1, end);
	}
}
```

> Python

```python
def quick_sort(arr, st, end) -> None:
    if st < end:
        pivot = partition(arr, st, end)
        quick_sort(arr, st, pivot - 1)
        quick_sort(arr, pivot + 1, end)
```
