\pom.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>spring-demo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>spring-demo</name>
	<description>Demo project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.0.0.M1</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

	<repositories>
		<repository>
			<id>spring-snapshots</id>
			<name>Spring Snapshots</name>
			<url>https://repo.spring.io/snapshot</url>
			<snapshots>
				<enabled>true</enabled>
			</snapshots>
		</repository>
		<repository>
			<id>spring-milestones</id>
			<name>Spring Milestones</name>
			<url>https://repo.spring.io/milestone</url>
			<snapshots>
				<enabled>false</enabled>
			</snapshots>
		</repository>
	</repositories>

	<pluginRepositories>
		<pluginRepository>
			<id>spring-snapshots</id>
			<name>Spring Snapshots</name>
			<url>https://repo.spring.io/snapshot</url>
			<snapshots>
				<enabled>true</enabled>
			</snapshots>
		</pluginRepository>
		<pluginRepository>
			<id>spring-milestones</id>
			<name>Spring Milestones</name>
			<url>https://repo.spring.io/milestone</url>
			<snapshots>
				<enabled>false</enabled>
			</snapshots>
		</pluginRepository>
	</pluginRepositories>


</project>
```
\src\main\java\com\example\demo\BackupStockDataProvider.java
```
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class BackupStockDataProvider
		implements StockDataProvider {

	@Override
	public int[] getAllData() {
		// Let's assume all the logic goes here..
		return new int[] { 1, 2, 3, 4, 5, 15 };
	}

}
```
\src\main\java\com\example\demo\CollectionExamples.java
```
package com.example.demo;

public class CollectionExamples {
	// References
	// https://github.com/in28minutes/JavaInterviewQuestionsAndAnswers/blob/master/docs/collections.md
	//
	// Why do we need collections?
	// An array is a container object that holds a fixed number of values of a
	// single type
	// The length of an array is established when the array is created. After
	// creation, its length is fixed.

	// Collections are used to store, retrieve, manipulate,

	// List
	// Positional Access
	// Trim all elements in a list

	// Set
	// Find distint names/words
	// Find duplicates -> if (!uniques.add(a))

	// Map
	// Occurrences of Letters
	// Occurrences of Words
	// Group employees by department
	// Group students by Grade
	// Group people by city

	// Queue/DeQueue

	// Decide which collection to use!
	// Select one student from my students to receive an award in a lucky draw
	// Find list of unique words in a paragraph
	// Find five most popular names
	// Waiting list for train reservations

	// Collection interfaces
	// Collection of Collections
	// * Map of List
	// Ordering collections - Comparable

	// Synchronization Wrappers ->
	// https://docs.oracle.com/javase/tutorial/collections/implementations/wrapper.html
	// List<Type> list = Collections.synchronizedList(new ArrayList<Type>());

	// Unmodifiable Wrappers
	// public static <T> Collection<T> unmodifiableCollection(Collection<?
	// extends T> c);
	// Collections and Lambdas ->
	// https://docs.oracle.com/javase/tutorial/collections/interfaces/map.html

}
```
\src\main\java\com\example\demo\DefaultStockDataProvider.java
```
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class DefaultStockDataProvider
		implements StockDataProvider {

	@Override
	public int[] getAllData() {
		// Let's assume all the logic goes here..
		return new int[] { 1, 2, 3, 4 };
	}

}
```
\src\main\java\com\example\demo\DemoApplication.java
```
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {

	public static void main(String[] args) {
		SpringApplication.run(DemoApplication.class, args);
	}

}
```
\src\main\java\com\example\demo\LamdaStreamExamples.java
```
package com.example.demo;

