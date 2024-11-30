
# Bank Management System

![java__](https://github.com/user-attachments/assets/7034c956-3b14-410d-bf3a-d881309c9794)

## Project Overview

The Bank Management System is a Java-based application designed to manage various banking operations such as user registration, account management, transactions, and balance inquiries. The system aims to provide a seamless and secure banking experience for users.

## Features

- **User Registration**: Allows users to sign up and create a new account.
- **Account Management**: Users can view and manage their accounts.
- **Transactions**: Supports deposit, withdrawal, and fast cash transactions.
- **Balance Inquiry**: Users can check their current account balance.
- **Mini Statement**: Displays recent transactions and current balance.
- **PIN Change**: Allows users to change their account PIN.

## Technical Architecture

### Frontend

- **Java Swing**: Used for building the user interface.
- **Event Handlers**: Handles user interactions through ActionListeners and button clicks.
- **Database Access**: Uses JDBC to interact with the database.

### Backend

- **Spring Boot**: Used for building RESTful services.
- **Spring Data JPA**: Provides repository support for JPA, making it easy to implement CRUD operations.
- **Spring Security**: Secures the application by providing authentication and authorization mechanisms.
- **PostgreSQL**: Used as the database for storing user and transaction data.

## Setup Instructions

### Steps to Set Up Locally

1. **Clone the repository from GitHub**:

   ```sh
   git clone https://github.com/Jagdish20222/Bank_Management_System
   cd bank-management-system
   ```
2. **Install Java and PostgreSQL**:

   - **Java**: Download and install Java 17 from the [official website](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html).
   - **PostgreSQL**: Download and install PostgreSQL from the [official website](https://www.postgresql.org/download/).
3. **Configure the database connection in `application.properties`**:

   - Open the `application.properties` file located in `spring backend/src/main/resources/`.
   - Update the database connection details:
     ```properties
     spring.datasource.url=jdbc:postgresql://localhost:5432/bank_management_system
     spring.datasource.username=your_postgres_username
     spring.datasource.password=your_postgres_password

     spring.jpa.show-sql=true
     spring.jpa.properties.hibernate.format_sql=true
     spring.jpa.hibernate.ddl-auto=update
     spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect

     server.tomcat.accesslog.enabled=true
     ```
4. **Run the Spring Boot application**:

   ```sh
   cd spring backend
   mvn spring-boot:run
   ```
5. **Launch the Java Swing application**:

   - Open your IDE (e.g., IntelliJ IDEA, Eclipse).
   - Import the project.
   - Navigate to the main class of the Java Swing application (e.g., `main_Class.java`).
   - Run the main method to start the application.

### Dependencies

- **Java 17**
- **Spring Boot 3.0.9**
- **PostgreSQL**
- **Maven**

### Configuration

- Update `application.properties` with your PostgreSQL database credentials as shown in the steps above.

## Team Contributions

- **Jagdish**: Frontend development and UI design. Responsible for the Java Swing part.
- **Jsh**: Backend development and API implementation. Responsible for the Spring Boot part.
- **Megha**: Database design and integration. Also handled testing and documentation.

## Challenges and Solutions

### Technical Challenges

- **Database Connectivity**:
  - **Challenge**: Initially, the application faced issues with managing database connections efficiently. The default JDBC connection handling was not sufficient for handling multiple concurrent requests, leading to performance bottlenecks and potential connection leaks.
  - **Solution**: Implemented connection pooling using HikariCP, a high-performance JDBC connection pool. This allowed the application to manage database connections more efficiently, reducing the overhead of establishing new connections and improving overall performance. The configuration for HikariCP was added to the `application.properties` file:
    ```properties
    spring.datasource.hikari.maximum-pool-size=10
    spring.datasource.hikari.minimum-idle=5
    spring.datasource.hikari.idle-timeout=30000
    spring.datasource.hikari.max-lifetime=1800000
    spring.datasource.hikari.connection-timeout=30000
    ```

### UI Responsiveness

- **Challenge**: Ensuring the UI is responsive and user-friendly was a significant challenge. The initial design of the Java Swing application had issues with layout management, leading to components overlapping or not resizing correctly on different screen sizes.
  - **Solution**: Used Java Swing components and layout managers effectively to create a responsive and intuitive user interface. The `GridBagLayout` and `BorderLayout` managers were particularly useful in achieving a flexible and adaptive layout. Additionally, event listeners were added to handle user interactions smoothly, providing a better user experience.

### Security

- **Challenge**: Securing the application to protect user data and prevent unauthorized access was a critical requirement. The initial implementation lacked robust security measures.
  - **Solution**: Integrated Spring Security to handle authentication and authorization. Implemented JWT (JSON Web Token) for secure token-based authentication. The `JwtService` class was created to generate and validate tokens, ensuring that only authenticated users could access protected endpoints. The security configuration was defined in the `SecurityConfiguration` class:
    ```java
    @Configuration
    @EnableWebSecurity
    @RequiredArgsConstructor
    public class SecurityConfiguration {
        private final JwtService jwtService;
        private final AuthenticationProvider authenticationProvider;

        @Bean
        public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
            return http
                    .cors().and()
                    .csrf().disable()
                    .authorizeRequests()
                    .antMatchers("/auth/**").permitAll()
                    .anyRequest().authenticated()
                    .and()
                    .sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS)
                    .and()
                    .authenticationProvider(authenticationProvider)
                    .addFilterBefore(new JwtAuthenticationFilter(jwtService), UsernamePasswordAuthenticationFilter.class)
                    .build();
        }
    }
    ```

### Testing and Debugging

- **Challenge**: Ensuring the application was free of bugs and performed as expected required extensive testing and debugging.
  - **Solution**: Implemented unit tests and integration tests using JUnit and Mockito. The tests covered various aspects of the application, including service methods, repository interactions, and controller endpoints. Additionally, used Postman for manual API testing to verify the correctness of the endpoints. The test classes were annotated with `@SpringBootTest` and `@DataJpaTest` to set up the application context and test the database interactions.

## Learning Outcomes and Conclusion

### Skills Learned

- **Java Swing for UI Development**: Gained hands-on experience in designing and implementing user interfaces using Java Swing.
- **Spring Boot for Building RESTful Services**: Acquired knowledge in building RESTful APIs using Spring Boot.
- **PostgreSQL for Database Management**: Developed skills in managing databases using PostgreSQL.
- **Effective Team Collaboration and Project Management**: Improved collaboration and communication skills by working in a team. Learned how to use version control systems (Git), manage tasks, and coordinate efforts to achieve project goals.

### Reflections

The project provided valuable insights into building a full-stack application using Java technologies. It highlighted the importance of integrating frontend and backend components seamlessly and ensuring that the application is secure, efficient, and user-friendly. The experience gained from this project will be beneficial for future software development endeavors.

### Future Improvements

- **Enhancing Security Features**: Implement additional security measures such as two-factor authentication (2FA) and role-based access control (RBAC) to further protect user data and prevent unauthorized access.
- **Adding More Transaction Types**: Expand the functionality of the application by adding more transaction types, such as fund transfers between accounts, bill payments, and recurring transactions.
- **Optimizing Performance**: Continuously monitor and optimize the performance of the application. Implement caching mechanisms to reduce database load and improve response times.
- **Improving User Experience**: Enhance the user interface by adding more interactive elements, improving the layout, and providing better feedback to users. Conduct user testing to gather feedback and make necessary improvements.
- **Extending Test Coverage**: Increase the test coverage by adding more unit tests, integration tests, and end-to-end tests. Use automated testing tools to ensure the application remains stable and bug-free.

Overall, the project was a great learning experience that provided a solid foundation in full-stack development using Java technologies. The skills and knowledge gained will be valuable for future projects and career growth.
