# Tree

## Node

-    Each element in a tree is called as `Node`. It contains a data and address
     of next 2 nodes named left and right.
-    Create a constructor which takes `data` as parameter and assigns left and
     right as null;

> Java

```java
class Node {
    String data;
    Node left;
    Node right;

    public Node(String data) {
        this.data = data;
        this.left = null;
        this.right = null;
    }
}
```

> Typescript

```typescript
class TreeNode {
	data: string;
	left: TreeNode | null;
	right: TreeNode | null;

	constructor(data: string) {
		this.data = data;
		this.left = null;
		this.right = null;
	}
}
```

> Python

```python
class Node:
    def __init__(self, data: str):
        self.data: str = data
        self.left: Node | None = None
        self.right: Node | None = None

```

## Tree

-    It is the class which will be treated as actual `Tree`. This class will
     contain all the tree method.
-    This class must have a private variable root to track the root of tree.
-    There must be a constructor which initializes root as null.

> Java

```java
public class Tree {
    private Node root;

    public Tree() {
        this.root = null;
    }
}
```

> Typescript

```typescript
class Tree {
	root: TreeNode | null;
	constructor() {
		this.root = null;
	}
}
```

> Python

```python
class Tree:
    def __init__(self):
        self.root: Node | None = None
```

### Traversal

-    There are 4 type of traversal methods
     1.   PreOrder `root` -> `left` -> `right`
     2.   InOrder `left` -> `root` -> `right`
     3.   PostOrder `left` -> `right` -> `root`
     4.   Level Order i.e traversing level wise

#### PreOrder

-    The traversing format should be `root` -> `left` -> `right`.
-    create a function `preorder` which takes `root` as parameter.
     -    check if `root == null` then return
     -    print `root.data`
     -    call `preorder` for `root.left`
     -    all `preorder` for `root.right`

> Java

```java
private void preorder(Node root) {
        if (root == null) {
            return;
        }
        System.out.println(root.data);
        preorder(root.left);
        preorder(root.right);
    }
```

> Typescript

```typescript
preorder(root?: TreeNode | null) {
		if (root !== undefined) {
			if (root === null) return;
			console.log(root.data);
			this.preorder(root.left);
			this.preorder(root.right);
		} else {
			this.preorder(this.root);
		}
	}
```

> Python

```python
    def __preorder(self, root: Node | None):
        if root is None:
            return
        print(root.data)
        self.__preorder(root.left)
        self.__preorder(root.right)
```

#### InOrder

-    The traversing format should be `left` -> `root` -> `right`.
-    create a function `inorder` which takes `root` as parameter.
     -    check if `root == null` then return
     -    call `inorder` for `root.left`
     -    print `root.data`
     -    call `inorder` for `root.right`

> Java

```java
private void inorder(Node root) {
        if (root == null) {
            return;
        }
        inorder(root.left);
        System.out.println(root.data);
        inorder(root.right);
    }
```

> Typescript

```typescript
inorder(root?: TreeNode | null) {
		if (root !== undefined) {
			if (root === null) return;
			this.inorder(root.left);
			console.log(root.data);
			this.inorder(root.right);
		} else {
			this.inorder(this.root);
		}
	}
```

> Python

```python
    def __inorder(self, root: Node | None):
        if root is None:
            return
        self.__inorder(root.left)
        print(root.data)
        self.__inorder(root.right)
```

#### PostOrder

-    The traversing format should be `left` -> `right` -> `root`.
-    create a function `postorder` which takes `root` as parameter.
     -    check if `root == null` then return
     -    call `postorder` for `root.left`
     -    call `postorder` for `root.right`
     -    print `root.data`

> Java

```java
private void postorder(Node root) {
        if (root == null) {
            return;
        }
        postorder(root.left);
        postorder(root.right);
        System.out.println(root.data);
    }
```

> Typescript

```typescript
postorder(root?: TreeNode | null) {
		if (root !== undefined) {
			if (root === null) return;
			this.postorder(root.left);
			this.postorder(root.right);
			console.log(root.data);
		} else {
			this.postorder(this.root);
		}
	}
```

> Python

```python
    def __postorder(self, root: Node | None):
        if root is None:
            return

        self.__postorder(root.left)
        self.__postorder(root.right)
        print(root.data)
```

#### Level Order

-    This method traverse the tree level wise.
-    create an empty `queue`.
-    First push `root` and `null`.
-    Loop while `!queue.isEmpty()` i.e queue is not empty
     -    initialize `curNode` by popping from queue.
     -    Check if `curNode == null`
          -    if `queue.isEmpty()` then return
          -    else print newline and update `curNode`

> Java

```java
public void levelWise() {
        Queue<Node> queue = new LinkedList<>();
        queue.add(root);
        queue.add(null);

        while (!queue.isEmpty()) {
            Node current = queue.poll();

            if (current == null) {
                if (queue.isEmpty()) {
                    return;
                } else {
                    queue.add(null);
                    System.out.println();
                }
            } else {
                System.out.print(current.data + "\t");
                if (current.left != null)
                    queue.add(current.left);
                if (current.right != null)
                    queue.add(current.right);
            }

        }
    }
```

```typescript
levelOrder() {
		let queue: Array<TreeNode | null> = [];
		queue.push(this.root);
		queue.push(null);
		let opStr: string = '';
		while (queue.length !== 0) {
			let curNode: TreeNode | null = queue.shift() as TreeNode | null;
			if (curNode === null) {
				if (queue.length === 0) {
					console.log(opStr);
					return;
				} else {
					queue.push(null);
					console.log(opStr);
					opStr = '';
				}
			} else {
				opStr += curNode.data + '\t';
				if (curNode.left) queue.push(curNode.left);
				if (curNode.right) queue.push(curNode.right);
			}
		}
	}
```

```python
def level_order(root: Node | None):
    queue: list = [root, None]

    while len(queue) != 0:
        currNode: Node | None = queue[0]
        if currNode is None:
            queue.remove(currNode)
            print()
            if len(queue) == 0:
                return
            else:
                queue.append(None)
            currNode = queue[0]

        print(queue[0].data, end="   ")

        if currNode.has_left():
            queue.append(currNode.left)

        if currNode.has_right():
            queue.append(currNode.right)

        queue.remove(currNode)

```
