# spring-poc

spring boot
	spring mvc
	spring security
	

	src
		| main
			| java
			| resources
				| static -> index.html
				| templates ->
				| application.properties
		| test


add the security starter dependency:-
This will include the SecurityAutoConfiguration class – containing the initial/default security configuration.

Simply put, by default, the Authentication gets enabled for the Application. 
Also, content negotiation is used to determine if basic or formLogin should be used.

i.e :- by including only spring-security dependency, localhost:8080/ will be redirected to localhost:8080/login by default

application.properties
spring.security.user.name=megz
spring.security.user.password=dureja

******************************************************************************************************

If we don’t configure the password using the predefined property spring.security.user.password and start the application, 
we’ll notice that a default password is randomly generated and printed in the console log:
Using default security password: c8be15de-4488-4490-9dc6-fab3f91435c6


******************************************************************************************************

Disabling the Auto-Configuration

@SpringBootApplication(exclude = { SecurityAutoConfiguration.class })
public class SpringBootSecurityApplication {
 
    public static void main(String[] args) {
        SpringApplication.run(SpringBootSecurityApplication.class, args);
    }
}

			OR

spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.security.SecurityAutoConfiguration

******************************************************************************************************

Customizing an existing security setup to fulfill our needs

If we want a more flexible configuration, with multiple users and roles for example – 
you now need to make use of a full @Configuration class:
