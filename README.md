## Maven project with integration of Spring and Hibernate 
malliiiiiiiiibbbbhhbchwwb;;sjd;sd
iiiiiiiibbbbhhbchwwb;;sjd;sd
>>>>>>> ce2802bf270562280768a572efdb3d22c33452a2
iiiiihhhyyyyyy
Goal: The purpose of this project is to test CI-CD Pipeline setup with Jenkins Automation Server.

### Database Info 
- `src/main/resources/application.properties` 

### Steps for building/running this project

Be in the directory docker-jenkins
- `Create a database with name : websystique`
- `Database connectivity config is in : src/main/resources/application.properties`

#### Steps for creating a Schema

`CREATE TABLE EMPLOYEE(
    id INT NOT NULL auto_increment, 
    name VARCHAR(50) NOT NULL,
    joining_date DATE NOT NULL,
    salary DOUBLE NOT NULL,
    ssn VARCHAR(30) NOT NULL UNIQUE,
    PRIMARY KEY (id)
);`
