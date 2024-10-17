# FutureAI API - Python Package for Lower Division Students (In Development)
Author: [Ramis.H](https://github.com/ramizik), [Yucheng.A](https://github.com/Yucheng-An), [Bekzhan.A](https://github.com/theonlybex)

GitHub Repo: https://github.com/comp-229/api-design-2023-futureai.git

## Introduction

&nbsp;&nbsp;&nbsp;&nbsp;FutureAI combines several API functions that can be helpful to regular students while studying undergraduate computer science.
Instead of implementing the function from scratch, we offer students to use our API, which will save their precious time.

## Getting started
Package Installation 
```zsh
pip install git+https://github.com/comp-229/api-design-2023-futureai.git/TreeHelper
```
Usage:
```python
import TreeHelper (...)
```
`...` present functions and methods in API. Detail please click [HERE](Documentation/TreeHelper.md)

**OR**

```zsh
git clone https://github.com/comp-229/api-design-2023-futureai.git
```
Get in directory
```zsh
cd Futureai
```
Using Python3 run target file
```zsh
python3 userAPI.py
```


### API File Structure

Repo - \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`main.py` - Manual test API file\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`userAPI.py` - Interface for users to interact with API via CLI\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`image` - keep the image files\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`UnitTest` - keep all test file\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`TreeHelper` - keep the original API code\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Documentation` - keep API_Documentation


## File Structure Diagram
![File Diagram](Image/fileDiagram.png)
*User interaction diagram in development*


## Tree Helper API
**Description:**

Tree Structures are usually unclear for lower division students. The **TreeHelper** provide several Class and Functions help students visualize and gain a better understanding of tree structures. Our API simplifies the creation, manipulation, and traversal of binary tree.\

Binary rees are often built using lists for simplicity. In our API, the list2Tree function converts a list of elements into a binary tree. Each element from the list becomes a node in the tree, and the nodes are being arranged following the order of insertion (Balanced vs Unbalanced tree).\

Trees have several advantages:
- Efficient searching/sorting
- Balancing for perfomance
- Flexibility (Dynamic: grows and shrink as needed)

------------------------------------------------------------

| Methods       | Type     | Explanation                      |
|---------------|----------|----------------------------------|
| TreeNode      | Class    | A Class construct Tree structure |
| list2Tree     | Function | Convert List to Tree             |
| tree2List     | Function | Convert Tree to List             |
| findNode      | Function | Find the TreeNode in Tree        |
| depthOfTree   | Function | Get Tree depth                   |
| isBalance     | Function | Check if Tree is balanced        |
| insertNode    | Function | Insert TreeNode to Tree          |
| deleteNode    | Function | Delete TreeNode from Tree        |
| mergeTrees    | Function | Merge two Trees into new Tree    |


## TreeNode Class

Since Python3 doesn't have build-in Tree structure. Class `TreeNode` proved Tree structure for each function usage.

Instance Attributes:

`self.val` - Store the node value\
`self.left` - Point to left node\
`self.right` - Point to right node

Instance Method:

`printTree` - Print structure based on `self.val` in terminal


## Functions
### 1. list2Tree
**Description**: Converts a list of integers or strings into a binary tree. Either creates a balanced
tree or constructs one using a specified `root`, depending on `balance` argument.

```python
list2Tree(inputList: list[str | int], root: str | int = None, balance: bool = False) -> TreeNode
```
__Arguments:__

`inputList (str | number)` - input list convert to tree

`root: str | int` - Assign specified root or not. Default is `None`

__Return:__

`TreeNode[TreeNode]` -  A TreeNode start from root

__Exceptions:__

`TypeError` - Raised when the input list contains mixed types (both strings and integers). The list must consist
entirely of either strings or integers.

`ValueError` - Raised if the input list is empty or balance is False and no root node is provided.

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
balance_tree = TreeHelper.list2Tree(num_list, balance=True)
balance_tree.printTree()
```
__Terminal Output:__

![list2Tree_Output](/Image/list2Tree_Output.jpg)



### 2. tree2List:
**Description**: Convert tree to list in certain order such as inorder, preorder,  postorder
```python
tree2List(root: TreeNode, traversal_type: str = 'inorder') -> list[str | int]
```
__Arguments:__

`root (TreeNode)` -The root node of the tree.

`traversal_type (str, optional)` - The type of traversal (`inorder`, `preorder`, `postorder`). Default is `inorder`

__Return:__

`list[str | int]` -  A list of values from the tree based on the chosen traversal

__Exceptions:__

`ValueError` - If an invalid traversal type is provided

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
balance_tree = TreeHelper.list2Tree(num_list, balance=True)
list1 = TreeHelper.tree2List(balance_tree, "preorder")
list2 = TreeHelper.tree2List(balance_tree, "inorder")
list3 = TreeHelper.tree2List(balance_tree, "postorder")
print(f"\nPreorder Tree: {list1}")
print(f"\nInorder Tree: {list2}")
print(f"\nPostorder Tree: {list3}")
```
__Terminal Output:__

![tree2List_Output](/Image/tree2List_Output.jpg)

### 3. findNode:
**Description**: Finds a node with the specified value in the tree
```python
findNode(root: TreeNode, value: str | int) -> TreeNode | None
```
__Arguments:__

`root (TreeNode)` -The root node of the tree

`value (str | int)` - Target value search

__Return:__

`TreeNode | None` -  The node with the specified value, or None if not found

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
balance_tree = TreeHelper.list2Tree(num_list, balance=True)
TreeHelper.findNode(balance_tree, 40).printTree()
```
__Terminal Output:__

![findNode_Output](/Image/findNode_Output.jpg)

### 4. depthOfTree:
**Description**: Calculates the depth (height) of the binary tree
```python
depthOfTree(root: TreeNode) -> int
```
__Arguments:__

`root (TreeNode)` -The root node of the tree

__Return:__

`int` -  The depth of the tree. Returns `0` if the tree is empty

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
balance_tree = TreeHelper.list2Tree(num_list, balance=True)
print(f"balance_tree depth: {TreeHelper.depthOfTree(balance_tree)}")
```
__Terminal Output:__

![depthOfTree_Output](/Image/depthOfTree_Output.jpg)


### 5. isBalance:
**Description**: Determines if the binary tree is balanced
```python
isBalanced(root: TreeNode) -> bool
```
__Arguments:__

`root (TreeNode)` -The root node of the tree

__Return:__

`bool` -  Tree is balance, `True`. Tree is NOT balance, `False`

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
balance_tree = TreeHelper.list2Tree(num_list, balance=True)
unbalance_tree = TreeHelper.list2Tree(num_list,20, balance=False)
print(f"\nbalance_tree is balance: {TreeHelper.isBalanced(balance_tree)}")
print(f"\nunbalance_tree is balance: {TreeHelper.isBalanced(unbalance_tree)}")
```
__Terminal Output:__

![isBalance_Output](/Image/isBalance_Output.jpg)

### 6. insertNode:
**Description**: Inserts a node with the given value into a binary search tree. If the tree is empty, the value becomes the root.
```python
insertNode(root: TreeNode, value: str | int) -> TreeNode
```
__Arguments:__

`root (TreeNode)` - The root node of the tree.
`value (str | int)` - The value to be inserted into the tree.

__Return:__

`TreeNode` - A TreeNode representing the updated tree after insertion.

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
tree = TreeHelper.list2Tree(num_list, balance=False, root=30)
print("\nTree before insertion:")
tree.printTree()
print("\nInserting value 25...")
updated_tree = TreeHelper.insertNode(tree, 25)
print("\nTree after insertion:")
updated_tree.printTree()
```
__Terminal Output:__

![insertNode_Output](/Image/insertNode_Output.jpg)


### 7. deleteNode:
**Description**: Deletes a node with the given value from the binary search tree. If the value is not found, it returns the original tree.
```python
deleteNode(root: TreeNode, value: str | int) -> TreeNode | None
```
__Arguments:__

`root (TreeNode)` - The root node of the tree.
`value (str | int)` - The value to be deleted from the tree.

__Return:__

`TreeNode | None` - A TreeNode representing the updated tree after deletion, or None if the tree becomes empty.

__Usage Sample__

```python
import TreeHelper
num_list = [30, 20, 40, 10, 35, 50, 5]
tree = TreeHelper.list2Tree(num_list, balance=False, root=30)
print("\nTree before deletion:")
tree.printTree()
print("\nDeleting value 20...")
updated_tree = TreeHelper.deleteNode(tree, 20)
print("\nTree after deletion:")
updated_tree.printTree()
```

__Terminal Output:__

![deleteNode_Output](/Image/deleteNode_Output.jpg)

### 8. mergeNode:
**Description**:
```python
mergeTrees(tree1: TreeNode | None, tree2: TreeNode | None) -> TreeNode
```
__Arguments:__

`tree1 (TreeNode)` - The first input tree to merge.
`tree2 (TreeNode)` - The second input tree to merge.

__Return:__

`TreeNode` - A TreeNode representing the merged tree.

__Usage Sample__

```python
import TreeHelper
num_list1 = [30, 20, 40, 10, 35, 50, 5]
num_list2 = [25, 15, 45, 60, 35, 55]
tree1 = TreeHelper.list2Tree(num_list1, balance=True)
tree2 = TreeHelper.list2Tree(num_list2, balance=True)
print("\nFirst Tree 1:")
tree1.printTree()
print("\nSecond Tree 2:")
tree2.printTree()
print("\nStart merging two trees:")
merged_tree = TreeHelper.mergeTrees(tree1, tree2)
print("\nMerged Tree:")
merged_tree.printTree()
```
__Terminal Output:__

![mergeTrees_Output](/Image/mergeTrees_Output.jpg)