public class LamdaStreamExamples {
	/*
	 * What is functional programming? Functional programming is a programming
	 * paradigmâ€”a style of building the structure and elements of computer
	 * programsâ€”that treats computation as the evaluation of mathematical
	 * functions and avoids changing-state and mutable data.
	 * 
	 * Can you give an example of functional programming?
	 * 
	 * @Test public void sumOfOddNumbers_Usual() { List<Integer> numbers =
	 * Arrays.asList(1, 3, 4, 6, 2, 7); int sum = 0; for (int number : numbers)
	 * if (number % 2 != 0) sum += number; assertEquals(11, sum); }
	 * 
	 * @Test public void sumOfOddNumbers_FunctionalProgramming() { List<Integer>
	 * numbers = Arrays.asList(1, 3, 4, 6, 2, 7); int sum =
	 * numbers.stream().filter(StreamsTest::isOdd).reduce(0, Integer::sum);
	 * assertEquals(11, sum); }
	 * 
	 * static boolean isOdd(int number) { return number % 2 != 0; }
	 * 
	 * What is a Stream? A Stream is a source of objects. In the above example,
	 * we created a stream from List.
	 * 
	 * Streams have Intermediate Operations and Terminal Operations. In the
	 * example above, we used filter as intermediate operation and reduce as a
	 * terminal operation.
	 * 
	 * What are Intermediate Operations in Streams? An Intermediate Operation on
	 * a Stream returns another Stream.
	 * 
	 * Examples : map, filter, distinct, sorted.
	 * 
	 * Distinct Example
	 * 
	 * @Test public void streamExample_Distinct() { List<Integer> numbers =
	 * Arrays.asList(1, 1, 2, 6, 2, 3);
	 * numbers.stream().distinct().forEach(System.out::print); // 1263 }
	 * 
	 * Sorted Example
	 * 
	 * @Test public void streamExample_Sorted() { List<Integer> numbers =
	 * Arrays.asList(1, 1, 2, 6, 2, 3);
	 * numbers.stream().sorted().forEach(System.out::print); // 112236 }
	 * 
	 * Filter Example
	 * 
	 * @Test public void streamExample_Filter() { List<Integer> numbers =
	 * Arrays.asList(1, 3, 4, 6, 2, 7);
	 * numbers.stream().filter(StreamsTest::isOdd).forEach(System.out::print);
	 * //137 }
	 * 
	 * What are Terminal Operations in Streams? Terminal Operation either
	 * produce a result or create a side effect.
	 * 
	 * reduce is used to cumulate elements.
	 * 
	 * @Test public void sumOfOddNumbers_FunctionalProgramming() { List<Integer>
	 * numbers = Arrays.asList(1, 3, 4, 6, 2, 7); int sum =
	 * numbers.stream().filter(StreamsTest::isOdd).reduce(0, Integer::sum);
	 * assertEquals(11, sum); }
	 * 
	 * forEach is used to create a side effect. Print to Output. Store to
	 * database.
	 * 
	 * @Test public void streamExample_Filter() { List<Integer> numbers =
	 * Arrays.asList(1, 3, 4, 6, 2, 7);
	 * numbers.stream().filter(StreamsTest::isOdd).forEach(System.out::print);
	 * //137 }
	 * 
	 * collect is used to group elements to a collection
	 * 
	 * @Test public void streamExample_Collect() { List<Integer> numbers =
	 * Arrays.asList(1, 3, 4, 6, 2, 7); List<Integer> oddNumbers =
	 * numbers.stream().filter(StreamsTest::isOdd).collect(Collectors.toList());
	 * System.out.println(oddNumbers); // [1, 3, 7] }
	 * 
	 * What are Method References? Integer::sum, System.out::print in the above
	 * examples are method references. These two are simple static methods which
	 * are used instead of Lambda Expressions.
	 * 
	 * What are Lambda Expressions? A lambda expression is an anonymous
	 * function. Simply put, it's a method without a declaration. There will be
	 * no access modifiers, no return value declaration, and no name. It's a
	 * shorthand that allows you to write a method in the same place you are
	 * going to use it. Especially useful in places where a method is being used
	 * only once, and the method definition is short.
	 * 
	 * Syntax : Parameters -> Executed code
	 * 
	 * Can you give an example of Lambda Expression?
	 * 
	 * In the example below, number -> System.out.print(number) is a lambda
	 * expression.
	 * 
	 * @Test public void lambdaExpression_simpleExample() { List<Integer>
	 * numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
	 * numbers.stream().filter(StreamsTest::isOdd).forEach(number ->
	 * System.out.print(number)); // 137 }
	 * 
	 * Can you explain the relationship between Lambda Expression and Functional
	 * Interfaces?
	 * 
	 * Look at the earlier example :
	 * 
	 * Function we passed in is number -> System.out.print(number). Input to
	 * this function is number. The function consumes it and prints it to the
	 * output.
	 * 
	 * forEach function has an interface - void
	 * java.util.stream.Stream.forEach(Consumer<T> action)
	 * 
	 * The JavaDoc for java.util.function.Consumer<T> reads
	 * - @FunctionalInterface : Represents an operation that accepts a single
	 * input argument and returns no result. Unlike most other functional
	 * interfaces, Consumer is expected to operate via side-effects.
	 * 
	 * When ever we create a Lambda Expression, we are defining a function which
	 * implements a pre-defined/custom defined Functional Interface.
	 * 
	 * What is a Predicate?
	 * 
	 * @FunctionalInterface public interface Predicate<T> { boolean test(T t); }
	 * 
	 * @Test public void lambdaExpression_predicate() { List<Integer> numbers =
	 * Arrays.asList(1, 3, 4, 6, 2, 7); numbers.stream().filter((number) ->
	 * (number % 2 != 0)).forEach(number -> System.out.print(number)); // 137 }
	 * 
	 * (number) -> (number % 2 != 0) is a Predicate. Takes an argument and
	 * returns true of false.
	 * 
	 * Signature of filter function : Stream<T>
	 * java.util.stream.Stream.filter(Predicate<? super T> predicate). filter
	 * returns a stream consisting of the elements of this stream that match the
	 * given predicate.
	 * 
	 * What is the functional interface - Function?
	 * 
	 * @FunctionalInterface public interface Function<T, R> { R apply(T t); }
	 * 
	 * What is a Consumer?
	 * 
	 * @FunctionalInterface public interface Consumer<T> { void accept(T t); }
	 * 
	 * Can you give examples of functional interfaces with multiple arguments?
	 * 
	 * @FunctionalInterface public interface BiFunction<T, U, R> { R apply(T t,
	 * U u); }
	 */
}
```
\src\main\java\com\example\demo\StockBusinessClass.java
```
package com.example.demo;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
public class StockBusinessClass {

