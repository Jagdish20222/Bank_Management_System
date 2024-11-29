 Detailed Description of Each File in the Codebase

 Main Application Code

1. `BankManagementSystemApplication.java`

   - Description: The entry point of the Spring Boot application.
   - Spring Usage: Annotated with `@SpringBootApplication` to enable auto-configuration, component scanning, and configuration properties.
   - Data Flow: Starts the Spring application context.
2. `ApplicationConfig.java`

   - Description: Configuration class for setting up beans and application-wide settings.
   - Spring Usage: Annotated with `@Configuration` and `@RequiredArgsConstructor`. Defines beans for `AuthenticationManager`, `UserDetailsService`, `AuthenticationProvider`, and `PasswordEncoder`.
   - Data Flow: Configures security and CORS settings.

 Controllers

3. `AuthenticationController.java`

   - Description: Handles authentication-related requests such as login and registration.
   - Spring Usage: Annotated with `@RestController`, `@RequestMapping("/auth")`, and `@RequiredArgsConstructor`. Uses `@PostMapping` for login and registration endpoints.
   - Data Flow: Receives HTTP requests, validates input, and delegates to `AuthenticationService`.
4. `AccountController.java`

   - Description: Manages user accounts, including creating new accounts and retrieving account details.
   - Spring Usage: Annotated with `@RestController`, `@RequestMapping("/accounts")`, and `@RequiredArgsConstructor`. Uses `@PostMapping` and `@GetMapping` for account-related endpoints.
   - Data Flow: Receives HTTP requests, validates input, and delegates to `AccountService`.
5. `TransactionController.java`

   - Description: Handles transaction-related requests such as deposits and withdrawals.
   - Spring Usage: Annotated with `@RestController`, `@RequestMapping("/transaction")`, and `@RequiredArgsConstructor`. Uses `@PostMapping` for transaction endpoints.
   - Data Flow: Receives HTTP requests, validates input, and delegates to `TransactionService`.

 Entities

6. `User.java`

   - Description: Represents a user in the system.
   - Spring Usage: Annotated with `@Entity` and `@Table(name = "bank_user")`. Implements `UserDetails` for Spring Security.
   - Data Flow: Mapped to the `bank_user` table in the database.
7. `Account.java`

   - Description: Represents a bank account.
   - Spring Usage: Annotated with `@Entity` and `@Table(name = "account")`.
   - Data Flow: Mapped to the `account` table in the database.
8. `Transaction.java`

   - Description: Represents a transaction.
   - Spring Usage: Annotated with `@Entity` and `@Table(name = "transaction")`.
   - Data Flow: Mapped to the `transaction` table in the database.

 Repositories

9. `UserRepository.java`

   - Description: Repository interface for `User` entity.
   - Spring Usage: Extends `JpaRepository<User, Long>`.
   - Data Flow: Provides CRUD operations for `User` entity.
10. `AccountRepository.java`

    - Description: Repository interface for `Account` entity.
    - Spring Usage: Extends `JpaRepository<Account, Long>`.
    - Data Flow: Provides CRUD operations for `Account` entity.
11. `TransactionRepository.java`

    - Description: Repository interface for `Transaction` entity.
    - Spring Usage: Extends `JpaRepository<Transaction, Long>`.
    - Data Flow: Provides CRUD operations for `Transaction` entity.

 Services

12. `AuthenticationService.java`

    - Description: Interface for authentication-related operations.
    - Spring Usage: Annotated with `@Service`.
    - Data Flow: Defines methods for login and registration.
13. `AuthenticationServiceImpl.java`

    - Description: Implementation of `AuthenticationService`.
    - Spring Usage: Annotated with `@Service` and `@RequiredArgsConstructor`.
    - Data Flow: Implements login and registration logic, interacts with `UserRepository` and `JwtService`.
14. `AccountService.java`

    - Description: Interface for account-related operations.
    - Spring Usage: Annotated with `@Service`.
    - Data Flow: Defines methods for creating and retrieving accounts.
15. `AccountServiceImpl.java`

    - Description: Implementation of `AccountService`.
    - Spring Usage: Annotated with `@Service` and `@RequiredArgsConstructor`.
    - Data Flow: Implements account creation and retrieval logic, interacts with `AccountRepository`.
16. `TransactionService.java`

    - Description: Interface for transaction-related operations.
    - Spring Usage: Annotated with `@Service`.
    - Data Flow: Defines methods for deposits and withdrawals.
