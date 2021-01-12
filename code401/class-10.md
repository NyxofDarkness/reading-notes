# Read: Stacks and Queues

|The Thing | The Things Explaination|
|---|---|
|What is a Stack | A stack is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous.|
|FILO |  the first item added in the stack will be the last item popped out of the stack|
|LIFO | last item added to the stack will be the first item popped out of the stack.|
|Stack Visualization | he topmost item is denoted as the top. When you push something to the stack, it becomes the new top. When you pop something from the stack, you pop the current top and set the next top as top.next|
|Push O(1) | Pushing a Node onto a stack will always be an O(1) operation|
|Pop O(1) | Popping a Node off a stack is the action of removing a Node from the top, Typically, you would check isEmpty before conducting a pop. This will ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block|
|Peek O(1) | When conducting a peek, you will only be inspecting the top Node of the stack|
|IsEmpty O(1) | check out the pseudocode for isEmpty below|
|What is a Queue | Common terminology for a queue is below|
|FIFO | first item in the queue will be the first item out of the queue.|
|LILO |  last item in the queue will be the last item out of the queue|
|Enqueue O(1) | see code below!|
|Dequeue O(1) | When you remove an item from a queue, you use the dequeue action.|
|Peek O(1) | When conducting a peek, you will only be inspecting the front Node of the queue.|
|IsEmpty O(1) | checks to make sure stack isnt empty to ensure that an exception is not raised. Alternately, you can wrap the call in a try/catch block.|

> Terminology:

1. Push - Nodes or items that are put into the stack are pushed
2. Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.
3. Top - This is the top of the stack.
4. Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
5. IsEmpty - returns true when stack is empty otherwise returns false.

Adding a node to the stack: Push it into the stack by assigning it as the new top, with it's next property equal to the original top.

> walking through the steps:

1. Have node that you want to push into the stack
2. assign the next property of Node 5 to reference the same Node that top is referencing: Node 4
3. re-assign our reference top to the newly added Node, Node 5.

example:

``` python
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
   ```

``` python
ALGORITHM pop()
// INPUT <-- No input
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   Node temp <-- top
   top <-- top.next
   temp.next <-- null
   return temp.value
   ```

``` python
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   return top.value
   ```

``` python
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return top = NULL
```

> Common terminology for a queue:

1. Enqueue - Nodes or items that are added to the queue.
2. Dequeue - Nodes or items that are removed from the queue. If called 3. when the queue is empty an exception will be raised.
3. Front - This is the front/first Node of the queue.
4. Rear - This is the rear/last Node of the queue.
5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
6. IsEmpty - returns true when queue is empty otherwise returns false.

> Here is the pseudocode for the enqueue method:

``` python
ALGORITHM enqueue(value)
// INPUT <-- value to add to queue (will be wrapped in Node internally)
// OUTPUT <-- none
   node = new Node(value)
   rear.next <-- node
   rear <-- node
   ```

> Here is the pseudocode for the dequeue method:

``` python
ALGORITHM dequeue()
// INPUT <-- none
// OUTPUT <-- value of the removed Node
// EXCEPTION if queue is empty

   Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value
   ```

> Here is the pseudocode for a peek

``` python
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of the front Node in Queue
// EXCEPTION if Queue is empty

   return front.value
   ```

> Here is the pseudocode for isEmpty

``` python
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return front = NULL
```