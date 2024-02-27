# LinkedList

## Node

-    Each element in a linked list is called as `Node`. It contains a data and
     address of next Node.
-    Create a constructor which takes `data` as parameter and assigns next
     address as null.

> Java

```java
class Node{
    String data;
    Node next;

    Node(String data){
        this.data = data;
        this.next = null;
    }
}
```

> Python

```python
class Node:
    def __init__(self, data: str):
        self.data: str = data
        self.next: Node | None = None
```

> Typescript

```typescript
class MyNode {
	data: string;
	next: MyNode | null;
	constructor(data: string) {
		this.data = data;
		this.next = null;
	}
}
```

## LinkedList

-    It is the class which will be treated as actual `LinkedList`. This class
     will contain all the linked list method.
-    This class must have a private variable head to track the head of linked
     list.
-    There must be a constructor which initializes head as null.

> Java

```java
public class LinkedList {
    private Node head;

    public LinkedList() {
        head = null;
    }
}
```

> Typescript

```typescript
class LinkedList {
	private head: MyNode | null;
	constructor() {
		this.head = null;
	}
}
```

> Python

```python
class LinkedList:
    def __init__(self):
        self.head: Node | None = None

```

### insert(data)

-    This method is responsible for inserting data into linked list. This method
     adds element to the end of linked list.
-    initialize a `newNode` with the variable data;
-    if `head` is `null` then `head = newNode` and return;
-    initialize a new variable `ptr` as `head` which will traverse nodes.
-    Loop while `ptr.next != null` i.e traverse till last element

     -    then `ptr = ptr.next` move ptr to next element

-    Now `ptr.next = null` so do `ptr.next = newNode`

> Java

```java
public void insert(String data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node ptr = head;
        while (ptr.next != null) {
            ptr = ptr.next;
        }
        ptr.next = newNode;
    }
```

> Typescript

```typescript
insert(data: string) {
		const newNode: MyNode = new MyNode(data);
		if (this.head == null) {
			this.head = newNode;
			return;
		}
		let ptr: MyNode = this.head;
		while (ptr.next != null) {
			ptr = ptr.next;
		}
		ptr.next = newNode;
	}
```

> Python

```python
    def insert(self, data: str) -> None:
        newNode: Node = Node(data)
        if self.head is None:
            self.head = newNode
            return

        ptr: Node | None = self.head
        while ptr.next is not None:
            ptr = ptr.next

        ptr.next = newNode
```

### delete()

-    This method is responsible for removing the elements from linked list. This
     method removes last element from the linked list.
-    Check if `head == null` then return
-    initializes a variable `ptr` as `head.next` and `prevPtr` as `head`. i.e
     prevPtr is head and ptr is it's next element.
-    Loop while `ptr.next != null` i.e ptr till last element
     -    then update `ptr = ptr.next` and `prevPtr = prevPtr.next`
-    Now prevPtr is at previous of last element so do `prevPtr.next = null`.

> Java

```java
public void delete() {
        if (head == null) {
            return;
        }
        Node ptr = this.head.next;
        Node prevPtr = this.head;
        while (ptr.next != null) {
            ptr = ptr.next;
            prevPtr = prevPtr.next;
        }
        prevPtr.next = null;
    }
```

> Typescript

```typescript
delete() {
		if (this.head == null) {
			return;
		}
		let ptr: MyNode | null = this.head.next;
		let prevPtr: MyNode = this.head;
		while (ptr && ptr.next != null) {
			ptr = ptr.next;
			prevPtr = prevPtr.next as MyNode;
		}
		prevPtr.next = null;
	}
```

> Python

```python
    def delete(self) -> None:
        if self.head is not None:
            ptr: Node | None = self.head.next
            prevPtr: Node | None = self.head
            while ptr.next is not None:
                ptr = ptr.next
                prevPtr = prevPtr.next

            prevPtr.next = None
```

### insertBegin(data)

-    This method is responsible for inserting element in the beginning of the
     linked list.
-    initialize a `newNode` with the variable data;
-    check if `head == null`
     -    then call `insert(data)` and return
-    `newNode.next = head`
-    `head = newNode`

> Java

```java
public void insertBegin(String data) {
        if (head == null) {
            insert(data);
            return;
        }
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;

    }
```

> Typescript

```typescript
insertBegin(data: string) {
		if (this.head == null) {
			this.insert(data);
			return;
		}
		const newNode: MyNode = new MyNode(data);
		newNode.next = this.head;
		this.head = newNode;
	}
```

> Python

