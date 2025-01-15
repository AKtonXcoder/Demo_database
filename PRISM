CREATE DATABASE PRISM;
USE PRISM;

-- Create  PanID table
CREATE TABLE PanID (
    PanID INT PRIMARY KEY AUTO_INCREMENT,
    PanNumber VARCHAR(20) UNIQUE NOT NULL,
    IssuedDate VARCHAR(20),
    IsActive BOOLEAN DEFAULT TRUE
);

-- Create  Address table
CREATE TABLE Address (
    AddressID INT PRIMARY KEY AUTO_INCREMENT,
    StreetAddress VARCHAR(100),
    City VARCHAR(50),
    State VARCHAR(50),
    ZipCode VARCHAR(10),
    IsActive BOOLEAN DEFAULT TRUE
);

-- Create  Employee table
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50),
    DOB VARCHAR(20),
    Gender ENUM('Male', 'Female', 'Other'),
    PanID INT,
    CurrentAddressID INT,
    PermanentAddressID INT,
    IsActive BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (PanID) REFERENCES PanID(PanID),
    FOREIGN KEY (CurrentAddressID) REFERENCES Address(AddressID),
    FOREIGN KEY (PermanentAddressID) REFERENCES Address(AddressID)
);

-- Create  Hobbies table
CREATE TABLE Hobbies (
    HobbyID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    HobbyName VARCHAR(100),
    IsActive BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID)
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY AUTO_INCREMENT,
    CourseName VARCHAR(100),
    DurationMonths INT,
    EmployeeID INT,
    IsActive BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID)
);

-- Create  Education table
CREATE TABLE Education (
    EducationID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    Degree VARCHAR(100),
    InstitutionName VARCHAR(100),
    YearOfPassing YEAR,
    IsActive BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID)
);

-- Insert  data into the PanID table
INSERT INTO PanID (PanNumber, IssuedDate) VALUES
('INDPN12345A', '01-15-2015'),
('INDPN23456B', '12-06-2018'),
('INDPN34567C', '14-11-2008'),
('INDPN45678D', '16-03-2020'),
('INDPN56789E', '18-07-2018');

-- Insert data into the Address table
INSERT INTO Address (StreetAddress, City, State, ZipCode) VALUES
('Satna ', 'Satna', 'M.P', '560001'),
('CTI ', 'Singrauli', 'M.P', '400001'),
('Sajanpur', 'Satna', 'M.P', '600002'),
('Gole ka mandir', 'Gurgaon', 'Haryana', '700064'),
('City center', 'Kota', 'Rajasthan', '122002');

-- Insert  data into the Employee table
INSERT INTO Employee (FirstName, LastName, DOB, Gender, PanID, CurrentAddressID, PermanentAddressID) VALUES
('Ajit', 'Tiwari', '05-10-1998', 'Male', 1, 1, 2),
('Anil', 'Verma', '29-03-2000', 'male', 2, 2, 3),
('Sunil', 'Sir', '11-05-1990', 'Male', 3, 3, 4),
('Ruchi', 'Maravi', '20-08-2002', 'Female', 4, 4, 5),
('Rohit', 'Meena', '19-03-2000', 'Male', 5, 5, 1);

-- Insert  data into the Hobbies table
INSERT INTO Hobbies (EmployeeID, HobbyName) VALUES
(1, 'Cricket'),
(2, 'Football'),
(3, 'Reading'),
(3, 'Photography'),
(4, 'Painting'),
(2, 'Traveling');

-- Insert  data into the Courses table
INSERT INTO Courses (CourseName, DurationMonths, EmployeeID) VALUES
('Cybersecurity', 6, 1),
('Full Stack Development and Data Analytics', 8, 2),
('Cybersecurity', 6, 3),
('Machine Learning ', 8, 4),
('AutocadDesign', 6, 5);

-- Insert data into the Education table
INSERT INTO Education (EmployeeID, Degree, InstitutionName, YearOfPassing) VALUES
(1, 'B.Tech in Computer Science', 'IIT Delhi', 2012),
(2, 'B.Tech in Data Science', 'MITS', 2025),
(3, 'M.Sc in Information Technology', 'DTU Delhi', 2018),
(4, 'B.E in Mechanical Engineering', 'BHU', 2024),
(5, 'B.Tech in Civil Engineering', 'IIT Guwahati', 2023);


-- Query to check database
-- select all employees who are IITians 
-- we can write an SQL query that selects employees whose education records indicate they attended an institution with "IIT" 
SELECT 
    e.EmployeeID,
    e.FirstName,
    e.LastName,
    ed.InstitutionName,
    ed.Degree
FROM 
    Employee e
INNER JOIN 
    Education ed
ON 
    e.EmployeeID = ed.EmployeeID  -- Foreign Key relationship
WHERE 
    ed.InstitutionName LIKE '%IIT%'; -- LIKE use to retrieves all records for institutions containing "IIT" 