17. `TransactionServiceImpl.java`

    - Description: Implementation of `TransactionService`.
    - Spring Usage: Annotated with `@Service` and `@RequiredArgsConstructor`.
    - Data Flow: Implements deposit and withdrawal logic, interacts with `AccountRepository` and `TransactionRepository`.

 Mappers

18. `UserMapper.java`

    - Description: Interface for mapping `User` entity to response models.
    - Spring Usage: Annotated with `@Mapper`.
    - Data Flow: Converts `User` entity to response model.
19. `AccountMapper.java`

    - Description: Interface for mapping `Account` entity to response models.
    - Spring Usage: Annotated with `@Mapper`.
    - Data Flow: Converts `Account` entity to response model.
20. `TransactionMapper.java`

    - Description: Interface for mapping `Transaction` entity to response models.
    - Spring Usage: Annotated with `@Mapper`.
    - Data Flow: Converts `Transaction` entity to response model.
21. `TransactionMapperImpl.java`

    - Description: Implementation of `TransactionMapper`.
    - Spring Usage: Annotated with `@Component`.
    - Data Flow: Implements mapping logic for `Transaction` entity.

 Models

22. `ResponseModel.java`

    - Description: Generic response model for API responses.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used as a standard response format for API endpoints.
23. `RegisterRequestModel.java`

    - Description: Request model for user registration.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to capture registration data from clients.
24. `LoginRequestModel.java`

    - Description: Request model for user login.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to capture login data from clients.
25. `AuthenticationResponseModel.java`

    - Description: Response model for authentication responses.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to return authentication data to clients.
26. `AccountResponseModel.java`

    - Description: Response model for account details.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to return account details to clients.
27. `DepositRequestModel.java`

    - Description: Request model for deposit transactions.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to capture deposit data from clients.
28. `WithdrawRequestModel.java`

    - Description: Request model for withdrawal transactions.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to capture withdrawal data from clients.
29. `TransactionResponseModel.java`

    - Description: Response model for transaction details.
    - Spring Usage: Annotated with Lombok annotations (`@Data`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@Builder`).
    - Data Flow: Used to return transaction details to clients.

 Security

30. `SecurityConfiguration.java`

    - Description: Configures security settings for the application.
    - Spring Usage: Annotated with `@Configuration`, `@EnableWebSecurity`, and `@RequiredArgsConstructor`. Configures `SecurityFilterChain` bean.
    - Data Flow: Sets up security filters, authentication providers, and session management.
31. `JwtService.java`

    - Description: Provides JWT-related operations such as token generation and validation.
    - Spring Usage: Annotated with `@Service`.
    - Data Flow: Generates and validates JWT tokens.
32. `JwtAuthenticationFilter.java`

    - Description: Filters incoming requests to validate JWT tokens.
    - Spring Usage: Annotated with `@Component`.
    - Data Flow: Intercepts requests to validate JWT tokens and set authentication context.

 Configuration

33. `OpenApiConfig.java`
    - Description: Configures OpenAPI/Swagger for API documentation.
    - Spring Usage: Annotated with `@Configuration`.
    - Data Flow: Sets up Swagger UI and API documentation.

 Utilities

34. `Utils.java`
    - Description: Contains utility methods used across the application.
    - Spring Usage: Annotated with `@Component`.
    - Data Flow: Provides common utility functions.

 Test Classes

35. `BankManagementSystemApplicationTests.java`

    - Description: Contains tests for the main application context.
    - Spring Usage: Annotated with `@SpringBootTest`.
    - Data Flow: Tests if the application context loads correctly.
36. `AccountRepositoryTest.java`

    - Description: Contains tests for `AccountRepository`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)`, `@DataJpaTest`, and `@AutoConfigureTestDatabase(connection = EmbeddedDatabaseConnection.H2)`.
    - Data Flow: Tests CRUD operations for `Account` entity.
37. `UserRepositoryTest.java`

    - Description: Contains tests for `UserRepository`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)`, `@DataJpaTest`, and `@AutoConfigureTestDatabase(connection = EmbeddedDatabaseConnection.H2)`.
    - Data Flow: Tests CRUD operations for `User` entity.
38. `AccountServiceImplTest.java`

    - Description: Contains tests for `AccountServiceImpl`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)` and `@SpringBootTest`.
    - Data Flow: Tests business logic for account-related operations.
