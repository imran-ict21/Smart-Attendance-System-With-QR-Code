# Smart Attendance System with QR Code

<p align="center">
  <strong>A Java Desktop Application for Dynamic QR-Code-Based Student Attendance</strong><br>
  Project-II (ICT-2200) · Object Oriented Programming and Design with Java
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-21-orange?logo=openjdk" alt="Java 21">
  <img src="https://img.shields.io/badge/JavaFX-Desktop%20UI-blue" alt="JavaFX">
  <img src="https://img.shields.io/badge/Database-MySQL%208-4479A1?logo=mysql&logoColor=white" alt="MySQL 8">
  <img src="https://img.shields.io/badge/Database%20Access-JDBC-informational" alt="JDBC">
  <img src="https://img.shields.io/badge/QR-ZXing-black" alt="ZXing">
  <img src="https://img.shields.io/badge/Build-Maven-C71A36?logo=apachemaven&logoColor=white" alt="Maven">
</p>

---

## Project Information

| Item | Details |
|---|---|
| Project Title | **Smart Attendance System with QR Code** |
| Course | Project-II (ICT-2200) |
| Course Area | Object Oriented Programming and Design with Java |
| Department | Department of Information and Communication Technology (ICT) |
| University | **Mawlana Bhashani Science and Technology University (MBSTU)** |
| Academic Level | 2nd Year, 2nd Semester |
| Application Type | Java desktop application |
| Repository | [Smart Attendance System with QR Code](https://github.com/imran-ict21/Smart-Attendance-System-With-QR-Code) |

### Submitted By

| Student Name | Student ID |
|---|---|
| **Imran Hossen** | **IT 24063** |
| **Md. Jahidul Islam** | **IT 24018** |

### Project Supervisor

**Dr. Md. Abir Hossain**  
Professor  
Department of Information and Communication Technology (ICT)  
Mawlana Bhashani Science and Technology University (MBSTU)

---

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [Key Features](#key-features)
- [User Roles](#user-roles)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Application Workflow](#application-workflow)
- [Dynamic QR-Code Mechanism](#dynamic-qr-code-mechanism)
- [QR Validation Rules](#qr-validation-rules)
- [Database Design](#database-design)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation and Setup](#installation-and-setup)
- [Database Configuration](#database-configuration)
- [Running the Application](#running-the-application)
- [Main Functional Modules](#main-functional-modules)
- [Important Implementation Concepts](#important-implementation-concepts)
- [Attendance Percentage](#attendance-percentage)
- [CSV Export](#csv-export)
- [Security Considerations](#security-considerations)
- [Testing and Verification](#testing-and-verification)
- [Observed Application Screens](#observed-application-screens)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Troubleshooting](#troubleshooting)
- [Learning Outcomes](#learning-outcomes)
- [Contributors](#contributors)
- [Supervisor](#supervisor)
- [Acknowledgement](#acknowledgement)
- [References](#references)
- [License](#license)

---

## Overview

The **Smart Attendance System with QR Code** is a Java-based desktop application developed to make classroom attendance faster, more organized, and easier to manage. It replaces the conventional roll-call or paper-based attendance process with a dynamic QR-code-based approach.

A teacher creates a course and starts a class session. The application generates a QR code associated with that active session and displays it on the teacher's screen or projector. The QR code is automatically renewed every **25 seconds**. A student selects the corresponding course, starts the webcam, and scans the displayed QR code. After the required validation checks are completed, the application records the student's attendance in a MySQL database.

The application also provides role-based dashboards, course management, student enrollment, attendance summaries, date-wise attendance sheets, profile settings, password change functionality, and CSV export.

The project is developed as an academic project for **Project-II (ICT-2200)** under the Department of Information and Communication Technology at Mawlana Bhashani Science and Technology University.

### Project at a Glance

| Property | Description |
|---|---|
| Interface | JavaFX desktop interface using FXML and CSS |
| Programming Language | Java 21 |
| Database | MySQL 8 |
| Database Connectivity | JDBC with PreparedStatement |
| QR Generation and Decoding | ZXing |
| Camera Access | webcam-capture (Sarxos) |
| Build and Dependency Management | Maven |
| Development Environment | IntelliJ IDEA |
| QR Refresh Interval | 25 seconds |
| Webcam Frame Scan Interval | 400 milliseconds |
| Attendance Output | Present/Absent records and attendance percentage |
| Export Format | CSV |

---

## Problem Statement

Traditional attendance procedures often require teachers to call student names or circulate a paper attendance sheet. These methods create several practical difficulties:

1. **Time consumption:** Roll call takes valuable time away from lectures, particularly in large classes.
2. **Manual errors:** Paper-based records may contain missing, duplicated, or incorrectly entered information.
3. **Proxy attendance:** A student may sign or respond on behalf of an absent student.
4. **Difficult record management:** Searching, updating, and preserving paper attendance sheets can be inconvenient.
5. **Manual calculation:** Teachers have to calculate attendance percentages and prepare reports manually.
6. **Limited student access:** Students may not have a convenient way to check their attendance status for each course.

This project addresses these issues through a centralized database and a dynamic QR-code-based attendance workflow.

---

## Project Objectives

The primary objectives of the project are:

- To develop a desktop-based attendance management system using Java.
- To reduce the time required to record classroom attendance.
- To introduce dynamic QR codes that automatically refresh after a fixed interval.
- To make old QR-code screenshots invalid after token renewal.
- To store student, teacher, course, session, and attendance information in MySQL.
- To allow teachers to create courses and manage class sessions.
- To allow students to browse and enroll in available courses.
- To validate a scanned QR code before recording attendance.
- To prevent duplicate attendance records for the same student and session.
- To display course-wise attendance information and percentage.
- To provide date-wise attendance sheets for teachers.
- To export attendance reports in CSV format.
- To apply object-oriented programming concepts and a layered software architecture.

---

## Key Features

### 1. Role-Based Registration and Login

The application supports two user roles:

- **Student**
- **Teacher**

Users register and log in using their email address and password. The application directs authenticated users to the appropriate dashboard according to their role.

### 2. Teacher Dashboard

The teacher dashboard provides access to the teacher's courses and attendance-management operations.

Main functions include:

- Create a new course.
- View the courses created by the teacher.
- Enter an optional topic for the class.
- Start a new class session.
- Generate and display a dynamic QR code.
- Close an active class session.
- View the attendance sheet.
- Export attendance data as a CSV file.
- Open profile settings and change the password.

### 3. Student Dashboard

The student dashboard provides access to course and attendance information.

Main functions include:

- View available or enrolled courses.
- Browse courses and enroll where applicable.
- Select a course for attendance scanning.
- Start the webcam.
- Scan the teacher's active QR code.
- Receive attendance status feedback.
- View course-wise attendance information and percentage.
- Update profile information and change the password.

### 4. Dynamic QR Code

The QR code is generated for an active class session and contains a session identifier and a temporary token. The token is renewed every **25 seconds**. The application updates the QR display and its countdown/progress indicator after renewal.

### 5. Webcam-Based QR Scanning

The student-side scanning screen uses the webcam to capture frames. The application checks frames at approximately **400-millisecond intervals** and uses ZXing to decode QR-code content.

### 6. Attendance Validation

Before an attendance record is inserted, the application checks the active session, QR token, expiry time, selected course, course enrollment, and duplicate attendance status.

### 7. Duplicate Attendance Prevention

A student cannot be marked present more than once for the same class session. The attendance layer checks for an existing record before inserting a new one.

### 8. Attendance Sheet

The teacher can view a date-wise attendance sheet containing student IDs, student names, session dates, Present/Absent status, and attendance percentage.

### 9. CSV Export

The attendance sheet can be exported as a CSV file for use in spreadsheet applications such as Microsoft Excel or WPS Office.

### 10. Profile and Password Settings

The settings screen provides profile editing options such as name and department. The registered email address is displayed as a non-editable field. Users can also change their password by providing the current password and a new password.

---

## User Roles

| Role | Main Responsibilities |
|---|---|
| Teacher | Create courses, start and close sessions, display QR codes, view attendance sheets, and export CSV reports |
| Student | Register, log in, browse/enroll in courses, scan QR codes, and view attendance information |

> **Note:** The documented application scope contains Student and Teacher roles. A separate administrator dashboard is not included in the current version described here.

---

## Technology Stack

| Technology | Purpose |
|---|---|
| **Java 21** | Main programming language and runtime environment |
| **JavaFX** | Desktop graphical user interface |
| **FXML** | Declarative layout for JavaFX screens |
| **CSS** | Styling of JavaFX user-interface components |
| **MySQL 8** | Relational database for persistent application data |
| **JDBC** | Communication between Java and MySQL |
| **PreparedStatement** | Parameterized SQL queries |
| **ZXing** | QR-code generation and decoding |
| **webcam-capture (Sarxos)** | Access to built-in or external webcams |
| **Maven** | Dependency and build management |
| **IntelliJ IDEA** | Development environment |

---

## System Architecture

The application follows a layered **Model–DAO–Controller** design with JavaFX views.

```text
+------------------------------------------------------+
|                  JavaFX User Interface               |
|                    FXML + CSS                        |
|                                                      |
| Login | Register | Teacher Dashboard | Student      |
| Dashboard | QR Display | QR Scan | Attendance Sheet |
+----------------------------+-------------------------+
                             |
                             v
+------------------------------------------------------+
|                    Controllers                       |
|                                                      |
| Login | Register | TeacherDashboard | Student       |
| Dashboard | NewCourse | BrowseCourses | QRDisplay   |
| QRScan | AttendanceSheet                              |
+----------------------------+-------------------------+
                             |
                 +-----------+-----------+
                 |                       |
                 v                       v
+---------------------------+  +-----------------------+
|           Model           |  |        Utility        |
|                           |  |                       |
| User                      |  | DBConnection          |
| Course                    |  | QRUtil                |
| ClassSession              |  | PasswordUtil          |
| AttendanceRecord          |  | SceneManager          |
|                           |  | SessionManager        |
+---------------------------+  +-----------------------+
                 |
                 v
+------------------------------------------------------+
|              Data Access Objects (DAO)               |
|                                                      |
| UserDAO | CourseDAO | SessionDAO | AttendanceDAO     |
|             JDBC + PreparedStatement                |
+----------------------------+-------------------------+
                             |
                             v
+------------------------------------------------------+
|                    MySQL 8 Database                  |
|                                                      |
| users | courses | enrollments | class_sessions      |
| attendance                                           |
+------------------------------------------------------+
```

### Architectural Responsibilities

| Layer | Responsibility |
|---|---|
| View | Displays screens and collects user input through FXML and CSS |
| Controller | Handles UI events and coordinates application operations |
| Model | Represents application entities and their data |
| DAO | Encapsulates SQL queries and database operations |
| Utility | Provides reusable services such as QR processing, password utilities, session handling, and screen navigation |
| Database | Stores persistent user, course, session, enrollment, and attendance records |

This separation makes the application easier to understand, maintain, test, and extend.

---

## Application Workflow

The overall attendance process follows these steps:

1. A teacher registers and logs in.
2. The teacher creates a course.
3. A student registers and logs in.
4. The student browses and enrolls in the relevant course.
5. The teacher selects a course and starts a class session.
6. The application creates a session and generates a temporary QR token.
7. The QR code is displayed on the teacher's screen or projector.
8. The QR token is automatically renewed every 25 seconds.
9. The student selects the corresponding course and starts the webcam.
10. The webcam captures frames and ZXing attempts to decode the QR code.
11. The application validates the decoded session identifier and token.
12. If all validation checks succeed, attendance is recorded as `PRESENT`.
13. The teacher can view the attendance sheet and export it as CSV.

### Attendance Workflow Diagram

```text
          +-----------------------+
          | Teacher Login         |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Select / Create Course|
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Start Class Session  |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Generate QR + Token  |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Display QR Code      |
          | Refresh every 25 sec |
          +-----------+-----------+
                      |
                      | Student scans QR
                      v
          +-----------------------+
          | Webcam Capture       |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | ZXing Decode QR      |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Validate Session and |
          | Token                |
          +-----------+-----------+
                      |
                      v
          +-----------------------+
          | Check Course,        |
          | Enrollment, Duplicate|
          +-----------+-----------+
                      |
               +------+------+
               |             |
             Valid         Invalid
               |             |
               v             v
     +----------------+  +----------------+
     | Save PRESENT   |  | Reject Scan /  |
     | in MySQL       |  | Show Feedback  |
     +--------+-------+  +----------------+
              |
              v
     +------------------------+
     | Teacher Views Sheet    |
     | and Exports CSV        |
     +------------------------+
```

---

## Dynamic QR-Code Mechanism

A central feature of the application is the use of a temporary QR token instead of a permanent QR code.

When a teacher starts a class session, the system generates a session identifier and a random token. The QR code represents the session identifier and token in the following conceptual format:

```text
sessionId:token
```

For example, the structure may look like:

```text
125:temporary-random-token
```

The example above is illustrative only; it is not a live attendance credential.

### QR Renewal Process

- The application displays the QR code for the active session.
- A JavaFX `Timeline` tracks elapsed time.
- A progress bar indicates the remaining validity period.
- After 25 seconds, a new token is generated.
- The new token and expiry time are saved in the database.
- The QR image is rendered again with the renewed token.
- The previous token is no longer accepted by the current validation process.

### Why Dynamic QR Codes?

A static QR code can be photographed and shared repeatedly. A short-lived token reduces the usefulness of an old screenshot because it becomes invalid after renewal.

**Important security limitation:** A rotating QR code reduces reuse of old screenshots, but it does not completely prevent a person from relaying a currently valid QR code to someone elsewhere during its validity window. Location, classroom Wi-Fi, or another verification factor would be needed to strengthen this protection.

---

## QR Validation Rules

The student scanning process performs a sequence of checks before attendance is recorded.

| No. | Validation | Purpose |
|---:|---|---|
| 1 | Session exists and is active | Prevents attendance for a missing or closed session |
| 2 | QR token matches the current session token | Rejects an old or incorrect QR code |
| 3 | QR expiry time is valid | Rejects expired tokens |
| 4 | Selected course matches the session course | Prevents attendance in the wrong course |
| 5 | Student is enrolled in the course | Restricts attendance to eligible students |
| 6 | Attendance has not already been recorded | Prevents duplicate attendance |

Only when all required checks succeed does the application insert a `PRESENT` attendance record.

---

## Database Design

The application uses **MySQL 8** to store its persistent data. The documented database design contains the following main tables.

| Table | Purpose |
|---|---|
| `users` | Stores student and teacher account information, role, and password-related data |
| `courses` | Stores course code, course name, and the teacher responsible for the course |
| `enrollments` | Connects students with the courses in which they are enrolled |
| `class_sessions` | Stores course sessions, topics, QR tokens, expiry times, and active status |
| `attendance` | Stores the attendance status of students for individual sessions |

### Main Data Fields

The following field lists describe the documented logical schema. Confirm the actual SQL definitions in the project before making database changes.

#### `users`

```text
id
name
email
password_hash
salt
role
student_id
department
```

#### `courses`

```text
id
code
name
teacher_id
```

#### `enrollments`

```text
student_id
course_id
```

#### `class_sessions`

```text
id
course_id
session_date
topic
qr_token
qr_expires_at
active
created_at
```

#### `attendance`

```text
id
student_id
course_id
session_id
status
```

### Entity Relationships

- One teacher can create multiple courses.
- A student can enroll in multiple courses.
- A course can have multiple enrolled students.
- A course can contain multiple class sessions.
- Each attendance record connects a student with a particular class session.
- A session can have attendance records for multiple enrolled students.

### Database Relationship Overview

```text
USERS (Teacher)
      |
      | one-to-many
      v
   COURSES
      |
      | one-to-many
      v
 CLASS_SESSIONS
      |
      | one-to-many
      v
 ATTENDANCE
      ^
      |
      | student attendance
      |
    USERS (Student)

USERS (Student) ---- ENROLLMENTS ---- COURSES
                         many-to-many
```

---

## Project Structure

The application is organized into model, DAO, controller, utility, database, and JavaFX resource components.

The following is the logical package organization documented for the project. Individual filenames or package paths may differ in the current repository.

```text
Smart-Attendance-System-With-QR-Code/
│
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── attendance/
│       │           │
│       │           ├── model/
│       │           │   ├── User.java
│       │           │   ├── Course.java
│       │           │   ├── ClassSession.java
│       │           │   └── AttendanceRecord.java
│       │           │
│       │           ├── dao/
│       │           │   ├── UserDAO.java
│       │           │   ├── CourseDAO.java
│       │           │   ├── SessionDAO.java
│       │           │   └── AttendanceDAO.java
│       │           │
│       │           ├── controller/
│       │           │   ├── LoginController.java
│       │           │   ├── RegisterController.java
│       │           │   ├── TeacherDashboardController.java
│       │           │   ├── StudentDashboardController.java
│       │           │   ├── NewCourseController.java
│       │           │   ├── BrowseCoursesController.java
│       │           │   ├── QRDisplayController.java
│       │           │   ├── QRScanController.java
│       │           │   └── AttendanceSheetController.java
│       │           │
│       │           ├── util/
│       │           │   ├── PasswordUtil.java
│       │           │   ├── QRUtil.java
│       │           │   ├── SceneManager.java
│       │           │   └── SessionManager.java
│       │           │
│       │           └── db/
│       │               └── DBConnection.java
│       │
│       └── resources/
│           └── com/
│               └── attendance/
│                   ├── fxml/
│                   └── css/
│
├── pom.xml
└── README.md
```

> This tree is an architectural guide, not a verified file listing. Use the actual repository tree as the source of truth when navigating the code.

---

## Prerequisites

Install the following software before running the application.

### 1. Java Development Kit (JDK 21)

Install JDK 21 from a trusted distribution such as Eclipse Temurin (Adoptium) or Oracle JDK.

Verify the installation:

```bash
java -version
```

Also verify the Java compiler:

```bash
javac -version
```

The output should indicate Java 21.

### 2. IntelliJ IDEA

Install IntelliJ IDEA and open the project by selecting its `pom.xml` file or project root directory.

### 3. MySQL 8

Install MySQL Server 8 and a database management tool such as MySQL Workbench. Ensure that the MySQL service is running before launching the application.

### 4. Maven

The project uses Maven for dependency management. If the project includes the Maven Wrapper, use `mvnw` or `mvnw.cmd`. Otherwise, install Maven and verify it:

```bash
mvn -version
```

### 5. Webcam

A built-in or external webcam is required for student-side QR scanning. Allow the operating system to grant camera access to the application.

---

## Installation and Setup

Follow these steps to prepare the development environment.

### Step 1: Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/imran-ict21/Smart-Attendance-System-With-QR-Code.git
```

Move into the project directory:

```bash
cd Smart-Attendance-System-With-QR-Code
```

### Step 2: Open the Project in IntelliJ IDEA

1. Start IntelliJ IDEA.
2. Select **Open**.
3. Choose the cloned project folder.
4. If prompted, select the Maven `pom.xml` file.
5. Allow IntelliJ IDEA to import Maven dependencies.
6. Set the Project SDK to **JDK 21**.
7. Confirm that the project language level is compatible with Java 21.

### Step 3: Start MySQL Server

1. Open MySQL Workbench or your installed MySQL service manager.
2. Connect to the local MySQL server.
3. Confirm that the server is running.
4. Create or select the database used by the application.
5. Prepare the tables according to the project's actual schema.

### Step 4: Configure Database Connectivity

Locate the database connection class, documented as:

```text
com.attendance.db.DBConnection
```

Review the JDBC URL, database name, username, and password. Configure them for the local MySQL installation.

A typical local JDBC URL has this structure:

```text
jdbc:mysql://localhost:3306/DATABASE_NAME
```

Use the actual database name and connection settings required by the project. Do not commit real database passwords or other private credentials to GitHub.

### Step 5: Verify Maven Dependencies

In IntelliJ IDEA:

1. Open the Maven tool window.
2. Select **Reload All Maven Projects**.
3. Wait for dependency downloads to finish.
4. Resolve any dependency or JavaFX configuration errors shown by the IDE.

### Step 6: Prepare the Database

Create the database and tables using the SQL schema supplied with the project, if present. If the repository does not contain a schema file, use the documented database design in this README as a guide and confirm the exact columns, constraints, and relationships from the DAO queries before creating tables.

Do not assume that the illustrative field lists in this README replace the application's actual SQL schema.

---

## Database Configuration

The application uses JDBC to connect Java code to MySQL.

A connection generally follows this pattern:

```java
Connection connection = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/DATABASE_NAME",
    "YOUR_DB_USERNAME",
    "YOUR_DB_PASSWORD"
);
```

The example is illustrative. Use the actual connection class and configuration approach in the repository.

### Database Configuration Checklist

- [ ] MySQL Server is installed.
- [ ] MySQL service is running.
- [ ] The project database exists.
- [ ] Required tables have been created.
- [ ] Database name in the Java configuration is correct.
- [ ] MySQL username is correct.
- [ ] MySQL password is correct.
- [ ] JDBC driver dependency is available through Maven.
- [ ] Database connection succeeds before testing login or attendance.

---

## Running the Application

### Option A: Run from IntelliJ IDEA

1. Open the project in IntelliJ IDEA.
2. Wait until Maven dependency resolution is complete.
3. Locate the JavaFX application entry-point class in the source tree.
4. Confirm that the run configuration uses JDK 21 and the required JavaFX VM/module settings.
5. Run the application's main class.
6. Confirm that the login screen appears.

The exact entry-point class and JavaFX run configuration must be taken from the actual source code and `pom.xml`; they are not assumed in this README.

### Option B: Build with Maven

From the project root:

```bash
mvn clean
mvn compile
```

To create the configured build artifact:

```bash
mvn package
```

The command used to launch the application depends on the JavaFX Maven plugin and main-class configuration in the repository. If the project has a configured JavaFX Maven plugin, use the run goal specified by that configuration.

---

## Main Functional Modules

### Authentication Module

The authentication module manages user registration and login.

Responsibilities:

- Accept registration information.
- Store account details in the database.
- Authenticate users using email and password.
- Identify the user's role.
- Open the appropriate dashboard after successful login.
- Reject invalid credentials.

### Course Management Module

The teacher can create and view courses. Each course is associated with its teacher and has a course code and course name.

### Enrollment Module

Students can browse available courses and enroll in the relevant course. The enrollment relationship is used during QR validation to ensure that only eligible students can record attendance for a course.

### Class Session Module

The teacher starts a class session for a selected course. The session stores information such as the course, date, optional topic, QR token, expiry time, and active status.

The teacher can close the session when the class attendance period is over.

### QR Generation Module

The QR utility uses ZXing to encode session information into a QR image. The generated image is displayed in the JavaFX interface.

### QR Scanning Module

The scanning module accesses the webcam through the webcam-capture library. Frames are captured periodically and decoded through ZXing.

### Attendance Module

The attendance DAO performs the database operations required to check existing records and insert a valid attendance entry.

### Attendance Reporting Module

The reporting module displays date-wise attendance information and calculates student attendance percentages. The teacher can export the report as a CSV file.

### Profile and Settings Module

The settings screen allows users to update supported profile fields and change their password. The email field is displayed as non-editable in the documented interface.

---

## Important Implementation Concepts

### 1. Encapsulation

Application model classes keep data fields private and expose controlled access through getters and setters.

Example:

```java
public class User {
    private int id;
    private String name;
    private String email;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### 2. Abstraction

DAO classes hide SQL and JDBC implementation details from JavaFX controllers. Controllers call meaningful DAO methods instead of directly managing SQL statements.

### 3. Modularity

Different screens and database entities are handled by separate controllers and DAO classes. This keeps responsibilities organized.

### 4. Reusability

Utility classes such as `QRUtil`, `PasswordUtil`, `SceneManager`, and `SessionManager` provide reusable functionality.

### 5. Interfaces

JavaFX controllers may implement `Initializable` to initialize their interface components and screen state.

### 6. Enumeration

An attendance result can be represented using an enum such as:

```java
public enum MarkResult {
    SUCCESS,
    ALREADY_MARKED,
    ERROR
}
```

This provides clear outcomes for attendance operations.

### 7. Exception Handling

JDBC operations, file export, and webcam access can fail. Exception handling and try-with-resources help manage errors and release resources.

### 8. PreparedStatement

Parameterized SQL statements help prevent SQL injection and improve the safety of database operations.

---

## Attendance Percentage

The application presents attendance information as a percentage for each student and course.

The general calculation is:

\[
\text{Attendance Percentage}
=
\frac{\text{Number of Present Sessions}}
{\text{Total Conducted Sessions}}
\times 100
\]

For example, if a student is present in 8 out of 10 conducted sessions:

\[
\frac{8}{10}\times 100 = 80\%
\]

The actual application should use its stored attendance records and the course's conducted sessions when calculating the percentage.

---

## CSV Export

Teachers can export the attendance sheet into CSV format.

A typical attendance report contains:

- Student ID
- Student Name
- Session dates
- Attendance status for each session (`P` or `A`)
- Attendance percentage

CSV files can be opened using spreadsheet applications such as Microsoft Excel, WPS Office, and LibreOffice Calc.

The CSV export feature helps teachers preserve records, review attendance, and prepare course-end reports.

---

## Security Considerations

The project includes several security-oriented design choices:

- Role-based access for students and teachers.
- Salted password hashing as documented in the project specification.
- JDBC `PreparedStatement` for parameterized database queries.
- Temporary QR tokens with expiry times.
- Session-active and course-enrollment validation.
- Duplicate attendance checks.
- Database-side expiry calculation in the documented session update approach.

### Important Password-Storage Note

The project specification describes salted SHA-256 hashing. A unique salt is useful, but **plain SHA-256 is not a password-specific key-derivation algorithm** and is not recommended for production password storage. A production deployment should use a password-hashing algorithm such as Argon2id, bcrypt, or PBKDF2 with appropriate parameters.

### Additional Security Recommendations

- Store database credentials outside source code.
- Do not upload `.env`, private configuration files, passwords, or real user data.
- Use least-privilege database accounts.
- Enforce unique constraints for attendance per student and session at the database level.
- Validate all user input.
- Consider HTTPS and authenticated APIs if a web/mobile version is developed.
- Add classroom Wi-Fi or location verification if stronger anti-relay protection is required.

---

## Testing and Verification

The following test scenarios describe the important behaviours that should be verified during project evaluation.

| No. | Test Scenario | Expected Behaviour |
|---:|---|---|
| 1 | Register with a new email | A new account is created |
| 2 | Register with an existing email | Duplicate registration is rejected |
| 3 | Log in with valid credentials | The correct role dashboard opens |
| 4 | Log in with invalid credentials | Login is rejected |
| 5 | Teacher creates a course | The course appears in the teacher dashboard |
| 6 | Student enrolls in a course | The enrollment is stored |
| 7 | Teacher starts a class session | An active session and QR code are created |
| 8 | QR token reaches its 25-second renewal point | A new token and QR code are displayed |
| 9 | Student scans the current valid QR | Attendance is recorded if all checks pass |
| 10 | Student scans the same session QR again | Duplicate attendance is rejected |
| 11 | Student scans an expired QR | The scan is rejected |
| 12 | Student selects a different course | A course mismatch is rejected |
| 13 | A non-enrolled student scans the QR | Attendance is rejected |
| 14 | Student scans after the session is closed | Attendance is rejected |
| 15 | Teacher opens the attendance sheet | Date-wise attendance information is displayed |
| 16 | Teacher exports the attendance sheet | A CSV file is generated |
| 17 | User updates profile settings | Supported profile information is saved |
| 18 | User changes password | Password is changed after the required validation |

> **Testing record:** These are recommended verification cases, not a claim that every case has been independently re-tested for this README. Record the actual outcome (`Pass`, `Fail`, or `Not Tested`) during your final demonstration and evaluation.

---

## Observed Application Screens

The project screenshots supplied during documentation show the following application interfaces and outputs:

1. **Login Screen** — email and password fields with a registration link.
2. **Settings Screen** — profile information, non-editable email field, and change-password section.
3. **Teacher Dashboard** — course list, new-course option, topic field, session-start action, attendance-sheet view, and CSV export.
4. **QR Display Screen** — course/session heading, QR image, 25-second refresh information, progress indicator, and close-session action.
5. **Student QR Scanning Screen** — course selection, start-camera control, webcam preview, and scanning status.
6. **Attendance Sheet** — student IDs, student names, date-wise `P`/`A` values, and percentage.
7. **CSV Output** — exported attendance information opened in a spreadsheet application.

The screenshots demonstrate the user-interface flow and the attendance-reporting features of the running application.

---

## Limitations

The current project version has the following limitations:

- It is a desktop application rather than a web or mobile application.
- Student scanning requires a working webcam.
- QR scanning performance depends on lighting, camera quality, and QR display clarity.
- A valid QR code may still be relayed to an absent student during its short validity period.
- There is no documented GPS or classroom Wi-Fi verification in the current version.
- A separate multi-department administrator panel is outside the documented scope.
- Production deployment would require stronger password hashing, credential management, and additional security controls.
- The application depends on a running MySQL service and correct database configuration.

---

## Future Enhancements

The system can be extended in several ways:

1. **Mobile Application:** Develop an Android/iOS application so students can scan QR codes using their phones.
2. **Web-Based Version:** Provide browser access for teachers and students.
3. **Cloud Deployment:** Host the application services and database in a secure cloud environment.
4. **Geo-Fencing:** Verify that students are within the classroom or a permitted location.
5. **Wi-Fi/Bluetooth Verification:** Add classroom network or beacon-based checks.
6. **Face Verification:** Introduce an optional second verification factor, subject to privacy and consent requirements.
7. **Administrator Panel:** Manage departments, teachers, students, and courses centrally.
8. **Advanced Reports:** Generate PDF reports, charts, and semester-wise analytics.
9. **Low-Attendance Alerts:** Notify students when their attendance percentage falls below a defined threshold.
10. **Improved Password Security:** Migrate to Argon2id or bcrypt.
11. **Automated Testing:** Add unit, integration, and UI tests.
12. **University System Integration:** Integrate with an official student information system if authorized.

---

## Troubleshooting

### 1. `java` or `javac` Is Not Recognized

**Possible cause:** JDK is not installed or the PATH environment variable is not configured.

**Solution:**
- Install JDK 21.
- Configure `JAVA_HOME`.
- Add the JDK `bin` directory to PATH.
- Restart the terminal and run `java -version`.

### 2. Maven Dependencies Are Not Downloading

**Possible cause:** Internet connectivity, Maven configuration, or dependency-resolution problems.

**Solution:**
- Check the internet connection.
- Reload Maven projects in IntelliJ IDEA.
- Confirm that `pom.xml` contains the required dependencies.
- Run:

```bash
mvn -U clean compile
```

### 3. MySQL Connection Failed

**Possible cause:** MySQL service is stopped, credentials are incorrect, or the JDBC URL is wrong.

**Solution:**
- Start MySQL Server.
- Verify the host and port.
- Check the database name.
- Verify username and password.
- Confirm that the MySQL JDBC driver dependency is available.

### 4. JavaFX Runtime Components Are Missing

**Possible cause:** JavaFX dependencies or VM/module configuration are incomplete.

**Solution:**
- Confirm the JavaFX dependencies in `pom.xml`.
- Reload Maven.
- Verify that the JavaFX version is compatible with the project setup.
- Use the run configuration or Maven plugin configured by the project.

### 5. Webcam Is Not Starting

**Possible cause:** Camera permission is disabled, another application is using the camera, or no camera is detected.

**Solution:**
- Close other applications using the webcam.
- Enable camera access in the operating system's privacy settings.
- Reconnect an external webcam if used.
- Restart the application and try again.

### 6. QR Code Is Not Being Detected

**Possible cause:** Poor lighting, low camera resolution, reflection, or a QR code that is too small.

**Solution:**
- Increase screen brightness.
- Keep the QR code fully visible in the camera frame.
- Adjust the camera distance.
- Avoid reflections and motion blur.
- Ensure that the QR code is still valid.

### 7. Login or Registration Does Not Work

**Possible cause:** Database connection failure, missing tables, duplicate email, or incorrect credentials.

**Solution:**
- Confirm the MySQL connection.
- Check that the required tables exist.
- Review application logs and DAO queries.
- Verify the entered email and password.

---

## Learning Outcomes

Through this project, the team gained practical experience in:

- Applying object-oriented programming principles in Java.
- Developing desktop interfaces using JavaFX, FXML, and CSS.
- Connecting Java applications with MySQL through JDBC.
- Designing relational database entities and relationships.
- Using PreparedStatement for parameterized database operations.
- Generating and decoding QR codes with ZXing.
- Accessing webcam frames through a Java library.
- Implementing time-limited QR tokens and validation logic.
- Organizing code using Model, DAO, Controller, and Utility layers.
- Handling exceptions and managing application resources.
- Generating attendance reports and exporting CSV files.
- Collaborating on a software project and documenting its design.

---

## Contributors

This project was collaboratively developed by the following students of the Department of Information and Communication Technology, Mawlana Bhashani Science and Technology University.

### Imran Hossen

- **Student ID:** IT 24063
- **Department:** Information and Communication Technology (ICT)
- **University:** Mawlana Bhashani Science and Technology University (MBSTU)
- **GitHub:** [imran-ict21](https://github.com/imran-ict21)

### Md. Jahidul Islam

- **Student ID:** IT 24018
- **Department:** Information and Communication Technology (ICT)
- **University:** Mawlana Bhashani Science and Technology University (MBSTU)

---

## Supervisor

**Dr. Md. Abir Hossain**  
Professor  
Department of Information and Communication Technology (ICT)  
Mawlana Bhashani Science and Technology University (MBSTU)

---

## Acknowledgement

We express our sincere gratitude to our project supervisor, **Dr. Md. Abir Hossain, Professor, Department of Information and Communication Technology, Mawlana Bhashani Science and Technology University**, for his academic guidance and support throughout the development of this project.

We also acknowledge the Department of Information and Communication Technology, MBSTU, for providing the academic environment in which we could apply the concepts learned in Object Oriented Programming and Design with Java.

Finally, we thank everyone who contributed through suggestions, feedback, and support during the planning, implementation, and evaluation of the project.

---

## References

1. ZXing Project, “ZXing (Zebra Crossing) barcode scanning library for Java.” [Online]. Available: https://github.com/zxing/zxing
2. OpenJFX, “JavaFX — Open Source Application Platform.” [Online]. Available: https://openjfx.io
3. Oracle Corporation, “MySQL 8.0 Reference Manual.” [Online]. Available: https://dev.mysql.com/doc/refman/8.0/en/
4. S. Sarxos, “webcam-capture: Java library to use built-in or external webcams.” [Online]. Available: https://github.com/sarxos/webcam-capture
5. Apache Software Foundation, “Apache Maven Project.” [Online]. Available: https://maven.apache.org
6. OpenJDK, “JDK 21 Documentation.” [Online]. Available: https://docs.oracle.com/en/java/javase/21/
7. GitHub Repository, “Smart Attendance System with QR Code.” [Online]. Available: https://github.com/imran-ict21/Smart-Attendance-System-With-QR-Code

---

## License

No explicit open-source license has been specified in this repository documentation. Unless a license file is added to the repository, all rights remain with the copyright holder(s), and reuse or redistribution should not be assumed to be permitted.

---

<p align="center">
  <strong>Smart Attendance System with QR Code</strong><br>
  Project-II (ICT-2200)<br>
  Department of Information and Communication Technology<br>
  Mawlana Bhashani Science and Technology University (MBSTU)
</p>
