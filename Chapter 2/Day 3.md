> 1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.
![image](https://user-images.githubusercontent.com/104716561/168471288-380d9cfe-b573-4b96-ab1a-c2a15091c70d.png)

> 2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!
![image](https://user-images.githubusercontent.com/104716561/168471498-10bef2b8-ce89-4f12-8230-00c0016d5f6a.png)

> 3. Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).
Converts an optional type into the underlying type, or panic if the optional is nil.
![image](https://user-images.githubusercontent.com/104716561/168471857-60b98759-d67b-4d68-be31-566157e635db.png)

>Using this picture below, explain...
>- What the error message means

The main function is expecting to return a String variable, but thing[0x03] is a different type (String optional).

>- Why we're getting this error

Accessing elements of a dictionary will always return an optional type. In this case, 'thing[0x03]' is returning a String optional.

>- How to fix it

Either use the force unwrap as follows:
return thing[0x03]!

or change the return type of main to be a String optional as follows:
pub var main(): String? {
...