39. `AuthenticationServiceImplTest.java`

    - Description: Contains tests for `AuthenticationServiceImpl`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)` and `@SpringBootTest`.
    - Data Flow: Tests business logic for authentication-related operations.
40. `TransactionServiceImplTest.java`

    - Description: Contains tests for `TransactionServiceImpl`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)` and `@SpringBootTest`.
    - Data Flow: Tests business logic for transaction-related operations.
41. `UserServiceImplTest.java`

    - Description: Contains tests for `UserServiceImpl`.
    - Spring Usage: Annotated with `@ExtendWith(SpringExtension.class)` and `@SpringBootTest`.
    - Data Flow: Tests business logic for user-related operations.

 Configuration Files

42. `application.properties`

    - Description: Configuration file for Spring Boot application settings.
    - Spring Usage: Configures data source, JPA properties, and server settings.
    - Data Flow: Provides configuration for connecting to PostgreSQL database.
43. `application-test.properties`

    - Description: Configuration file for Spring Boot application settings during testing.
    - Spring Usage: Configures data source, JPA properties, and server settings for H2 database.
    - Data Flow: Provides configuration for connecting to H2 in-memory database during tests.

 Build and Run

44. `pom.xml`

    - Description: Maven configuration file for managing dependencies and build configuration.
    - Spring Usage: Defines dependencies for Spring Boot, Spring Data JPA, Spring Security, Lombok, PostgreSQL, H2, and testing libraries.
    - Data Flow: Manages project dependencies and build lifecycle.
45. 

mvnw

 and

mvnw.cmd

    - Description: Maven wrapper scripts for building and running the application.
    - Spring Usage: Provides a standardized way to run Maven commands.
    - Data Flow: Executes Maven build and run commands.

 Docker

Dockerfile

    - Description: Docker configuration file for containerizing the application.
    - Spring Usage: Defines build and runtime stages for the Docker image.
    - Data Flow: Builds a Docker image and runs the application in a container.

 Data Flow and CRUD APIs

 Data Flow

1. User Registration and Login

   - Flow: `AuthenticationController` -> `AuthenticationService` -> `UserRepository` -> `JwtService`
   - Description: Handles user registration and login, generates JWT tokens.
2. Account Management

   - Flow: `AccountController` -> `AccountService` -> `AccountRepository`
   - Description: Manages account creation and retrieval.
3. Transaction Management

   - Flow: `TransactionController` -> `TransactionService` -> `AccountRepository` and `TransactionRepository`
   - Description: Handles deposit and withdrawal transactions.

 CRUD APIs

1. User Registration

   - Endpoint: `POST /auth/register`
   - Controller: `AuthenticationController`
   - Service: `AuthenticationService`
   - Repository: `UserRepository`
2. User Login

   - Endpoint: `POST /auth/login`
   - Controller: `AuthenticationController`
   - Service: `AuthenticationService`
   - Repository: `UserRepository`
3. Create New Account

   - Endpoint: `POST /accounts`
   - Controller: `AccountController`
   - Service: `AccountService`
   - Repository: `AccountRepository`
4. Get My Accounts

   - Endpoint: `GET /accounts`
   - Controller: `AccountController`
   - Service: `AccountService`
   - Repository: `AccountRepository`
5. Deposit

   - Endpoint: `POST /transaction/deposit`
   - Controller: `TransactionController`
   - Service: `TransactionService`
   - Repository: `AccountRepository` and `TransactionRepository`
6. Withdraw

   - Endpoint: `POST /transaction/withdraw`
   - Controller: `TransactionController`
   - Service: `TransactionService`
   - Repository: `AccountRepository` and `TransactionRepository`

 Spring Framework and JDBC Connection

- Spring Boot: Used to create a stand-alone, production-grade Spring-based application.
- Spring Data JPA: Provides repository support for JPA, making it easy to implement CRUD operations.
- Spring Security: Secures the application by providing authentication and authorization mechanisms.
- Spring Web: Provides support for building web applications, including RESTful services.
- Spring Test: Provides support for testing Spring applications.
- JDBC and PostgreSQL: The application uses Spring Data JPA to interact with the PostgreSQL database. The `application.properties` file contains the necessary configurations for connecting to the PostgreSQL database. During testing, the application uses an H2 in-memory database, configured in the `application-test.properties` file.

This detailed description should give you a comprehensive understanding of the structure, functionality, and data flow of the Bank Management System codebase.
