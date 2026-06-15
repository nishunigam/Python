Instance methods like .__init__() and .__str__() are called dunder methods. This term is short for double-underscore methods and is commonly used in the Python community because these methods begin and end with double underscores (__).

Other names for these methods are special methods and magic methods.

You can use the **isinstance()** function to check if an object is an instance of a specific class.

The function takes two arguments: the object and the class. It returns True if the object is an instance of the class, and False otherwise:
```
isinstance("hello", str)


True
```


The **.speak()** method in the JackRussellTerrier class is an example of both overriding and extending a method from a parent class. It overrides the .speak() method of the Dog parent class by providing a new implementation. However, this new implementation actually calls the original .speak() method of the Dog class using super().speak(sound).

This is an example of extending a method because it provides additional functionality (a default sound) while still maintaining the original behavior of the .speak() method from the Dog class.


## Python Scopes and Namespaces

A **namespace** is a mapping from names to objects. Most namespaces are currently implemented as Python dictionaries, but that’s normally not noticeable in any way (except for performance), and it may change in the future.

In a sense the set of attributes of an object also form a namespace.



**attribute** for any name following a dot — for example, in the expression `z.real`, `real` is an attribute of the object `z`.

references to names in modules are attribute references: in the expression `modname.funcname`, `modname` is a module object and `funcname` is an attribute of it.

**Attributes** may be read-only or writable.

Module attributes are writable: you can write `modname.the_answer = 42`. Writable attributes may also be deleted with the <ins>del</ins> statement. For example, `del modname.the_answer` will remove the attribute `the_answer` from the object named by `modname`.





if <ins>no global or nonlocal</ins> statement is in effect – assignments to names always go into the innermost scope. Assignments do not copy data — they just bind names to objects.

The **global** statement can be used to indicate that particular variables live in the global scope and should be rebound there.

the **nonlocal** statement indicates that particular variables live in an enclosing scope and should be rebound there.

```
def scope_test():
    def do_local():
        spam = "local spam"

    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"

    def do_global():
        global spam
        spam = "global spam"

    spam = "test spam"
    do_local()
    print("After local assignment:", spam)
    do_nonlocal()
    print("After nonlocal assignment:", spam)
    do_global()
    print("After global assignment:", spam)

scope_test()
print("In global scope:", spam)
```

The output of the example code is:
```
After local assignment: test spam
After nonlocal assignment: nonlocal spam
After global assignment: nonlocal spam
In global scope: global spam
```
