# Stack

A data structure in which elements are organised in a sequence is called linear data structure.
<br>
It thus follows the Last-In-First-out (LIFO)
principle.
<br> In Other words :
<br>

 A stack is a **linear, ordered collection** of elements that follows the **LIFO (Last In, First Out)** principle.

 ![stack_example](https://github.com/user-attachments/assets/99127a93-bdd0-4f27-8e08-b995a1bfd747)


## Some examples of application of stack in programming are as follows:<br>

• When we need to reverse a string, the string is
traversed from the last character till the first
character. i.e. characters are traversed in the reverse
order of their appearance in the string. This is very
easily done by putting the characters of a string in
a stack.<br>
• We use text/image editor for editing the text/image
where we have options to redo/undo the editing
done. When we click on the redo /undo icon, the
most recent editing is redone/undone. In this
scenario, the system uses a stack to keep track of
changes made.<br>
• While browsing the web, we move from one web page
to another by accessing links between them. In order
to go back to the last visited web page, we may use the
back button on the browser. Let us say we accessed
a web page P1 from where we moved to web page P2
followed by browsing of web page P3. Currently, we
are on web page P3 and want to revisit web page P1.
We may go to a previously visited web page by using
the BACK button of the browser. On clicking the
BACK button once, we are taken from web page P3
to web page P2, another click on BACK shows web
page P1. In this case, the history of browsed pages is
maintained as stack.<br>
• While writing any arithmetic expression in a program,
we may use parentheses to order the evaluation
of operators. While executing the program, the
compiler checks for matched parentheses i.e. each
opening parenthesis should have a corresponding
closing parenthesis and the pairs of parentheses
are properly nested. In case of parentheses are
mismatched, the compiler needs to throw an error.
To handle matching of parentheses, stack is used.
<br>

## Operations On Stack

The end from which elements are added or
deleted is called TOP of the stack. Two fundamental
operations performed on the stack are PUSH and POP.

![stack_operation](https://github.com/user-attachments/assets/b8c38a52-d97a-4330-8147-ca9eb61162c6)


### PUSH and POP Operations

• **_PUSH_** adds a new element at the _TOP_ of the stack.
It is an insertion operation. We can add elements
to a stack until it is full. A stack is full when no
more elements can be added to it. Trying to add an
element to a full stack results in an exception called
‘**overflow**’.

• **_POP_** operation is used to remove the top most element
of the stack, that is, the element at the _TOP_ of the
stack. It is a delete operation. We can delete elements
from a stack until it is empty i.e. there is no element
in it. Trying to delete an element from an empty stack
results in an exception called ‘**underflow**’.
<br>
A stack is used to insert and delete elements in LIFO order.




* **Implementation:**
  In Python, a stack can be implemented using a **list**.

  * `append()` → adds an element to the top (right end).
  * `pop()` → removes an element from the top (right end).
    No explicit `TOP` variable is needed.

---

### **Main Stack Operations (Functions)**

1. **Create an empty stack**

   ```
   glassStack = list()
   ```

2. **Check if stack is empty**

   ```
   def isEmpty(glassStack):
       return len(glassStack) == 0
   ```

3. **Push (Insert element)**

   ```
   def opPush(glassStack, element):
       glassStack.append(element)
   ```

4. **Pop (Remove top element)**

   ```
   def opPop(glassStack):
       if isEmpty(glassStack):
           print("Underflow")
           return None
       else:
           return glassStack.pop()
   ```

5. **View top element**

   ```
   def top(glassStack):
       if isEmpty(glassStack):
           print("Stack is empty")
           return None
       else:
           return glassStack[-1]
   ```

6. **Get stack size**

   ```
   def size(glassStack):
       return len(glassStack)
   ```

7. **Display all elements**

   ```
   def display(glassStack):
       print("Current elements in stack:")
       for item in reversed(glassStack):
           print(item)
   ```

---

### **Example Usage**

```
glassStack = list()
opPush(glassStack, 'glass1')
opPush(glassStack, 'glass2')
print("Size:", size(glassStack))
print("Popped:", opPop(glassStack))
opPush(glassStack, 'glass3')
print("Top element:", top(glassStack))
display(glassStack)
```

