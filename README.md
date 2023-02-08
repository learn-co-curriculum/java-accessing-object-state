# Accessing Object State

## Learning Goals

- Use "dot notation" to access a field (instance variable) through an object reference
- Modify an object's state by assigning a new value to a field
- Use IntelliJ's Java Visualizer to view object state

## Introduction

In this lesson, we will learn how to change an object's state by using
Java's dot operator `.` to access a field through an object reference. 

## Setup

Let's create a new project and then add the `Dog` class.

Create a new Maven Java project named "object_state".
  
![new java project](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/new_java_project.png)

Right-click on the Java folder and create a new Java class named `Dog`.

![new dog class](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/project_structure_newclass.png)

Edit the `Dog` class and add the following code:     

```java
public class Dog {
    
    String name;
    String breed;
    int age;
    boolean waggingTail;
    
    public static void main(String[] args) {

       // create 2 Dog instances
       Dog bigDog = new Dog();
       Dog smallDog = new Dog();
       
    }
    
}
```


## Dot Notation

Let's continue with the `Dog` class and the `main` method that creates two `Dog` instances:

```java
public class Dog {
    
    String name;
    String breed;
    int age;
    boolean waggingTail;
    
    public static void main(String[] args) {

       // create 2 Dog instances
       Dog bigDog = new Dog();
       Dog smallDog = new Dog();
       
    }
    
}
```

As we saw in the last lesson, the fields of each `Dog` instance are initialized to default values based on their data type:

