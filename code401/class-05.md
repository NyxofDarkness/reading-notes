# Linked Lists

## Read: Linked Lists

> Linked List - A data structure that contains nodes that links/points to the next node in the list.
> Singly - Singly refers to the number of references the node has. A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.
> Doubly - Doubly refers to there being two (double) references within the node. A Doubly linked list means that there is a reference to both the Next and Previous node.
> Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.
> Next - Each node contains a property called Next. This property contains the reference to the next node.
> Head - The Head is a reference type of type Node to the first node in a linked list.
> Current - The Current reference is a reference type of type Node that is currently being looked at. This node is traditionally used when traversing through a full linked list. When traversing, you typically reset the current to the head to guarantee you are starting from the beginning of the linked list.

> Next value in each node to guide us where the next reference is pointing. important because it will lead us where the next node is

```
		ALGORTIHM Includes (value)
		// INPUT <-- integer value
		// OUTPUT <-- boolean
			
			Current <-- Head

			WHILE Current is not NULL
				IF Current.Value is equal to value
					return TRUE

				Current <-- Current.Next

			return FALSE
          
```

> I love this example of how to account for the Big O:


``` Big O
The Big O of time for Includes would be O(n). This is because, at its worse case, the node we are looking for will be the very last node in the linked list. n represents the number of nodes in the linked list.

The Big O of space for Includes would be O(1). This is because there is no additional space being used than what is already given to us with the linked list input.
```

> ere are the required steps to add a new node with an O(1) efficiency.

1. Set Current equal to Head. This will guarantee us that we are starting from the very beginning.
2. We can then instantiate the new node that we are adding. The values passed in as arguments into the Add() method will define what the value of the Node will be.

> adding a node

```

		ALGORITHM Add(newNode)
		// INPUT <-- Node to add 
		// OUTPUT<-- No output

			Current <-- Head
			newNode.Next <-- Head
			Head <-- newNode
			Current <-- Head

```

> Now let’s start the adding. We can do an AddBefore method or an AddAfter. For this documentation, we will do an AddBefore. The AddAfter is extremely similar…see if you can figure it out on your own!

> Here is the Pseudo code for an AddBefore method in a linked list

```

Here is the Pseudo code for an AddBefore method in a linked list

		ALGORITHM AddBefore(newNode, existingNode)
		// INPUT <-- New Node, Existing Node
		// OUTPUT <-- No Output

			Current <-- Head

			while Current.Next is not equal to NULL
				if Current.Next.Value is equal to existingNode.Value
					newNode.Next <-- existingNode
					Current.Next <-- newNode

				Current <-- Current.Next;	

```

> Print out nodes

```

		ALGORITHM Print()
		// INPUT <-- None
		// OUTPUT <-- string to console

			Current <-- Head

			while Current.Next is not equal to NULL
				OUTPUT <-- "Current.Value --> "
				Current <-- Current.Next

			OUTPUT <-- "Current.Value --> NULL"

```
