# Using Spring to build an MVC Application

### Objectives
- Students will be introduced to the Spring Framework by creating a sample MVC application
- Students will `Model` a `CourseTopic` and setup a `CourseController` to handle GET requests to display many and one courses in a `View`

### Annotations used in this tutorial
- **`@Repository`**: Indicates that an annotated class is a "Repository", originally defined by Domain-Driven Design (Evans, 2003) as "a mechanism for encapsulating storage, retrieval, and search behavior which emulates a collection of objects".
- **`@Controller`**: Handles HTTP Requests
- **`@Resource`**: The Resource annotation marks a resource that is needed by the application. This annotation may be applied to an application component class, or to fields or methods of the component class. When the annotation is applied to a field or method, the container will inject an instance of the requested resource into the application component when the component is initialized.
- **`@RequestMapping`**: Annotation for mapping web requests onto specific handler classes and/or handler methods.
- **`@RequestParam`**: Annotation which indicates that a method parameter should be bound to a web request parameter. If the method parameter type is Map and a request parameter name is specified, then the request parameter value is converted to a Map assuming an appropriate conversion strategy is available. 

Not an annotation but important to define:
- **`Model model`**: Java-5-specific interface that defines a holder for model attributes. Primarily designed for adding attributes to the model. Allows for accessing the overall model as a java.util.Map.

### Project Set-up 
- Use the Spring Initializr to create the java-courses project
  - We will add the devtools dependency. This will allow us to make changes during run time without having to restart our server.
  - Add the Web dependency
  - Add the Thymeleaf dependency
- Unzip to your default-package or code folder 
- Access through `Bash` and do a `gradle eclipse`
- `import` through your Eclipse package explorer

### Classes to build
- **`Course`**: 
  - contains `String` object properties for `id`, `name`, and `description`
  - contains appropriate constructor, and getters 
- **`CourseRepository`**: 
	- Creates 3 courses and puts them into the map we can use:
		- `spring`, `Spring Framework`, `Spring Frameword Description`
		- `java`, `Core Java`, `Core Java Description`
		- `javascript`, `Intro to Javascript`, `Javascript Description`
 	- contains the ability to access the entire map's collection of courses or one course in the map
- **`CourseController`**: The Controller class to handle HTTP requests
	- Give user the ability to see all courses offered in the application
	- Give user the ability to navigate into one of the courses for the details of the course
- An Application class that will already be built out using the Spring Initializr

### Resources to build

The following html resources are needed to `View` the application during run time. We will begin to go into deeper detail about these files on Wednesday and Thursday once we get into Front End Design with Intro to HTML and Thymeleaf. For now, copy these into your project so that you are able to see this application in action.

In **templates package** create **`courses.html`** and paste the following code snippet
```html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>A List of All Available Courses</title>
</head>
<body>

	<header>
		<h1>A List of All Courses</h1>
	</header>
	
	<main>
		<ul>
			<li th:each="course: ${courses}"><a th:href="@{/course(id=${course.id})}" th:text="${course.name}"></a></li>
		</ul>
	</main>

	<footer>
		<small>Copyright South Harmon Institute of Technology 2018</small>
	</footer>

</body>
</html>
```

In the **templates package**, create **`course.html`** and paste the following code snippet
```html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title th:text="${course.name}">A course</title>
</head>
<body>

	<header>
		<h1 th:text="${course.name}">A Course</h1>
	</header>

	<main>
		<ol>
			<li><a href="/courses">Courses</a></li>
			<li th:text="${course.name}"></li>
		</ol>
		<h2 th:text="${course.description}"></h2>
	</main>

	<footer>
		<small>Copyright South Harmon Institute of Technology 2018</small>
	</footer>

</body>
</html>
```


# Stretch Tasks
- Add a 4th param (instructor) to the course and show this information in the front end of your application