	// I will give you the data provider to use
	@Autowired
	StockDataProvider defaultStockDataProvider;

	public void setDependency(
			StockDataProvider dependency) {
		this.defaultStockDataProvider = dependency;
	}

	public int findMaxPrice() {
		int[] allData = defaultStockDataProvider.getAllData();

		if (allData.length == 0)
			throw new RuntimeException("No Data Returned");

		return findMaxFromArray(allData);
	}

	private int findMaxFromArray(int[] data) {
		int max = 0;
		for (int value : data) {
			if (value > max) {
				max = value;
			}
		}
		return max;
	}

}
```
\src\main\java\com\example\demo\StockDataProvider.java
```
package com.example.demo;

public interface StockDataProvider {
	int[] getAllData();
}
```
\src\main\resources\application.properties
```
logging.level.org.springframework=DEBUG
```
\src\test\java\com\example\demo\DemoApplicationTests.java
```
package com.example.demo;

import org.junit.Assert;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit4.SpringRunner;

@RunWith(SpringRunner.class)
@SpringBootTest
public class DemoApplicationTests {

	@Autowired
	StockBusinessClass businessClass;

	@Test
	public void contextLoads() {
		Assert.assertEquals(4,
				businessClass.findMaxPrice());
	}
}
```
\src\test\java\com\example\demo\lambda.txt
```
What is functional programming?
Functional programming is a programming paradigmâ€”a style of building the structure and elements of computer programsâ€”that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

Can you give an example of functional programming?

	@Test
	public void sumOfOddNumbers_Usual() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		int sum = 0;
		for (int number : numbers)
			if (number % 2 != 0)
				sum += number;
		assertEquals(11, sum);
	}

	@Test
	public void sumOfOddNumbers_FunctionalProgramming() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		int sum = numbers.stream().filter(StreamsTest::isOdd).reduce(0, Integer::sum);
		assertEquals(11, sum);
	}

	static boolean isOdd(int number) {
		return number % 2 != 0;
	}
	
What is a Stream?
A Stream is a source of objects. In the above example, we created a stream from List.

Streams have Intermediate Operations and Terminal Operations. In the example above, we used filter as intermediate operation and reduce as a terminal operation.

What are Intermediate Operations in Streams?
An Intermediate Operation on a Stream returns another Stream.

Examples : map, filter, distinct, sorted.

Distinct Example
	
	@Test
	public void streamExample_Distinct() {
		List<Integer> numbers = Arrays.asList(1, 1, 2, 6, 2, 3);
		numbers.stream().distinct().forEach(System.out::print);
		// 1263
	}
	
Sorted Example
	
	@Test
	public void streamExample_Sorted() {
		List<Integer> numbers = Arrays.asList(1, 1, 2, 6, 2, 3);
		numbers.stream().sorted().forEach(System.out::print);
		// 112236
	}

Filter Example
	
	@Test
	public void streamExample_Filter() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		numbers.stream().filter(StreamsTest::isOdd).forEach(System.out::print);
		//137
	}

What are Terminal Operations in Streams?
Terminal Operation either produce a result or create a side effect.

reduce is used to cumulate elements.
	@Test
	public void sumOfOddNumbers_FunctionalProgramming() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		int sum = numbers.stream().filter(StreamsTest::isOdd).reduce(0, Integer::sum);
		assertEquals(11, sum);
	}

