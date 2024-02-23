# Bubble Sort

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

## bubbleSort(arr)

-    For i from `0` to `arr.length`
-    Again for j `0` to `arr.length-i-1`
-    If `arr[j] > arr[j+1]`
     -    then call `swap(arr, j, j+1)`

> Java

```java
public static void bubbleSort(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    swap(arr, j, j + 1);
                }
            }
        }
    }
```

> Typescript

```typescript
export function bubbleSort(list: number[]): void {
	for (let i = 0; i < list.length; i++) {
		for (let j = 0; j < list.length - i - 1; j++) {
			if (list[j] > list[j + 1]) swap(list, j, j + 1);
		}
	}
}
```

> Python

```python
def bubble_sort(arr: list) -> None:
    for i in range(len(arr)):
        for j in range(len(arr) - i - 1):
            if arr[j] > arr[j + 1]:
                swap(arr, j, j + 1)
```
