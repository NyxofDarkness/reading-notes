# Reading:15-Trees

## This is all about binary, and binary search trees

|Terminology|Definitions|
|---|---|
|Node | A node is the individual item/data that makes up the data structure|
|Root | The root is the first/top Node in the tree|
|Left Child | The node that is positioned to the left of a root or node|
|Right Child | The node that is positioned to the right of a root or node|
|Edge | The edge in a tree is the link between a parent and child node|
|Leaf | A leaf is a node that does not contain any children|
|Height | The height of a tree is determined by the number of edges from the root to the bottommost node|


> two categories of traversals when it comes to trees:

|Depth First|we prioritize going through the depth (height) of the tree first|
|---|---|
|Pre-order| root >> left >> right|
|In-order| left >> root >> right|
|Post-order| left >> right >> root|

``` python
ALGORITHM preOrder(root)

  OUTPUT <-- root.value

  if root.left is not NULL
      preOrder(root.left)

  if root.right is not NULL
      preOrder(root.right)
```

- Breadth First- iterates through the tree by going through each level of the tree node-by-node

### Binary Trees restrict the number of children to two

> The Big O time complexity for inserting a new node is O(n). Searching for a specific node will also be O(n). Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve traversing the entire tree

> The Big O time complexity of a Binary Search Tree’s insertion and search operations is O(h), or O(height). In the worst case, we will have to search all the way down to a leaf, which will require searching through as many nodes as the tree is tall