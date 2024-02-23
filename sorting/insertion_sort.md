# Insertion Sort

## insertionSort(arr)

-    For i from `1` to `arr.length`
     -    initialize `current` as `arr[i]`
     -    initialize `j` as `i-1`
     -    loop while `j >= 0 && arr[j] > current`
          -    then `arr[j+1] = arr[j]`
          -    and `j--`
     -    `arr[j+1]=current`

> Java

```java
private static void insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            int current = arr[i];
            int j = i - 1;
            while (j >= 0 && current < arr[j]) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = current;
        }
    }
```

> Typescript

```typescript
export function insertionSort(list: number[]) {
	for (let i: number = 1; i < list.length; i++) {
		let current: number = list[i];
		let j: number = i - 1;
		while (j >= 0 && current < list[j]) {
			list[j + 1] = list[j];
			j--;
		}
		list[j + 1] = current;
	}
}
```

> Python

```python
def insertion_sort(arr: list) -> None:
    for i in range(1, len(arr)):
        current: int = arr[i]
        j: int = i - 1
        while j >= 0 and arr[j] > current:
            arr[j + 1] = arr[j]
            j -= 1

        arr[j + 1] = current
```
