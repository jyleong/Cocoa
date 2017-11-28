+++
title = "Your code's use cases"
date = "2017-11-26T20:10:38-08:00"
draft = false

+++

So today we are going to discuss when you write classes or methods, how they are going to be used. When thinking about that, this leads into testing your methods and figuring out the acceptable cases to use/invoke your methods and classes. We also want to consider the necessary setup conditions before you use a particularly method and the after effects after it runs.

**For our example in the blog, let's go with implementing a queue class and a dequeue method:**

Important aspects when it comes to good methods are how you imagine its implementation and how we view its edge cases. What would happen if the programmer using our queue class attempts to use dequeue on an empty queue? There are two ways this can be approached, the creator of the class can treat this behaviour as an error. If that is the case, users of this method are plainly forbidden on dequeueing an empty queue. The other answer is that the designer of the calss and method decides to let this behaviour work, but makes the method robust with a way to handle teh failure, like returning a null.

I think the way it goes when figuring out the use cases of your code is knowing the purpose of the class and method, and the programmer using said class should understand and agree with how its suppose to be used.

So let's say that the _precondition_ is something that has to be true before you can use the piece of code, if its not true. Then the outcome of the code is up to the programmer to handle afterwards. Then a _postcondition_ is the condition the piece of code guarantees to happen always after it is run.

Here we can write our method given a precondition that the size must be greater than 0:

```java
/**
	Remove and return first element of queue
	@precondition size() > 0
*/
public <T> dequeue() {
	return elements.remove(0);
}
```

Well, the documentation is nice but this method here makes no promises what happens when we call it on an empty queue. We would probably get an IndexOutOfBoundsException. Then the program would terminate.

A good practice when following our precondtion is to make sure its checkable by the caller. Here we can make a method to check if its empty. I will revisit this isEmpty() method later.

```java
/**
	@return true is the size == 0
*/
public boolean isEmpty() {
	return this.size() == 0;
}
```

When we implement some code with expected and unexpected behaviour, what should you do if you call the method with its precondition unfulfilled? How are you going to make sure its doing what you want it to do? Well, some programmers would go abouts and do nothing. 

We could use asserts, exceptions or have a guard before using the method to check its precondition. Or else the user of class should check the precondition of the method before using it.

With *assertions* lots of languages have it in some shape or form. It is primarily used for small unit testing but designing and implementing a method with preconditions is a use case for assertions. Assertions would help detect if something went wrong, then provide a message. Here is an example of how I would put it into our dequeue method.

```java
/**
	Remove and return first element of queue
	@precondition size() > 0
*/
public <T> dequeue() {
	assert this.size() > 0: "Queue size must be > 0";
	return elements.remove(0);
}
```

If a user calls this method on an empty queue, the program terminates with this assertion error.

Another viable option sometimes is to avoid checking the condition and instead return null when it violates the condition, like in the case of our dequeue() method, it returns a object. We will also use our isEmpty() method from up top.

```java
/**
	Remove and return first element of queue
	@precondition size() > 0
*/
public <T> dequeue() {
	if (this.isEmpty()) return null;
	return elements.remove(0);
}
```

That is one way, but it wont help the user any further. The null value could cause problems later, and make the error even more ambiguous down the road.

Another option for dealing with errors are throwing exceptions, here is an example:

```java

public <T> dequeue() {
	if (this.size() == 0) 
		throw new NoSuchElementException("Must have size > 0");
	return elements.remove(0);
}
```

Like assertions, they cannot be turned off and will run in your code, thehy are meant to be caught and somehow handled later on. So we have different ways to handle unexpected behaviours in code, and we have to think about how they are used. When is a good example to use exceptions? Well, what about a method or class that deals with file I/O? It would make sense to check and throw a FileNotFOundException is the file doesn't exist. Compared to a queue, existence of a certain file is not easy to check compared to the size of a queue, so throwing the exception is a better way to handle this case.

The three top examples here with how to handle the error cases in dequeue is what we could call the 'guard' code in the method. To check if we fulfill the precondition to continue on with the method. This is entirely appropriate to write when starting to write code used in enterprise. Sometimes we do not know when the methods we write will be used in other cases.  

In development, we usually promise that every operation does the right thing, provided we meet the precondition. Like the dequeue method promises to return the first element in the queue, the promise is the postcondition. We generalize the definition of the postcondition  as the condition the method promises to fulfill after it is done its operation.

These things are something that I am trying to habitualize myself as I am writing more and more code to be used in production and for other colleagues. I am also being mindful when I'm using their existing code, there could be side effects or consequences. So I have to be conscious of whats happening, instead of blindly copy pasting.

That is all for today : ).