```python
    def insertBegin(self, data: str) -> None:
        if self.head is None:
            self.insert(data)
            return

        newNode: Node = Node(data)
        newNode.next = self.head
        self.head = newNode
```

### deleteBegin()

-    This method deletes the element at the beginning.
-    Check if `head == null` then return
-    `head = head.next`

> Java

```java
public void deleteBegin() {
        if (head == null) {
            return;
        }
        head = head.next;
    }
```

> Typescript

```typescript
deleteBegin() {
		if (this.head == null) return;
		this.head = this.head.next;
	}
```

> Python

```python
    def deleteBegin(self) -> None:
        if self.head is None:
            return

        self.head = self.head.next
```

### insertAt(data, index)

-    This method inserts an element at the given index.
-    if `head == null` then return
-    initialize `ptr` as head.
-    loop for `0` from `0` to `index`
     -    `ptr = ptr.next`
-    create `newNode` using data
-    `newNode.next = ptr.next`
-    `ptr.next = newNode`

> Java

```java
public void insertAt(String data, int index) {
        if (head == null) {
            insert(data);
            return;
        }
        Node newNode = new Node(data);
        Node ptr = head;
        for (int i = 0; i < index; i++) {
            if (ptr == null) {
                System.out.println("Unreachable index");
                return;
            }
            ptr = ptr.next;
        }
        newNode.next = ptr.next;
        ptr.next = newNode;
    }
```

> Typescript

```typescript
insertAt(data: string, index: number) {
		if (this.head == null) {
			this.insert(data);
		}
		let ptr: MyNode | null = this.head;
		for (let i = 0; i < index; i++) {
			if (ptr == null) {
				console.log('index not present');
			} else {
				ptr = ptr.next;
			}
		}
		let newNode: MyNode = new MyNode(data);
		if (ptr) {
			newNode.next = ptr.next;
			ptr.next = newNode;
		}
	}
```

> Python

```python
    def insertAt(self, data: str, index: int) -> None:
        if self.head is None:
            self.insert(data)
            return
        newNode: Node = Node(data)
        ptr: Node = self.head
        for i in range(index):
            if ptr is None:
                print("List ended before index")
                return
            ptr = ptr.next

        newNode.next = ptr.next
        ptr.next = newNode
```

### deleteAt(index)

-    This method deletes element at specific index.
-    check if `head == null` then return
-    initialize `ptr` as `head.next` and `prevPtr` as head
-    loop for `i` from `0` to `index`
-    `ptr = ptr.next`
-    `prevPtr = prevPtr.next`
-    `prevPtr.next = ptr.next`

> Java

```java
public void deleteAt(int index) {
        if (head == null) {
            return;
        }
        Node ptr = head.next;
        Node prevPtr = head;
        for (int i = 0; i < index; i++) {
            if (ptr == null) {
                System.out.println("Unreachable index");
                return;
            }
            ptr = ptr.next;
            prevPtr = prevPtr.next;
        }
        prevPtr.next = ptr.next;
    }
```

> Typescript

```typescript
deleteAt(index: number) {
		if (this.head == null) {
			return;
		}
		let ptr: MyNode | null = this.head.next;
		let prevPtr: MyNode | null = this.head;
		for (let i = 0; i < index; i++) {
			if (ptr == null) {
				console.log('index not present');
			} else {
				ptr = ptr.next;
				prevPtr = prevPtr.next as MyNode;
			}
		}
		if (ptr) prevPtr.next = ptr.next;
	}
```

> Python

```python
def deleteAt(self, index: int) -> None:
        if self.head is None:
            return

        ptr: Node = self.head.next
        prevPtr: Node = self.head
        for i in range(index):
            if prevPtr is None:
                print("List ended before index")
                return
            ptr = ptr.next
            prevPtr = prevPtr.next

        prevPtr.next = ptr.next
```

### display()

-    This method traverse the list and prints elements.
-    initialize `ptr` as head
-    loop while `ptr != null`
     -    print `ptr.data`
     -    update `ptr = ptr.next`

> Java

```java
public void display() {
        Node ptr = head;
        while (ptr != null) {
            System.out.println(ptr.data);
            ptr = ptr.next;
        }
    }
```

> Typescript

```typescript
display() {
		let ptr: MyNode | null = this.head;
		while (ptr != null) {
			console.log(ptr.data);
			ptr = ptr.next;
		}
	}
```

> Python

```python
    def display(self) -> None:
        ptr: Node | None = self.head
        while ptr is not None:
            print(ptr.data)
            ptr = ptr.next
```
