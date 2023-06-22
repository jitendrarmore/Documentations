# Documentations
All kind of documentations for learning


# To enable Swagger in a Spring Boot application, you can follow these steps:


## Step 1: Add dependencies
In your pom.xml file, add the following dependencies:


```xml
<dependency>
<groupId>io.springfox</groupId>
<artifactId>springfox-boot-starter</artifactId>
<version>3.0.0</version>
</dependency>
```


## Step 2: Configure Swagger
Create a new Java class, for example, SwaggerConfig, and annotate it with @Configuration and @EnableSwagger2WebMvc.


````java
import org.springframework.context.annotation.Configuration;
import springfox.documentation.swagger2.annotations.EnableSwagger2WebMvc;

@Configuration
@EnableSwagger2WebMvc
public class SwaggerConfig {

}

````


## Step 3: Customize Swagger Configuration (Optional)
If you want to customize the Swagger configuration, you can create additional methods in the SwaggerConfig class and use the appropriate annotations provided by the Swagger library. For example, you can specify the API title, description, version, etc.

```java
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2WebMvc;

@Configuration
@EnableSwagger2WebMvc
public class SwaggerConfig 
{

    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.controller"))
                .paths(PathSelectors.any())
                .build()
                .apiInfo(apiInfo());
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("My API")
                .description("API documentation for My Application")
                .version("1.0.0")
                .build();
    }
}

```


## Step 4: Access Swagger UI
Once you've added the dependencies and configured Swagger, you can access the Swagger UI by running your Spring Boot application and navigating to http://localhost:8080/swagger-ui/index.html in your browser. This will display the Swagger UI, where you can explore and test your API endpoints.

That's all ! You have now enabled Swagger in your Spring Boot application.