forEach is used to create a side effect. Print to Output. Store to database. 
	@Test
	public void streamExample_Filter() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		numbers.stream().filter(StreamsTest::isOdd).forEach(System.out::print);
		//137
	}

collect is used to group elements to a collection
	
@Test
	public void streamExample_Collect() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		List<Integer> oddNumbers = numbers.stream().filter(StreamsTest::isOdd).collect(Collectors.toList());
		System.out.println(oddNumbers);
		// [1, 3, 7]
	}
	
What are Method References?
Integer::sum, System.out::print in the above examples are method references. These two are simple static methods which are used instead of Lambda Expressions.

What are Lambda Expressions?
A lambda expression is an anonymous function. Simply put, it's a method without a declaration. There will be no access modifiers, no return value declaration, and no name. It's a shorthand that allows you to write a method in the same place you are going to use it. Especially useful in places where a method is being used only once, and the method definition is short. 

Syntax : Parameters -> Executed code

Can you give an example of Lambda Expression?

In the example below, number -> System.out.print(number) is a lambda expression.

	@Test
	public void lambdaExpression_simpleExample() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		numbers.stream().filter(StreamsTest::isOdd).forEach(number -> System.out.print(number));
		// 137
	}

Can you explain the relationship between Lambda Expression and Functional Interfaces?

Look at the earlier example : 

Function we passed in is number -> System.out.print(number). Input to this function is number. The function consumes it and prints it to the output. 

forEach function has an interface - void java.util.stream.Stream.forEach(Consumer<T> action)

The JavaDoc for java.util.function.Consumer<T> reads - @FunctionalInterface : Represents an operation that accepts a single input argument and returns no result. Unlike most other functional interfaces, Consumer is expected to operate via side-effects. 

When ever we create a Lambda Expression, we are defining a function which implements a pre-defined/custom defined Functional Interface. 

What is a Predicate?

@FunctionalInterface
public interface Predicate<T> {
  boolean test(T t);
}

	@Test
	public void lambdaExpression_predicate() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2, 7);
		numbers.stream().filter((number) -> (number % 2 != 0)).forEach(number -> System.out.print(number));
		// 137
	}

(number) -> (number % 2 != 0) is a Predicate. Takes an argument and returns true of false.

Signature of filter function : Stream<T> java.util.stream.Stream.filter(Predicate<? super T> predicate). filter returns a stream consisting of the elements of this stream that match the given predicate. 
	
What is the functional interface - Function?

@FunctionalInterface
public interface Function<T, R> {
  R apply(T t);
}

What is a Consumer?
@FunctionalInterface
public interface Consumer<T> {
  void accept(T t);
}

Can you give examples of functional interfaces with multiple arguments?
@FunctionalInterface
public interface BiFunction<T, U, R> {
  R apply(T t, U u);
}
```
\src\test\java\com\example\demo\LambdaExpressionTest.java
```
package com.example.demo;

import static org.junit.Assert.assertEquals;

import java.io.File;
import java.io.FileFilter;
import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;

import org.junit.Test;

public class LambdaExpressionTest {

	Course course = new Course("Java New Features",
			Arrays.asList(new Student("Ranga", "India", 90),
					new Student("Bill", "United States",
							80)));

	public File[] getDirectories(String path) {
		File[] hiddenFiles = new File(path)
				.listFiles(new FileFilter() {
					@Override
					public boolean accept(File file) {
						return file.isDirectory();
					}

				});

		return hiddenFiles;
	}

	public File[] getDirectoriesPassingaFunction(
			String path) {
		return new File(path).listFiles(File::isDirectory);
	}

	class Student {
		private String name;
		private String country;
		private int marks;

		public Student(String name, String country,
				int marks) {
			super();
			this.name = name;
			this.country = country;
			this.marks = marks;
		}

		public String getName() {
			return name;
		}

		public void setName(String name) {
			this.name = name;
		}

		public String getCountry() {
			return country;
		}

		public void setCountry(String country) {
			this.country = country;
		}

		public int getMarks() {
			return marks;
		}

		public void setMarks(int marks) {
			this.marks = marks;
		}

		@Override
		public String toString() {
			return "Student [name=" + name + ", country="
					+ country + ", marks=" + marks + "]";
		}

	}

	class Course {
		private String name;
		private List<Student> students;

		public Course(String name, List<Student> students) {
			super();
			this.name = name;
			this.students = students;
		}

		public String getName() {
			return name;
		}

		public void setName(String name) {
			this.name = name;
		}

		public List<Student> getStudents() {
			return students;
		}