![dog#2 created](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/new_dog2.png)


But we would like to assign the fields with specific values as shown below:

![dog state assigned values](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dogs_updated_state.png)

Looking at the objects in memory, we can see there are two memory locations with the label `name`,
and two memory locations with the label `breed`, etc.  How can we assign the name of the first
dog to "Bruno" and the name of the second dog to "Penny"?

The solution is to use syntax referred to as "dot notation".  The dot operator `.` is
used to separate a variable that references an object and the name of a field.  We can
assign a value to a field for a specific object using dot notation as shown below:

`objectReference.fieldName = value`

To assign the value "Bruno" as the name of the dog referenced by the variable `bigDog`, we write:

`bigDog.name = "Bruno";`

To assign the value "Penny" as the name of the dog referenced by the variable `smallDog`, we write:

`smallDog.name = "Penny";`

Let's update the `main` method to assign values to the fields of each dog
using the two object references `bigDog` and `smallDog`.

```java
public class Dog {

   String name;
   String breed;
   int age;
   boolean waggingTail;

   public static void main(String[] args) {

      // create 2 Dog instances
      Dog bigDog = new Dog();
      Dog smallDog = new Dog();

      // assign new values to the fields of the first dog
      bigDog.name = "Bruno";
      bigDog.breed = "Great Dane";
      bigDog.age = 8;

      // assign new values to the fields of the second dog
      smallDog.name = "Penny";
      smallDog.breed = "Pug";
      smallDog.age = 5;
      smallDog.waggingTail = true;
   }
}
```

Notice the `main` method does not assign a value to `bigDog.waggingTail`, so the field
retains the default boolean value `false`.

Executing the `main` method results in the desired object state:

![dog state assigned values](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dogs_updated_state.png)


## Java Visualizer - Code Along

Currently, the `main` method does not print anything, so it is hard to understand how the state changes as each
line of code is executed.

Let's step through the `main` method using the IntelliJ debugger and the `Java Visualizer` plugin, which
will let us see what the objects look like in memory.

Set a breakpoint on the first line of executable code in the `main` method (i.e. not a comment or blank line),
then click the "debug" icon to launch the debugger.   Your line number may differ depending on comments and blank lines.

![dog breakpoint](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/set_breakpoint.png)

Select the "Java Visualizer" tab in the debug window.
Notice the call stack shows the `main` method has stopped at the breakpoint (your line number may be different).    
 
![java visualizer tab](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/breakpoint_reached.png)

Press the "Step Over" icon to execute each line of code in the `main` method.

![step over](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/stepover_icon.png)

Continue stepping through the code one line at a time and notice how the object state is updated.
   
NOTE: IntelliJ's Java Visualizer lays out the objects in a row, and unfortunately the
arrows cross over the objects. If you want a column layout, use the browser based
Java visualizer at [https://pythontutor.com/java.html](https://pythontutor.com/java.html#mode=edit).


| Code                                           | Java Visualizer                                                                                                                                                                      |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Dog bigDog = new Dog();`                      | ![step 1](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog1_created.png)<br><br> IntelliJ displays the fields in alphabetical order.  <br>            |
| `Dog smallDog = new Dog();`                    | ![step 2](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog2_created.png)<br><br> IntelliJ displays the objects in a row.  <br>                        |
|                                                | ![hover](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/hover_arrow.png) <br><br> You can hover over an arrow with your mouse to change the color. <br> |
| `bigDog.name = "Bruno";`                       | ![step 3](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog1_name.png)                                                                                 |
| `bigDog.breed = "Great Dane";`                 | ![step 4](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog1_breed.png)                                                                                |
| `bigDog.age = 8;`                              | ![step 5](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog1_age.png)                                                                                  |
| `smallDog.name = "Penny";`                     | ![step 6](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog2_name.png)                                                                                 |
| `smallDog.breed = "Pug";`                      | ![step 7](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog2_breed.png)                                                                                |
| `smallDog.age = 5;`                            | ![step 8](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog2_age.png)                                                                                  |
| `smallDog.waggingTail = true;`                 | ![step 9](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/dog2_wagging.png)                                                                              |


## Java Visualizer Plugin Issues

Sometimes Intellij's Java Visualizer plugin messes up how it displays the pointers from the object references.

Resizing the image using either the `+` or `-` button usually fixes the layout issue.

![fix pointers in visualizer](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/resize_fix.png)



## IntelliJ Debugger

We can also use IntelliJ's default debugger and the "Variables" panel
to see the state of each object as we step through code.  

The process of setting a breakpoint and using the "Step Over"
button to step through the code is the same as with the Java Visualizer.

![intellij debugger object state](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/debugger_view.png)

Note that instead of using arrows, an object reference is displayed as a unique id such
as `Dog@691` and `Dog@693`.

## Comprehension Check

### Challenge #1

Assume the `Bike` class is defined as shown:

```java
public class Bike {
    String color;
    int height;

    public static void main(String[] args) {
        Bike mountainBike = new Bike();
        
        //change the color to red
       ????
       
    }
}
```

| Code                              | Java Visualizer                                                                                                            |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| `Bike mountainBike = new Bike();` | ![bike initialized](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/bike_no_color.png)         |
| ????                              | ![set bike color to red](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/bike_red_color.png)   |

<details>
    <summary>What is the correct Java statement to assign the color of the bike to "red"?</summary>

  <p>Answer: <code>mountainBike.color = "red";</code></p>

</details>

<br>

### Challenge #2

Assume the `ProgrammingLanguage` class is defined as shown:

```java
public class ProgrammingLanguage {

   String name;
   int yearReleased;

   public static void main(String[] args) {
      ProgrammingLanguage language1 = new ProgrammingLanguage();
      ProgrammingLanguage language2 = new ProgrammingLanguage();

      //assign values to fields
      ....

   }
}
```

Assume the `main` method has created two instances of `ProgrammingLanguage` and the statements
represented by `....` have assigned the fields using the object references as shown:

![programming_language_state](https://curriculum-content.s3.amazonaws.com/6676/java-mod2-oop-fundamentals/language_state.png) 

<details>
    <summary>What is the correct Java statement to assign the release year for the programming language named "Go" to 2007?</summary>

  <p>Answer: <code>language2.yearReleased = 2007;</code></p>

</details>

<br>




## Conclusion

Each class instance has its own copy of the fields (instance variables).
We need to use an object reference and the dot operator `.` to access a field of a specific object. 

We can modify an object's state by using dot notation to assign a new value to a field:

`objectReference.fieldName = value`

## Resources

- [Referencing an object's fields](https://docs.oracle.com/javase/tutorial/java/javaOO/usingobject.html)
