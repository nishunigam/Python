##Python Scopes and Namespaces

A **namespace** is a mapping from names to objects. Most namespaces are currently implemented as Python dictionaries, but that’s normally not noticeable in any way (except for performance), and it may change in the future.

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