		public void setStudents(List<Student> students) {
			this.students = students;
		}

		public void printStudentsFrom(String country) {
			for (Student student : students) {
				if (country.equals(student.getCountry())) {
					System.out.println(student);
				}
			}
		}

		public void printStudentsWithMarksGreaterThan(
				int min) {
			for (Student student : students) {
				if (student.getMarks() > min) {
					System.out.println(student);
				}
			}
		}

		public void printStudentsWithMarksWithinRange(
				int min, int max) {
			for (Student student : students) {
				if (student.getMarks() > min
						&& student.getMarks() <= max) {
					System.out.println(student);
				}
			}
		}

		/* Higher Order Function */
		public void printStudentsSatisfyingCheck(
				CheckStudent check) {
			for (Student student : students) {
				if (check.test(student)) {
					System.out.println(student);
				}
			}
		}

		/*
		 * Predefined Interface interface Predicate<T> { boolean test(T t); }
		 */
		public void printStudentsSatisfyingPredicate(
				Predicate<Student> check) {
			for (Student student : students) {
				if (check.test(student)) {
					System.out.println(student);
				}
			}
		}

		public void consumeStudentsSatisfyingPredicate(
				Predicate<Student> check,
				Consumer<Student> consumer) {
			for (Student student : students) {
				if (check.test(student)) {
					consumer.accept(student);
				}
			}
		}

	}

	interface CheckStudent {
		boolean test(Student student);
	}

	@Test
	public void testGetDirectories() {
		assertEquals(4, getDirectories(".").length);
		assertEquals(4,
				getDirectoriesPassingaFunction(".").length);
	}

	@Test
	public void testPrintStudentsFrom() {
		course.printStudentsFrom("India");
	}

	@Test
	public void testPrintStudentsWithMarksGreaterThan() {
		course.printStudentsWithMarksGreaterThan(70);
	}

	@Test
	public void testPrintStudentsWithMarksGreaterThanWithCustomCheck() {
		course.printStudentsSatisfyingCheck(
				new CheckStudent() {
					@Override
					public boolean test(Student student) {
						return student.getMarks() > 70
								&& student.getMarks() <= 90;
					}

				});
	}

	@Test
	public void testCreationOfReusableFunction() {
		final Function<Integer, Predicate<Student>> marksGreaterThan = minimumMarks -> student -> student
				.getMarks() > minimumMarks;
	}

	@Test
	public void testPrintStudentsWithMarksGreaterThanWithCustomCheckAndLambda() {
		course.printStudentsSatisfyingCheck(
				(Student student) -> student.getMarks() > 70
						&& student.getMarks() <= 90);
	}

	@Test
	public void testPrintStudentsWithMarksGreaterThanWithPredicateAndLambda() {
		course.printStudentsSatisfyingPredicate(
				(Student student) -> student.getMarks() > 70
						&& student.getMarks() <= 90);
	}

	@Test
	public void testConsumeStudentsSatisfyingPredicate() {
		course.consumeStudentsSatisfyingPredicate(
				(Student student) -> student.getMarks() > 70
						&& student.getMarks() <= 90,
				(Student student) -> System.out
						.println(student));
	}

	@Test
	public void testPreviousFunctionWithStreams() {
		course.getStudents().stream()
				.filter(student -> student.getMarks() > 70
						&& student.getMarks() <= 90)
				.forEach(student -> System.out
						.println(student));
	}

	@Test
	public void testPreviousFunctionWithStreams_findFirst() {
		// Optional class is useful whenever the result may be absent.
		Optional<Student> first = course.getStudents()
				.stream()
				.filter(student -> student.getMarks() > 70
						&& student.getMarks() <= 90)
				.findFirst();
		System.out.println(first.get());
	}

	@Test
	public void compareStudentsUsingLambdas() {
		// Behavior parameterization
		course.getStudents()
				.sort((Student s1, Student s2) -> Integer
						.compare(s1.getMarks(),
								s2.getMarks()));
		System.out.println(course.getStudents());
	}

}
```
\src\test\java\com\example\demo\LambdaExpressionTest2.java
```
package com.example.demo;

import java.util.Arrays;
import java.util.List;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.stream.Collectors;

import org.junit.Test;

public class LambdaExpressionTest2 {

	public class Person {

		private final String name;
		private final int age;

		public Person(final String theName,
				final int theAge) {
			name = theName;
			age = theAge;
		}

		public String getName() {
			return name;
		}

		public int getAge() {
			return age;
		}

		public int ageDifference(final Person other) {
			return age - other.age;
		}

