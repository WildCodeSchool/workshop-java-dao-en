# Dependency injection

This application currently displays the list of students at the Toulouse school.

Bordeaux would like to have the same application, displaying the list of its students.

You therefore need to adapt the code to change the display of the student list, depending on the school.

## 1 - Current state: strong coupling

Looking at the current project code, you can see that the student list is "hard-coded" into the `StudentController` class.

> When a class creates instances of another class, this is called strong coupling.

To display another list, you'd have to create different methods and call them according to the school. The code will become increasingly difficult to maintain, as future additions or modifications are made.

> You can test the application with the command `mvn spring-boot:run`.


## 2 - Switching to dependency injection: weak coupling

To improve existing code and remove strong coupling, you'll implement a **DAO**, as well as **dependency injection**:

* Create a new `StudentDao` interface, which has the signature of the `findAll()` method, returning `List<Student>`.
* Creates a `StudentRepoTls` class, implementing `StudentDao`. The implementation returns the list of Toulouse students (the one currently in `StudentController`).
* Modify `StudentController` to retrieve the list of students from `StudentRepoTls`, by dependency injection.

> You won't need to create an *.xml* file in this project.

## 3 - Multiple implementations

* Create a `StudentRepoBdx` class, a second implementation of `StudentDao`, returning a list of Bordeaux students (of your choice).
* Modify `StudentController`, to load the student list according to the chosen implementation, using `@Qualifier`.