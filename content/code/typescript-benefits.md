+++
title = "The benefits of Typescript"
date = "2018-02-25T12:08:51-08:00"
draft = false

+++

## Classes

Like C++/Java/C#, Typescript is purely object oriented, development in Typescript is by classes

Here is an example of a valid Typescript class:
```
Class Employee {
    private firstName: string;
    private lastName: string;
    private email: string;
    private address?: string;
    private department?: string;
}

```

Also, you can have constructors:
```
Constructor(firstName: string, lastName:string, email: string) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.email = email
}
```

Also notice that address and department can be optional (could be unassigned/null)


## Interfaces

You can also define interfaces to be implemented!

```
interface myType {
    color: string;
    point1: number;
    point2: number;

}
```

This isn't the greatest example but think of interfaces for react properties...

We defined set types, have the specific props or state implement and adhere to the interface. Then you don't have to deal with any kind of prop type checking down the road.


At the moment these are some small examples. However, having typing in javascript will make your programs and apps more robust.