		@Override
		public String toString() {
			return String.format("%s - %d", name, age);
		}
	}

	final List<Person> people = Arrays.asList(
			new Person("John", 20), new Person("Sara", 21),
			new Person("Jane", 21), new Person("Greg", 35));

	@Test
	public void testSomething() {

		final Function<String, Predicate<String>> startsWithLetter = (
				String letter) -> (String name) -> name
						.startsWith(letter);

		final List<String> friends = Arrays.asList("Brian",
				"Nate", "Neal", "Raju", "Sara", "Scott");

		friends.stream().forEach(System.out::println);

		friends.stream().map(String::toUpperCase)
				.forEach(System.out::println);

		friends.stream().filter(startsWithLetter.apply("N"))
				.forEach(System.out::println);

		System.out
				.println(friends.stream()
						.reduce((s1,
								s2) -> s1.length() > s2
										.length() ? s1 : s2)
				.get());

		System.out.println(
				friends.stream().map(String::toUpperCase)
						.collect(Collectors.joining(", ")));

		final String str = "text1234";

		str.chars().forEach(ch -> System.out.println(ch));

		str.chars().filter(Character::isDigit)
				.forEach(System.out::println);

		people.stream()
				.sorted((p1, p2) -> p1.ageDifference(p2))
				.forEach(System.out::println);

		people.stream().sorted(Person::ageDifference)
				.forEach(System.out::println);

		people.stream()
				.sorted((person1, person2) -> person1
						.getName()
						.compareTo(person2.getName()))
				.forEach(System.out::println);

	}

	@Test
	public void lambdaExpression_simpleExample() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		numbers.stream().filter(StreamsTest::isOdd).forEach(
				number -> System.out.print(number));
		// 137
	}

	@Test
	public void lambdaExpression_predicate() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		numbers.stream()
				.filter((number) -> (number % 2 != 0))
				.forEach(
						number -> System.out.print(number));
		// 137
	}

	@Test
	public void lambdaExpression_BiFunction() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		numbers.stream().forEach(
				number -> System.out.print(number));
		// 137
	}

}
```
\src\test\java\com\example\demo\StockBusinessClassTest.java
```
package com.example.demo;

import org.junit.Assert;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.Mockito;
import org.mockito.junit.MockitoJUnitRunner;

@RunWith(MockitoJUnitRunner.class)
public class StockBusinessClassTest {

	@InjectMocks
	StockBusinessClass businessClass = new StockBusinessClass();

	@Mock
	StockDataProvider dependency;

	// Problems
	// We are writing an integration test
	// What if I have to connect to a different data provider?
	// How can I unit test all possible scenarios?

	// Solution
	// Step 1: How can I test with all possible scenarios?
	// Create Interface StockDataProvider

	// What is a Dependency?
	// Spring Application Context
	//
	@Test
	public void testBasicExample() {
		Mockito.when(dependency.getAllData())
				.thenReturn(new int[] { 1, 2, 3 });

		Assert.assertEquals(3,
				businessClass.findMaxPrice());
	}

	@Test(expected = RuntimeException.class)
	public void testWithNoData_Returns0() {
		Mockito.when(dependency.getAllData())
				.thenReturn(new int[] {});

		businessClass.findMaxPrice();
	}

}
```
\src\test\java\com\example\demo\StreamsTest.java
```
package com.example.demo;

import static org.junit.Assert.assertEquals;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;

import org.junit.Test;

public class StreamsTest {

	// Laziness

	// All intermediate operations are lazy. An expression, method, or algorithm
	// is lazy if its value is evaluated only when it is required.

	@Test
	public void streamsBasics_creatingAStream() {
		List<String> list = Stream
				.of("Apple", "Banana", "Mango")
				.collect(Collectors.toList());
		assertEquals(
				Arrays.asList("Apple", "Banana", "Mango"),
				list);
	}

	@Test
	public void streamsBasics_mappingAValueToAnother() {
		List<String> collected = Stream
				.of("Apple", "Banana", "Mango")
				.map(value -> value.toUpperCase())
				.collect(Collectors.toList());

		assertEquals(
				Arrays.asList("APPLE", "BANANA", "MANGO"),
				collected);
	}

	@Test
	public void streamsBasics_filtering() {
		List<String> initCaps = Stream
				.of("Apple", "Banana", "mango")
				.filter(value -> Character
						.isUpperCase(value.charAt(0)))
				.collect(Collectors.toList());

		assertEquals(Arrays.asList("Apple", "Banana"),
				initCaps);
	}

	class Country {
		private String name;
		private long area;
		private long population;
		private String continent;

