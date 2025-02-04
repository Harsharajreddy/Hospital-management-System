# Hospital Management System (Java & MySQL)

## Overview
The **Hospital Management System** is a command-line application designed to manage patients, doctors, and appointments using Java and MySQL. It demonstrates basic CRUD operations, database connectivity, and interaction between Java and MySQL. This project serves as a learning tool for understanding the integration of Java with MySQL.

## Features
- Add Patients: Allows adding patient details to the database.
- View Patients: Displays a list of all patients stored in the database.
- View Doctors: Displays a list of all doctors stored in the database.
- Book Appointments: Enables booking an appointment between a patient and a doctor, ensuring the doctor's availability on the specified date.
- Exit: Closes the application and database connection safely.

## Technologies Used
- Programming Language: Java
- Database: MySQL
- IDE: Visual Studio Code (VS Code)
- JDBC Driver: MySQL Connector/J

## Prerequisites
- Java Development Kit (JDK): Ensure JDK is installed and configured.
- MySQL Server: Installed and running with access to MySQL Workbench or Shell.
- MySQL JDBC Driver: Add the MySQL Connector/J .jar file to your project.
- Database Setup: Create the required database and tables.

## Database Setup
Create a Database:
```sql
CREATE DATABASE hospital;
```
Use the Database:
```sql
USE hospital;
```
Create Tables:

### Patients Table:
```sql
CREATE TABLE patients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(10) NOT NULL
);
```

### Doctors Table:
```sql
CREATE TABLE doctors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    specialty VARCHAR(100) NOT NULL
);
```

### Appointments Table:
```sql
CREATE TABLE appointments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT NOT NULL,
    doctor_id INT NOT NULL,
    appointment_date DATE NOT NULL,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);
```

## How to Run
1. Clone or Download the Project.
2. Add MySQL Connector/J:
   - Place the .jar file in a `lib` folder in your project directory.
   - Add the .jar file to the project classpath.
3. Update Database Credentials:
   Modify the following fields in the `HospitalManagementSystem` class:
   ```java
   private static final String url = "jdbc:mysql://localhost:3306/hospital";
   private static final String username = "your_mysql_username";
   private static final String password = "your_mysql_password";
   ```
4. Compile and Run:
   ```sh
   javac -cp ".;lib/mysql-connector-j-9.1.0.jar" src/*.java
   java -cp ".;lib/mysql-connector-j-9.1.0.jar;src" HospitalManagement
   ```

## Usage Instructions
- Upon running the program, you'll see the Hospital Management System menu.
- Choose an option by entering the corresponding number:
  - To **Add a Patient**, provide the patient's name, age, and gender.
  - To **View Patients**, all patients in the database will be displayed.
  - To **View Doctors**, all doctors in the database will be displayed.
  - To **Book an Appointment**, enter the patient ID, doctor ID, and appointment date. The program will check the doctor's availability.
  - To **Exit**, choose the exit option to close the application and the database connection.

## Learning Objectives
- **JDBC Connection**: Understand how to connect Java with MySQL using JDBC.
- **CRUD Operations**: Learn to perform basic CRUD operations on a database.
- **Prepared Statements**: Avoid SQL injection and handle dynamic queries securely.
- **Modular Programming**: Separate concerns using different classes for patients, doctors, and main operations.

## Limitations
- Basic validation is implemented; further checks can be added.
- No GUI; this is a console-based application.

## Future Enhancements
- Add more features like patient and doctor search, updating records, and deleting records.
- Introduce a graphical user interface (GUI) for better user interaction.
- Implement advanced appointment scheduling features.

## Acknowledgments
This project was inspired by the YouTube tutorial:
**Java Project 🚀 - Hospital 🏥 Management System | Java Project For Beginners 🔥🔥**
by Indial Programmer.

While the video provided foundational concepts, I have made significant customizations and enhancements to suit my learning objectives and extend its functionality.

## Author
This project was developed as a learning exercise to understand Java and MySQL integration.

## License
This project is open-source and available for modification and distribution under the MIT License.

