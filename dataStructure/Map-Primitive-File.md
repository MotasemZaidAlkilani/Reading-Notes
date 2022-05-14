# Map - Primitive  -  File


## Java Primitives
Java has a two-fold type system consisting of primitives such as int, boolean and reference types such as Integer, Boolean.
Every primitive type corresponds to a reference type.Every object(reference type) contains a single value of the corresponding primitive type.
as u can see in the below picture :

<img src="../images/PrimitiveVsReferenceTypeJava.png" width=800 height=300>

-A primitive is not composed of other data types. Where as an object can be and generally is.
-Primitives are passed by value, i.e. a copy of the primitive itself is passed. Whereas for objects,
the copy of the reference is passed, not the object itself.
-Primitives are independent data types, i.e. there does not exist a hierarchy/super class for them.
Whereas every Object is descendent of class "Object"
-Primitives are immutable, they can be used as so without any special care. Whereas for objects,
special care needs to be taken, they are not immutable by default
-With objects, there are two types of copies, Shallow and Deep. There is a significant difference between them.
So the choice depends on how do we intend to use them. With primitives, there is no such difference, everything
is by default deep copy only

there a factor that may decide for u which one to choose , and this factor is memory impact on each one,
so here difference between primitive type and reference type in memory :

-boolean (primitive 1bits vs reference 128bits)
-byte (primitive 8bits vs reference 128bits)
-short,char (primitive 16bits vs reference 128bits)
-int, float (primitive 32bist vs reference 128bits)
-long, double (primitive 64bits vs reference 192bits)

## Exceptions
Exception is stand for the phrase "exceptional event."
> Definition: An exception is an event, which occurs during the execution of a program, that disrupts the normal flow of the program's instructions.

The exception happen when the program run of the context , so like when that occur in method ,the method creates an object and hands it off to the runtime system
 as in the picture below .After a method throws an exception, the runtime system attempts to find something to handle it. The set of possible "somethings" to handle the exception is the ordered list of methods that had been called to get to the method where the error occurred. The list of methods is known as the call stack. 

<img src="../images/Exception-Hierarchy.png" width=500 height=400>

to know how to catch and handle exceptions , u can use try and catch ,which try catches the error in the code ,and then catch appear what type of error 
u have .the context of try and catch is as follow :

try{

// required code to check if have any error

}catch(typeOfException blablabla){

//here u write what u want to do if the exception happen

}

Now that you know what exceptions are and how to use them, it's time to learn the advantages of using exceptions in your programs.

1: Separating Error-Handling Code from "Regular" Code
2: Propagating Errors Up the Call Stack
3: Grouping and Differentiating Error Types

## Scanner
Scanner is way to read text from user inputs or read from files in java ,and it is found in the java.util package.
 breaks its input into tokens using a delimiter pattern, which by default matches whitespace. The resulting tokens may
 then be converted into values of different types using the various next methods
 
 For example, this code allows a user to read a number from System.in:

     Scanner sc = new Scanner(System.in);
     int i = sc.nextInt();
     
The default whitespace delimiter used by a scanner is as recognized by Character.isWhitespace. The reset() method will reset the value of the scanner's delimiter to the default whitespace delimiter regardless of whether it was previously changed.     