		public Country(String name, long area,
				long population, String continent) {
			super();
			this.name = name;
			this.area = area;
			this.population = population;
			this.continent = continent;
		}

		public String getName() {
			return name;
		}

		public long getArea() {
			return area;
		}

		public long getPopulation() {
			return population;
		}

		public String getContinent() {
			return continent;
		}

		@Override
		public String toString() {
			return "Country [name=" + name + ", area="
					+ area + ", population=" + population
					+ ", continent=" + continent + "]";
		}

	}

	List<Country> countries = Arrays.asList(
			new Country("India", 10000, 20000, "Asia"),
			new Country("China", 30000, 30000, "Asia"),
			new Country("USA", 40000, 10000,
					"North America"));

	@Test
	public void streamsBasics_min() {
		Country smallestCountryInTheList = countries
				.stream().min(Comparator.comparing(
						(Country c) -> c.getArea()))
				.get();
		assertEquals("India",
				smallestCountryInTheList.getName());
	}

	@Test
	public void streamsBasics_max() {
		Country largestCountryInTheList = countries.stream()
				.max(Comparator.comparing(
						(Country c) -> c.getArea()))
				.get();
		assertEquals("USA",
				largestCountryInTheList.getName());
	}

	@Test
	public void streamsBasics_reduce() {
		int count = Stream.of(100, 200, 300).reduce(0,
				(acc, element) -> acc + element);
		assertEquals(600, count);
	}

	@Test
	public void streamsBasics_reduceForCountries() {
		long count = countries.stream()
				.map(Country::getArea).reduce(0l,
						(acc, element) -> acc + element);
		assertEquals(80000, count);
	}

	@Test
	public void streamsBasics_namesOfCountriesWithAreaGreaterThan20000() {
		List<String> countriesWithAreaGreaterThan20000 = countries
				.stream()
				.filter((Country country) -> country
						.getArea() > 20000)
				.map(c -> c.getName())
				.collect(Collectors.toList());
		assertEquals(Arrays.asList("China", "USA"),
				countriesWithAreaGreaterThan20000);
	}

	@Test
	public void streamsBasics_namesOfCountriesWithAreaGreaterThan20000_methodReferences() {
		List<String> countriesWithAreaGreaterThan20000 = countries
				.stream()
				.filter((Country country) -> country
						.getArea() > 20000)
				.map(Country::getName)
				.collect(Collectors.toList());
		assertEquals(Arrays.asList("China", "USA"),
				countriesWithAreaGreaterThan20000);
	}

	@Test
	public void streamsBasics_averageArea() {
		double average = countries.stream()
				.mapToLong(Country::getArea).average()
				.getAsDouble();
		assertEquals(26666.66, average, 0.1);
	}

	@Test
	public void streamsBasics_max_methodReferences() {
		Country largestCountryInTheList = countries.stream()
				.max(Comparator.comparing(Country::getArea))
				.get();
		assertEquals("USA",
				largestCountryInTheList.getName());
	}

	@Test
	public void streamsBasics_group() {
		Map<String, List<Country>> countriesGroupedByContinent = countries
				.stream().collect(Collectors.groupingBy(
						country -> country.getContinent()));
		System.out.println(
				countriesGroupedByContinent.get("Asia"));
	}

	@Test
	public void streamsBasics_groupAndCount() {
		Map<String, Long> countOfCountriesInContinent = countries
				.stream()
				.collect(Collectors.groupingBy(
						Country::getContinent,
						Collectors.counting()));
		assertEquals(2, countOfCountriesInContinent
				.get("Asia").longValue());
	}

	@Test
	public void streamsBasics_groupAndTotalArea() {
		Map<String, Long> countOfCountriesInContinent = countries
				.stream()
				.collect(Collectors.groupingBy(
						Country::getContinent,
						Collectors.reducing(0L,
								Country::getArea,
								Long::sum)));
		assertEquals(40000, countOfCountriesInContinent
				.get("Asia").longValue());
	}

	@Test
	public void streamsBasics_groupAndAveragingArea() {
		Map<String, Double> countOfCountriesInContinent = countries
				.stream()
				.collect(Collectors.groupingBy(
						Country::getContinent,
						Collectors.averagingLong(
								Country::getArea)));
		assertEquals(20000, countOfCountriesInContinent
				.get("Asia").doubleValue(), 0.1);
	}

	@Test
	public void streamsBasics_groupAndRetrieveOnlyNames() {
		Map<String, List<String>> countriesGroupedByContinent = countries
				.stream()
				.collect(Collectors.groupingBy(
						country -> country.getContinent(),
						Collectors.mapping(Country::getName,
								Collectors.toList())));

		// [India, China]
		System.out.println(
				countriesGroupedByContinent.get("Asia"));
	}

