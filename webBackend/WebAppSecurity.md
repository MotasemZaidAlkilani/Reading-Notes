 # Web App Security
 
 simple Entity Relationship Diagram – which shows the many-to-many association between two entities employee and project:
 
 <img src="https://www.baeldung.com/wp-content/uploads/2017/09/New.png"/>
 
## Database Setup

 need to create the employee and project tables along with the employee_project join table with employee_id and project_id as foreign keys
```
CREATE TABLE `employee` (
  `employee_id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(50) DEFAULT NULL,
  `last_name` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`employee_id`)
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8;

CREATE TABLE `project` (
  `project_id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`project_id`)
) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8;

CREATE TABLE `employee_project` (
  `employee_id` int(11) NOT NULL,
  `project_id` int(11) NOT NULL,
  PRIMARY KEY (`employee_id`,`project_id`),
  KEY `project_id` (`project_id`),
  CONSTRAINT `employee_project_ibfk_1` 
   FOREIGN KEY (`employee_id`) REFERENCES `employee` (`employee_id`),
  CONSTRAINT `employee_project_ibfk_2` 
   FOREIGN KEY (`project_id`) REFERENCES `project` (`project_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## The Model Classes

The model classes Employee and Project need to be created with JPA annotations
```
@Entity
@Table(name = "Employee")
public class Employee { 
    // ...
 
    @ManyToMany(cascade = { CascadeType.ALL })
    @JoinTable(
        name = "Employee_Project", 
        joinColumns = { @JoinColumn(name = "employee_id") }, 
        inverseJoinColumns = { @JoinColumn(name = "project_id") }
    )
    Set<Project> projects = new HashSet<>();
   
    // standard constructor/getters/setters
}
@Entity
@Table(name = "Project")
public class Project {    
    // ...  
 
    @ManyToMany(mappedBy = "projects")
    private Set<Employee> employees = new HashSet<>();
    
    // standard constructors/getters/setters   
}
```

## Execution

```
public class HibernateManyToManyAnnotationMainIntegrationTest {
	private static SessionFactory sessionFactory;
	private Session session;

	//...

	@Test
        public void givenSession_whenRead_thenReturnsMtoMdata() {
	    prepareData();
       	    @SuppressWarnings("unchecked")
	    List<Employee> employeeList = session.createQuery("FROM Employee").list();
            @SuppressWarnings("unchecked")
	    List<Project> projectList = session.createQuery("FROM Project").list();
            assertNotNull(employeeList);
            assertNotNull(projectList);
            assertEquals(2, employeeList.size());
            assertEquals(2, projectList.size());
        
            for(Employee employee : employeeList) {
               assertNotNull(employee.getProjects());
               assertEquals(2, employee.getProjects().size());
            }
            for(Project project : projectList) {
               assertNotNull(project.getEmployees());
               assertEquals(2, project.getEmployees().size());
            }
        }

	private void prepareData() {
	    String[] employeeData = { "Peter Oven", "Allan Norman" };
	    String[] projectData = { "IT Project", "Networking Project" };
	    Set<Project> projects = new HashSet<Project>();

	    for (String proj : projectData) {
		projects.add(new Project(proj));
	    }

	    for (String emp : employeeData) {
		Employee employee = new Employee(emp.split(" ")[0], emp.split(" ")[1]);
		employee.setProjects(projects);
			
	        for (Project proj : projects) {
		    proj.getEmployees().add(employee);
		}
			
		session.persist(employee);
	    }
	}
	
	//...
}
```
