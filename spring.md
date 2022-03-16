# spring 
using spring will build an application that has a static home page and that will also accept HTTP GET requests , and will respond with a web page that displays HTML.

In Spring’s approach to building web sites, HTTP requests are handled by a controller. You can easily identify the controller by the @Controller annotation.
handles GET requests for /greeting by returning the name of a View . A View is responsible for rendering the HTML content.

package com.example.servingwebcontent;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller

public class GreetingController {

	@GetMapping("/greeting") //getMapping annotation ensures that HTTP GET requests to /greeting are mapped to the greeting() method.
  
	public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
  
  //binds the value of the query string parameter name into the name parameter of the greeting() method.
  
		model.addAttribute("name", name);
    
		return "greeting";
    
	}

}
	
  
  

package com.example.servingwebcontent;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ServingWebContentApplication {

    public static void main(String[] args) {
        SpringApplication.run(ServingWebContentApplication.class, args);//@Configuration: Tags the class as a source of bean definitions for the application context.
        
        //@EnableAutoConfiguration: Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings. For example, 
        if spring-webmvc is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a DispatcherServlet
        
        //@ComponentScan: Tells Spring to look for other components, configurations, and services in the com/example package, letting it find the controllers
    }

}

ou can run the application from the command line with Gradle or Maven. You can also build a single executable JAR file that contains all the necessary dependencies, 
classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle,
across different environments, and so forth

If you use Gradle, you can run the application by using ./gradlew bootRun. Alternatively, you can build the JAR file by using ./gradlew build and then run the JAR file, 
as follows: java -jar build/libs/gs-serving-web-content-0.1.0.jar

to see if it work enter the localhost url in browser ,and enter the query if u want .


## spring mvc 
Spring MVC calls the pieces of data that can be accessed during the execution of views model attributes. The equivalent term in Thymeleaf language is context variables.

**threre 2 classes for spring  :**

-@controller :re responsible for preparing a model map with data and selecting a view to be rendered.

-@modal :  allows for the complete abstraction of the view technology and, in the case of Thymeleaf, it is transformed into a Thymeleaf context object

There are several ways of adding model attributes to a view in Spring MVC. Below you will find some common cases:

Add attribute to Model via its addAttribute method:

  @RequestMapping(value = "message", method = RequestMethod.GET)
        public String messages(Model model) {
            model.addAttribute("messages", messageRepository.findAll());
            return "message/list";
        }
       
       
**-Request parameters **

Request parameters can be easily accessed in Thymeleaf views. Request parameters are passed from the client to server like:

    https://example.com/query?q=Thymeleaf+Is+Great!
   
 **-Session attributes**
 In the below example we add mySessionAttribute to session:
  @RequestMapping({"/"})
        String index(HttpSession session) {
            session.setAttribute("mySessionAttribute", "someValue");
            return "index";
        }
        
**ServletContext attributes** 
he ServletContext attributes are shared between requests and sessions. In order to access ServletContext attributes in Thymeleaf you can use the #servletContext.

**Spring beans**
Thymeleaf allows accessing beans registered at the Spring Application Context with the @beanName syntax, for example:

    <div th:text="${@urlService.getApplicationUrl()}">...</div> 
    
In the above example, @urlService refers to a Spring Bean registered at your context, e.g.

  @Configuration
        public class MyConfiguration {
            @Bean(name = "urlService")
            public UrlService urlService() {
                return () -> "domain.com/myapp";
            }
        }

        public interface UrlService {
            String getApplicationUrl();
        }

        
        
        
        
        



