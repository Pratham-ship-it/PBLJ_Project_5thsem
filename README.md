# Student Management System - REST API

A Spring Boot-based Student Management RESTful Web Service built for managing student records with full CRUD operations, input validation, and flexible database support (H2 in-memory by default, with MySQL support).

---

## 🛠️ Tech Stack

- **Java**: 21+
- **Framework**: Spring Boot 3.4.2
- **ORM & Data**: Spring Data JPA, Hibernate
- **Validation**: Jakarta Bean Validation (`@Valid`, `@NotBlank`, `@Email`, `@Min`, `@Max`)
- **Database**: H2 (In-memory, default) / MySQL (configurable)
- **Build Tool**: Maven Wrapper (`mvnw`)

---

## 🚀 Getting Started

### Prerequisites
- Java 21 or higher installed (`java -version`)
- Git

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Pratham-ship-it/PBLJ_Project_5thsem.git
   cd PBLJ_Project_5thsem
   ```

2. **Run using Maven Wrapper:**
   - **Windows:**
     ```powershell
     .\mvnw.cmd spring-boot:run
     ```
   - **Linux / macOS:**
     ```bash
     ./mvnw spring-boot:run
     ```

3. **Or Build and Run the JAR:**
   ```bash
   ./mvnw clean package -DskipTests
   java -jar target/student-management-0.0.1-SNAPSHOT.jar
   ```

The application starts on **port 8081** by default:
- **Base API URL:** `http://localhost:8081/api/students`
- **H2 Console:** `http://localhost:8081/h2-console`
  - JDBC URL: `jdbc:h2:mem:student_db`
  - Username: `sa`
  - Password: *(empty)*

---

## 📡 REST API Endpoints

| Method | Endpoint | Description | Status Code |
|---|---|---|---|
| `POST` | `/api/students` | Add a new student | `201 Created` |
| `GET` | `/api/students` | Get all students | `200 OK` |
| `GET` | `/api/students/{id}` | Get student by ID | `200 OK` |
| `GET` | `/api/students/course/{course}` | Get students by course | `200 OK` |
| `PUT` | `/api/students/{id}` | Update student details | `200 OK` |
| `DELETE` | `/api/students/{id}` | Delete student by ID | `204 No Content` |

---

## 📝 Sample Payloads

### 1. Add Student (`POST /api/students`)
```json
{
  "name": "Jane Doe",
  "email": "jane.doe@example.com",
  "course": "Computer Science",
  "age": 20
}
```

### 2. Update Student (`PUT /api/students/1`)
```json
{
  "name": "Jane Doe",
  "email": "jane.doe@example.com",
  "course": "Software Engineering",
  "age": 21
}
```

---

## ⚙️ Database Configuration

By default, the application runs with an **H2 in-memory database** for instant plug-and-play development.

To switch to **MySQL**:
1. Open `src/main/resources/application.properties`.
2. Uncomment the MySQL configuration lines:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/student_db
   spring.datasource.username=root
   spring.datasource.password=root
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   ```
3. Ensure MySQL is running on port 3306 and the database `student_db` exists.