	@Test
	public void streamsBasics_partition() {
		Map<Boolean, List<Country>> partitionBasedOnContinentAsiaOrNot = countries
				.stream()
				.collect(Collectors.partitioningBy(
						country -> country.getContinent()
								.equals("Asia")));
		System.out
				.println(partitionBasedOnContinentAsiaOrNot
						.get(true));
	}

	@Test
	public void streamsBasics_joinAsString() {
		Map<Boolean, List<Country>> partitionBasedOnContinentAsiaOrNot = countries
				.stream()
				.collect(Collectors.partitioningBy(
						country -> country.getContinent()
								.equals("Asia")));

		List<Country> countriesInAsia = partitionBasedOnContinentAsiaOrNot
				.get(true);
		String joinedByComma = countriesInAsia.stream()
				.map(Country::getName)
				.collect(Collectors.joining(",", "[", "]"));
		assertEquals("[India,China]", joinedByComma);
	}

	List<Integer> values = new ArrayList<>();

	{
		for (int i = 1; i < 10000000; i++) {
			values.add(i);
		}
	}

	@Test
	public void streamsBasics_performance_parallelStream() {
		int sum = values.parallelStream().mapToInt(i -> i)
				.sum();
		System.out.println(sum);
	}

	@Test
	public void streamsBasics_performance_stream() {
		int sum = values.stream().mapToInt(i -> i).sum();
		System.out.println(sum);
	}

	@Test
	public void streamsBasics_performance_loop() {
		int sum = 0;
		for (int value : values)
			sum += value;
		System.out.println(sum);
	}

	@Test
	public void sumOfOddNumbers_Usual() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		int sum = 0;
		for (int number : numbers)
			if (number % 2 != 0)
				sum += number;
		assertEquals(11, sum);
	}

	@Test
	public void sumOfOddNumbers_FunctionalProgramming() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		int sum = numbers.stream()
				.filter(StreamsTest::isOdd)
				.reduce(0, Integer::sum);
		assertEquals(11, sum);
	}

	static boolean isOdd(int number) {
		return number % 2 != 0;
	}

	@Test
	public void streamExample_Distinct() {
		List<Integer> numbers = Arrays.asList(1, 1, 2, 6, 2,
				3);
		numbers.stream().distinct()
				.forEach(System.out::print);
		// 1263
	}

	@Test
	public void streamExample_Sorted() {
		List<Integer> numbers = Arrays.asList(1, 1, 2, 6, 2,
				3);
		numbers.stream().sorted()
				.forEach(System.out::print);
		// 112236
	}

	@Test
	public void streamExample_Filter() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		numbers.stream().filter(StreamsTest::isOdd)
				.forEach(System.out::print);
		// 137
	}

	@Test
	public void streamExample_Collect() {
		List<Integer> numbers = Arrays.asList(1, 3, 4, 6, 2,
				7);
		List<Integer> oddNumbers = numbers.stream()
				.filter(StreamsTest::isOdd)
				.collect(Collectors.toList());
		System.out.println(oddNumbers);
		// [1, 3, 7]
	}

	// Collection within an object and matching against it
	class Player {
		private String name;
		private List<Integer> scores;

		public Player(String name, List<Integer> scores) {
			super();
			this.name = name;
			this.scores = scores;
		}

		public String getName() {
			return name;
		}

		public List<Integer> getScores() {
			return scores;
		}

	}

	List<Player> players = Arrays.asList(
			new Player("Player1",
					Arrays.asList(10, 9, 1, 10, 9)),
			new Player("Player2",
					Arrays.asList(7, 9, 1, 4, 9)),
			new Player("Player3",
					Arrays.asList(10, 10, 1, 10, 9)));

	@Test
	public void streamExample_AtleastOne10() {
		List<Player> filteredPlayers = players.stream()
				.filter(player -> player.getScores()
						.stream()
						.anyMatch(score -> score == 10))
				.collect(Collectors.toList());
		assertEquals(2, filteredPlayers.size());
	}

	@Test
	public void streamExample_AtleastOne10_GetOnlyNames() {
		List<String> filteredPlayers = players.stream()
				.filter(player -> player.getScores()
						.stream()
						.anyMatch(score -> score == 10))
				.collect(Collectors.mapping(Player::getName,
						Collectors.toList()));
		assertEquals(Arrays.asList("Player1", "Player3"),
				filteredPlayers);
		
		//Think about .stream().allMatch()
	}
}
```
