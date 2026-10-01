## Overview

Bellbloom is a school management system with built-in authentication. It is used to handle academic data conveniently for both teachers and students.  

## Getting Started

### Authentication

1. To get started, navigate to the Login endpoint and select signup:

![Bellbloom screenshot](EX%20bellbloom/EX_1.png)

2. A dropdown menu will appear showing you the request body and the required JSON fields. Valid role values:  
   1. professor  
   2. student  
3. Click “Try it out”, edit the body, then execute the command.  
4. Navigate to the Login endpoint and input your email and password.

![Bellbloom screenshot](EX%20bellbloom/EX_2.png)

5. You will see Response 200 along with an assigned JSON Web token.  
6. Copy and paste your JSON Web token into the Authorize section at the top of the page.  
![Bellbloom screenshot](EX%20bellbloom/EX_3.png)
![Bellbloom screenshot](EX%20bellbloom/EX_4.png)
7. Congratulations\! You are now logged in.

JWT Tokens are valid for 60 minutes. After that, requests return 401 and you must login again to receive a new one. 

### Endpoint Reference

#### Login

##### POST

###### */api/Login/signup*

Description: Create a user account.

##### Request body

| Value | Type |
| :---- | :---- |
| firstName | string |
| lastName | string |
| username | string |
| password | string |
| phoneNumber | string |
| email | string |
| role | string |

###### */api/Login/login*

Description: Login to user account.

##### Request body

| Value | Type |
| :---- | :---- |
| email | string |
| password | string |

#### Attendance 

##### GET

###### */get-attendance-records*

Description: Get attendance records for students.

###### */get-attendance-by-student*

Description: Get attendance records by student ID.

###### */get-attendance-by-course*

Description: Get student attendance records by course.	

##### POST

###### */add-attendance*

Description: Add a student’s attendance.

##### Request body

| Value | Type |
| :---- | :---- |
| studentId | string |
| courseId | string |
| date | string(\$date-time) |
| isPresent | bool |

##### PUT

###### */update-attendance*

Description: Update a student’s attendance. 

##### Request body

| Value | Type |
| :---- | :---- |
| isPresent | bool |

#### Fees

##### GET

###### */get-Student-Fees*

Description: Retrieve the accrued fees of a specified student.

##### POST

###### */add-course-fee*

Description: Determine the cost of a specified course.

###### */assign-student-fee*

Description: Assign a fee to a specified student.

##### Request body

| Value | Type |
| :---- | :---- |
| feeAmount | int |
| studentLevel | int |

##### PUT

###### */update-student-fee*

Description: Update a student’s fees.

##### Request body

| Value | Type |
| :---- | :---- |
| studentId | string |
| studentLevel | int |
| feeAmount | int |
| amountPaid | int |

#### Grades

##### GET

###### */api/Grades/get-gpa*

Description: Retrieve a specified student’s GPA

###### */api/Grades/get-list-of-a-students-grades*

Description: Retrieve a list of all grades for a specified student.

###### */api/Grades/get-student-grade-in-1-course*

Description: Retrieve a specified student’s grade in a specified course.

##### POST

###### */api/Grades/assign-grade*

Description: Assign a grade to a specified student in a specified course.

##### Request body

| Value | Type |
| :---- | :---- |
| studentId | string |
| courseId | string |
| score | int |

##### PUT

###### */api/Grades/update-a-grade*

Description: Update a specified student’s grade in a specified course.

##### DELETE

###### */api/Grades/delete-a-grade*

Description: Delete a grade for a specified student in a specified course.

#### Scheduling

##### GET

###### */api/Scheduling/retrieve-schedules*

Description: Retrieve schedules for a specified date.

##### POST

###### */api/Scheduling/create-schedule*

Description: Schedule a new class with specified start, end time, preferred classroom, and course ID.

##### Request body

| Value | Type |
| :---- | :---- |
| classroomId | string |
| courseId | string |
| startTime | string(\$date-time) |
| endTime | string(\$date-time) |

##### PUT

###### */api/Scheduling/update-schedules*

Description: Update a class schedule.

##### Request body

| Value | Type |
| :---- | :---- |
| classroomId | string |
| courseId | string |
| startTime | string(\$date-time) |
| endTime | string(\$date-time) |

##### DELETE

###### */api/Scheduling/delete-schedules*

Description: Delete a specific class from the schedule.

#### Student Management

##### GET

###### */api/StudentManagement/display-student*

Description: Retrieve a list of all students and their information.

###### */api/StudentManagement/display-student-by-id*

Description: Retrieve a specified student’s information by ID.

##### POST

###### */api/StudentManagement/create-student*

Description: Insert a student into the school roster.

##### Request body

| Value | Type |
| :---- | :---- |
| userId | string |
| graduationDate | string(\$date-time) |
| enrollDate | string(\$date-time) |
| completedCredits | int |
| studentLevel | int |

###### */api/StudentManagement/enroll-student-in-course*

Description: Enroll a student into a specific course.

##### PUT

###### */api/StudentManagement/update-student*

Description: Update a specified student’s information.

##### Request body

| Value | Type |
| :---- | :---- |
| enrollDate | string(\$date-time) |
| graduationDate | string(\$date-time) |
| completedCredits | int |
| enrolledCourses | string\[\] |
| studentLevel | int |

###### */api/StudentManagement/assign-advisor*

Description: Assign an advisor to a specific student.

##### DELETE

###### */api/StudentManagement/delete-student*

Description: Delete a student from the school roster

###### */api/StudentManagement/drop-student-from-course*

Description: Drop a student from a specific course.

#### Professor Management

##### GET

###### */api/ProfessorManagement/display-professor*

Description: Retrieve a list of all professors and their information.

###### */api/ProfessorManagement/display-professor-by-id*

Description: Retrieve a specific professor’s information by ID.

##### POST

###### */api/ProfessorManagement/create-professor*

Description: Insert a professor into the school roster.

##### Request body

| Value | Type |
| :---- | :---- |
| userId | string |
| taughtCourses | string\[\] |
| department | string |
| employmentDate | string(\$date-time) |

##### PUT

###### */api/ProfessorManagement/update-professor*

Description: Update a specified professor’s information.

##### Request body

| Value | Type |
| :---- | :---- |
| taughtCourses | string\[\] |
| department | string |
| employmentDate | string(\$date-time) |

##### DELETE

###### */api/ProfessorManagement/delete-professor*

Description: Delete a professor from the school roster

#### Errors

##### CODE

###### *200 \- OK*

###### *204 \- Information not found*

###### *400 \- Bad request*

###### *401 \- Missing or invalid authorization*

###### *403 \- Role not allowed*

###### *404 \- Not found*

###### *500 \- Server Error*

###### 
