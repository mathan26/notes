# Data Structures and Algorithms
**Time Complexisty**

 - Asymptotic  runtime or big -O times.
 - Big-O: Upper bound
 - Big Omega - Lower Bound
 - Big Theta - Tight Bound Both lower and upper bound
 Cases:
	 - Best case
	 - Worst case
	 - Expected case

**Space Complexity:**

 - Stack space in recurisive calls counts too.
 - In Some case method inside the for loop doesnot mean that take up O(n) space, it will be cleared once it is out of the loop.

**Drop the constants:**

 - O(n) sometimes faster thatn O(1).Big-O Just describes the rate of increase.
 - This is the reason we have to drop the constants.
 - Example program for find the min and max we can write with one for loop or two for loops,so it comes outs like O(n) and O(2n).
 - In Big-O both are represented as same manneer.Just drop the constants.
 
  **Drop the Non Dominant Terms:**
  
 - O(N2 +N+) = O(N2)
 - ![big o cheatsheet](https://jarednielsen.com/static/9c24f10d0295ead7526e32d62fa2eac5/b9e4f/big-o-cheatsheet.png)

**Mutlipart Algorithm:**

 - O(A +B) vs O(A*B)
 - If your algorithm is in the from "do this, then when you're all done, do that" then you add the runtimes
 - If your algorithm is in the form "do this for each item you do that" then multiply the runtimes.
 
 **Amortized Time:**
 
 - Taking cost of operation over extented period of time.
 - Example: ArrayList Insertion
 - https://youtu.be/MTl8djZFWE0

**Log N Runtimes**

 - Example: Binary Search
 - Every time the operation is half of the element and finally reach to the  target that is 1.
 - [O(log n) Explained](https://medium.com/hackernoon/what-does-the-time-complexity-o-log-n-actually-mean-45f94bb5bfbf)

**Recursive Runtime:**

 - Check the Levels and calculartion of node
 - It is not O(n2) it is based on the operation
 - [Code School Explanation](https://youtu.be/ncpTxqK35PI)
------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 1 Introduction
 * Variables 
 * Data Types
 
    ![Data Types In Java(/Images/17 Data Types In Java.PNG)
    
 * Data Structures 
 
   *Once we have data that is stored in the variable we need some mechanism to manipulate the data,*
  
   > Data Structure is a way of storing and organizing data in a computer, so that it can be used efficiently.
   
   Depending on the organization of elements ,DS classified into two types:     
   1 Linear Data Structures
    > Elements are accessed in a sequential order.
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
   2 Non Linear Data Structures
   > Elements of this DS stored/accessed in a non-linear order. 
   
* Abstract Data Type
    > To Simplify the process of solving problems ,we combine the data structures with their operations
    > and are called ADT.
   * Two Parts:    
        * Declaration of Data 
        * Declaration of Operations
* Algorithm
    > An Algorithm is step-by-step instructions to solve a given problem.   
* Analysis of Algorithm
    > It helps us to find which of them is efficient in terms of time and space consumed.
* Goal of Analysis of Algorithm
    >Compare the Algorithms of different solutions.
* Running Time Analysis
    > It is the process of determining how process time increase as the size of the problem.
* Compare Algorithms
    > Running time of given algorithm as a function of input size n.
* Rate of Growth
    > The rate at which running time increase as a function of input is called rate of growth.
    We can igore the small terms when compare with big terms.

* Commonly used Rate of Growths
    
   Time Complexity | Name | Example 
   ------------ | ------------- | -------------
   1 | Constant | Adding Element in the front of the list
   logn | Logarithmic | Finding an element in sorted array
   n | Linear | Finding an element in unsorted array
   nlogn | Linear Logarithmic | sorting n items by 'divide-and-conquer' Mergesort
   n^2 | Quadratic | Shortest path between two nodes in a graph.
   n^3 | cubic | Matrix Multiplication
   2^n | Exponential | The Towers of Hanoi problem
   
  * Comparison from low to high processing,
    > 1 < log log n < √logn < log^2 n < 2^logn < n < log(n!) < n log n < n^2 < 2^n < 4^ < n! <2^2n
      
      
      
* Types of Analysis
    * To analysis the algorithm we need to know what input algorithm takes less time and on what inputs
    it takes huge time.
    * Three types
        * Worst Case (Big O)
            * Defines the input for which algorithm takes huge time.
            * Input is the one for which the algorithm runs slower
        * Best case (Big Omega)
            * Defines the input for which algorithm takes less time
         * Average Case (Theta)
            * Provides prediction about the running time of algorithm
            * input is random.
* Asymptotic Notation
    > Expression for Best ,Worst and Average
* Big-O Notation
    > Find tight upper bound of the given function.The function , f(n) = O(g(n)) iff +ve Constants C and n0
    > such that 
                   
                  f(n) <= C*g(n) for All n>= n0
    
    Example:
        f(n) = 2n + 3
        <br/>
        2n + 3 <= 10n n>=1
    Here C = 10, g(n) = n
    <code> 2n + 3 < = 2n + 3n=5n</code>
          Therefore 
    ```f(n)=O(n)```
    
    * In big-O write closest function i.e near of growth rate of f(n)

# LinkedList

* Successive elements are connected by pointers
* last elements points to null.
* It can shrink or grown execution of the program.
* It doesn't waste memory space.

# LinkedList ADT
* Main
    * Insert
    * Delete
* Auxiliary
    * Delete List
    * Count
    * Find nth

* Why constant time for accessing array elemens?
    * We already know the base address ,using the offset we can find any value.
    * So it takes constant time.
    
        * Advantage of Arrays:
            * simple and easy to use.
            * Faster access to the elements
        * Disadvantage:
            * Fixed size
            * One block allocation
            * Complex position-based insertion
        * Advantage of LinkedList
            * Expanded at constant time.
        * Disadvantage of LinkedList
            * Linear access
            * Hard to manipulate
            * Extra space for memory.
    
    * LinkedList Representation in Java
    
    ```
          class LinkedList {
           Node head; // head of the list
       
           /* Linked list Node*/
           class Node {
               int data;
               Node next;
       
               // Constructor to create a new node
               // Next is by default initialized
               // as null
               Node(int d) { data = d; }
           }
       }
  ```
  * In LinkedList data can be added in,
  
    1  At the front of the linked list
    
    ```
    public void push(int new_data) 
    { 
        /* 1 & 2: Allocate the Node & 
                  Put in the data*/
        Node new_node = new Node(new_data); 
      
        /* 3. Make next of new Node as head */
        new_node.next = head; 
      
        /* 4. Move the head to point to new Node */
        head = new_node; 
    } 
    ```
    > Time complexity of push() is O(1) as it does constant amount of work.
    
    2  After a given node.  
    
    ```
    public void insertAfter(Node prev_node, int new_data) 
    { 
        /* 1. Check if the given Node is null */
        if (prev_node == null) 
        { 
            System.out.println("The given previous node cannot be null"); 
            return; 
        } 
      
        /* 2. Allocate the Node & 
           3. Put in the data*/
        Node new_node = new Node(new_data); 
      
        /* 4. Make next of new Node as next of prev_node */
        new_node.next = prev_node.next; 
      
        /* 5. make next of prev_node as new_node */
        prev_node.next = new_node; 
    } 
    ```
    > Time complexity of insertAfter() is O(1) as it does constant amount of work.
      
    3  At the end of the linked list.
    
    ```
    /* Appends a new node at the end.  This method is  
       defined inside LinkedList class shown above */
    public void append(int new_data) 
    { 
        /* 1. Allocate the Node & 
           2. Put in the data 
           3. Set next as null */
        Node new_node = new Node(new_data); 
      
        /* 4. If the Linked List is empty, then make the 
               new node as head */
        if (head == null) 
        { 
            head = new Node(new_data); 
            return; 
        } 
      
        /* 4. This new node is going to be the last node, so 
             make next of it as null */
        new_node.next = null; 
      
        /* 5. Else traverse till the last node */
        Node last = head;  
        while (last.next != null) 
            last = last.next; 
      
        /* 6. Change the next of last node */
        last.next = new_node; 
        return; 
    } 
    ```
    
    > Time complexity of append is O(n) where n is the number of nodes in linked list. Since there is a loop from head to end, the function does O(n) work.
      This method can also be optimized to work in O(1) by keeping an extra pointer to tail of linked list

#### Doubly Linked List

* Advantage
  * We can navigate in both the direction.
  * Each Node has left and Right pointers, no need to keep pre pointer for delete operation.
* Disadvantage
  * Extra memory space
  * More pointer operation
  
  ```
    // Class for Doubly Linked List 
    public class DLL { 
        Node head; // head of list 
      
        /* Doubly Linked list Node*/
        class Node { 
            int data; 
            Node prev; 
            Node next; 
      
            // Constructor to create a new node 
            // next and prev is by default initialized as null 
            Node(int d) { data = d; } 
        } 
    } 
  ```

### Circular Linked list
  * All node are connected to form a circle.
    
    * Advantage
        * Any node can be starting point, need to stop when first visited node is visited again.
        * Useful for implementation of Queue.
    * Application
        * it is used in the application when repeatedly go around the list. Ex: OS managing list of application.
      
      
   
```
static void traverse(Node last) 
{ 
    Node p; 
  
    // If list is empty, return. 
    if (last == null) 
    { 
        System.out.println("List is empty."); 
        return; 
    } 
  
    // Pointing to first Node of the list. 
    p = last.next; 
  
    // Traversing the list. 
    do
    { 
        System.out.print(p.data + " "); 
        p = p.next; 
  
    } 
    while(p != last.next); 
  
} 
```  

### Stack

> Stack is a linear data structure which follows a particular order in which the operations are performed. The order may be LIFO(Last In First Out) or FILO(First In Last Out).

* Operations:
    * push
    * pop
    * peek or top
    * isEmpty
    
### Queue

> Like Stack, Queue is a linear structure which follows a particular order in which the operations are performed. The order is First In First Out (FIFO).  A good example of queue is any queue of consumers for a resource where the consumer that came first is served first.

* Operations
    * Enqueue
    * Dequeue
    * Front
    * Rear
    
### Tree

* A tree is an Undirected graph with no cycles.
*   Equivalently, a tree it is a connected graph with N nodes and N-1 edges.

##### Examples:
* File system on the computer.
* Social hierarchies.

* when to use tree?
* cost of operation.
### Images
* 18 Tree Indroduction and terminology
* Images\19 Nodes and Edges.PNG
* Images\20 HeightandDepth.PNG
* Images\21 TreePicRepresentation.PNG
* 22 Binary Tree.PNG
* 23 Proper Binary tree.PNG
* 24 complete binary tree.PNG
* 25 maxNode and level.PNG
* 26 Perfect binary tree.PNG
* 27 binary tree and normal tree height comparasion.PNG
* 28 Balanced binary tree.PNG
* 29 balanced binary tree rule.PNG
* 30 binary tree array impl.PNG
* 31 Array LinkedList search comparation for huge data.PNG
* 32 BST comparison.PNG
* 33 BST Rule.PNG
