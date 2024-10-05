### ODR(One definition Rule)
is a fundamental rule in C and C++ that establishes that each entity (function, variable, class, etc.) must have exactly **one definition**. 

**Single definition rule**
```c
int x = 10;
int x = 20; //Multiple definition error
```

**Multiple declarations is allow** 

```c
//a1.h(archive)
extern int myIntVar; //declaration withou allocate memory

//a2.h(another arcvhie)
int myIntVAr = 45; //definition locatted memory
```

is important to notice the difference between ==declaration== that can be done once and ==definition== that can be multiple times.
