# Selection Sort

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

## selectionSort(arr)

-    for i from `0` to `arr.length`
     -    Initialize `minIdx` as `i`
     -    again For j from `i+1` to `arr.length`
          -    if `arr[j] < arr[minIdx]`
               -    then `minIdx = arr[j]`
     -    call `swap(arr, i , minIdx)`

> Java

```java
    public static void selectionSort(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            int minIdx = i;
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[j] < arr[minIdx]) {
                    minIdx = j;
                }
            }
            swap(arr, i, minIdx);
        }
    }
```

> Typescript

```typescript
export function selectionSort(list: number[]) {
	for (let i = 0; i < list.length; i++) {
		let minIdx: number = i;
		for (let j: number = i + 1; j < list.length; j++) {
			if (list[j] < list[minIdx]) minIdx = j;
		}
		swap(list, i, minIdx);
	}
}
```

> Python

```python
def selection_sort(arr: list) -> None:
    for i in range(len(arr) - 1):
        smallestIdx: int = i
        for j in range(i, len(arr)):
            if arr[j] < arr[smallestIdx]:
                smallestIdx = j

        swap(arr, i, smallestIdx)
```
