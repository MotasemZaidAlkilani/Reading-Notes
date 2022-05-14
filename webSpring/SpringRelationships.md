# Relationships in Spring Data REST

## One-to-One Relationship
*In a one-to-one relationship, one record in a table is associated with one and only one record in another table. For example, in a school database,
each student has only one student ID, and each student ID is assigned to only one person.*

_____________________________________________________________________________________________________________________________________________________

#### how to make it works in code ?
I want to make one-one relation between person and student id

1-make **@Entity** for person class 

2- use @OneToOne annotation to student id variable.

note :student id is a variable inside person class.

## One-to-Many Relationship
*In a one-to-many relationship, one record in a table can be associated with one or more records in another table.
For example, each customer can have many sales orders.*

_____________________________________________________________________________________________________________________________________________________

#### how to make it works in code ?
I want to make one-many relation between customer and sales orders

1-make **@Entity** for customer class 

2- use  @ManyToOne annotation to sales orders variable.

##  Many-to-Many Relationship
*A many-to-many relationship occurs when multiple records in a table are associated with multiple records in another table. 
For example, a many-to-many relationship exists between customers and products:
customers can purchase various products, and products can be purchased by many customers.*

_____________________________________________________________________________________________________________________________________________________

#### how to make it works in code ?
I want to make one-one relation between customers and products

1-make **@Entity** for customers class 

2- use @ManyToMany annotation to products array variables.


## Integration Testing
*Integration testing is the second level of the software testing process comes after unit testing. In this testing, units or individual components of the software are
tested in a group. The focus of the integration testing level is to expose defects at the time of interaction between integrated components or units*

_____________________________________________________________________________________________________________________________________________________

#### how to make it works in code ?

1- we need to prepare the junit and spring-test dependencies  

2-by using jUnit5 , enable this extension by adding the @ExtendWith annotation to our test classes

3-annotate the test with @WebAppConfiguration, which will load the web application context

4- now for writing intergation testing

5-

**@Test**

**public void TestClass() {**

 **this.mockMvc.perform(get("/homePage")).andDo(print()).andExpect(view().name("index")); }**

#### what codes mean ?

-perform() method will call a GET request method, which returns the ResultActions.
Using this result, we can have assertion expectations about the response, like its content, HTTP status, or header.

-andDo(print()) will print the request and response. This is helpful to get a detailed view in case of an error.

-andExpect() will expect the provided argument. In our case, we're expecting “index” to be returned via MockMvcResultMatchers.view().





