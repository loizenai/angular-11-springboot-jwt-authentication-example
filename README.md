# Angular 11 SpringBoot JWT Authentication Example

[Angular 11 SpringBoot JWT Authentication Example](https://loizenai.com/angular-11-spring-boot-jwt-authentication-example/)

![Angular 11 SpringBoot JWT Authentication Example](https://loizenai.com/wp-content/uploads/2020/12/Angular-11-SpringBoot-Jwt-Authentication-Example-1.png)

In tutorial ‘Angular 11 Spring Boot JWT Token Based Authentication Example’, I guide you very clearly how to implement full stack example to demonistrade an jwt token based authentication flow from frontend Angular 11 to backend: SpringBoot and MySQL.

* Technology Stack: Angular11, SpringBoot, Jwt, SpringBoot, MySQL, PostgreSQL, Spring Security, Spring JPA

– I give you an Epic of the application, a fullstack excutive flow from frontend Angular 11 to backend jwt SpringBoot Security to database (MySQL/PostgreSQL) with overall architecture diagram.
– I give you a layer diagram of Angular 11 Jwt Authentication application with localStorage and Angular HttpClient (plus Interceptor)
– I guide you detail-steps how to implement a security SpringBoot Jwt Token Authentication.
– I guide you step by step how to develop a Angular 11 Jwt Authentication application.
– Finally, I do an integrative testing from Angular 11 to Jwt Based Token SpringBoot Security RestApis.

## Overview Angular 11 Spring Boot JWT Authentication example
We will build an application, from frontend (Angular 11) to backend (Spring Boot), which allows users to register, login account. This application is secured with JWT (JSON Web Token) authentication and Spring Security. Then, depending on the role of current User (user, pm or admin), this system accepts what he can access:

![Overview Angular 11 Spring Boot JWT Authentication example](https://loizenai.com/wp-content/uploads/2020/05/Angular-Login-Form.png)

![Register Form](https://loizenai.com/wp-content/uploads/2020/05/Register-Form.png)

![Home Page of Jack User](https://loizenai.com/wp-content/uploads/2020/05/Home-Page-of-Jack-User.png)

![Content of Jack User](https://loizenai.com/wp-content/uploads/2020/05/Content-of-Jack-User.png)

The diagram below show how our system handles User Registration and User Login processes:

![Angular Spring Boot Security Jwt Authentication Work Process Diagram](https://loizenai.com/wp-content/uploads/2020/05/Angular-Spring-Boot-Security-Jwt-Authentication-Work-Process-Diagram.png)

This is diagram for SpringBoot Token based authentication Security/JWT classes that are separated into 3 layers:
– HTTP
– Spring Security
– REST API

![Spring Boot Angular Spring Security Jwt Authentication Architecture Diagram Back End Server](https://loizenai.com/wp-content/uploads/2020/05/Spring-Boot-Angular-Spring-Security-Jwt-Authentication-Architecture-Diagram-Back-End-Server.png)

– SecurityContextHolder provides access to the SecurityContext.
– SecurityContext holds the Authentication and possibly request-specific security information.
– Authentication represents the principal which includes GrantedAuthority that reflects the application-wide permissions granted to a principal.
– UserDetails contains necessary information to build an Authentication object from DAOs or other source of security data.
– UserDetailsService helps to create a UserDetails from a String-based username and is usually used by AuthenticationProvider.
– JwtAuthTokenFilter (extends OncePerRequestFilter) pre-processes HTTP request, from Token, create Authentication and populate it to SecurityContext.
– JwtProvider validates, parses token String or generates token String from UserDetails.
– UsernamePasswordAuthenticationToken gets username/password from login Request and combines into an instance of Authentication interface.
– AuthenticationManager uses DaoAuthenticationProvider (with help of UserDetailsService & PasswordEncoder) to validate instance of UsernamePasswordAuthenticationToken, then returns a fully populated Authentication instance on successful authentication.
– SecurityContext is established by calling SecurityContextHolder.getContext().setAuthentication(…​) with returned authentication object above.
– AuthenticationEntryPoint handles AuthenticationException.
– Access to Restful API is protected by HTTPSecurity and authorized with Method Security Expressions.

In the tutorial, “Angular 11 Spring Boot JWT Authentication Example”, we need the Angular HTTP Interceptor to add JWT Authentication Token Based for Security:

![SpringBoot Angular Spring Security Jwt Authentication Architecture Diagram Front End Client](https://loizenai.com/wp-content/uploads/2020/05/SpringBoot-Angular-Spring-Security-Jwt-Authentication-Architecture-Diagram-Front-End-Client.png)

– app.component is the parent component that contains routerLink and router-outlet for routing. It also has an authority variable as the condition for displaying items on navigation bar.
– user.component, pm.component, admin.component correspond to Angular Components for User Board, PM Board, Admin Board. Each Board uses user.service to access authority data.
– register.component contains User Registration form, submission of the form will call auth.service.
– login.component contains User Login form, submission of the form will call auth.service and token-storage.service.

– user.service gets access to authority data from Server using Angular HttpClient ($http service).
– auth.service handles authentication and signup actions with Server using Angular HttpClient ($http service).
– every HTTP request by $http service will be inspected and transformed before being sent to the Server by auth-interceptor (implements HttpInterceptor).
– auth-interceptor check and get Token from token-storage.service to add the Token to Authorization Header of the HTTP Requests.

– token-storage.service manages Token inside Browser’s sessionStorage.

## Related post

- [Angular CRUD Application with SpringBoot and MySQL/PostgreSQL RestAPIs – Fullstack Angular 10-9-8 HttpClient Post/Get/Put/Delete](https://loizenai.com/angular-crud-application-with-springboot-and-mysql-postgresql-restapis-fullstack-angular-httpclient-post-get-put-delete/)
- [Build SpringBoot CRUD Application – FullStack: Frontend (Bootstrap and Ajax) to Backend (SpringBoot and MySQL/PostgreSQL database)](https://loizenai.com/build-springboot-crud-application-fullstack-frontend-bootstrap-and-ajax-to-backend-springboot-and-mysql-postgresql-database/)
- [Angular Nodejs Fullstack CRUD Application with MySQL/PostgreSQL – Angular 10-9-8 HttpClient + Nodejs Express, Sequelize ORM](https://loizenai.com/angular-nodejs-fullstack-crud-application-with-mysql-postgresql-angular-10-9-8-httpclient-client-nodejs-express-sequelize-orm/)
- [SpringBoot Jwt Authentication Example](https://loizenai.com/spring-boot-security-jwt-authentication-example-mysql-postgresql-spring-jpa-restapis/)
