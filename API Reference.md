## Overview

Bellbloom is a school management system with built-in authentication. It is used to handle academic data conveniently for both teachers and students.  

## Getting Started

### Authentication

1. To get started, navigate to the Login endpoint and select signup:

![][image1]

2. A dropdown menu will appear showing you the request body and the required JSON fields. Valid role values:  
   1. professor  
   2. student  
3. Click “Try it out”, edit the body, then execute the command.  
4. Navigate to the Login endpoint and input your email and password.

![][image2]

5. You will see Response 200 along with an assigned JSON Web token.  
6. Copy and paste your JSON Web token into the Authorize section at the top of the page.  
   ![][image3]  
   ![][image4]  
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

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAL8AAABTCAYAAADObNb/AAAEa0lEQVR4Xu3dT2sdVRiA8X4KTZMgjaatYCmpxXQRLFQhUrDhglij4DK4EEEDStBlTaUFKRWtCF22dFvFjYsuBUGRfqPjnJOZM2fedyZ3kntmvOF9Fr9F5s+ZuckzM+duJqcWFpccYNEpuQCwgvhhFvHDLOKHWcQPs4gfZhE/zCJ+mEX8MIv4YRbxwyzih1nED7OIH2YRP8wifphF/DCL+GEW8cMs4odZxA+ziB9mET/MGjX+pUuvupWdd9y5/Y/cudvADIqGfEu+KdlZX6PF708yRr//of4wwFFUDRVNHfcCGC3+cMcvTvbMx2+5heVltR44kqIh35Jvyrel1vcwTvynFw/u+sXVSvjIpmgpPAGKtnxjav0Uo8T/oo+/fFzJdcAsqq58Y3LdNMSPE434YRbxwyzix/9i9c3L7vrjb9x7f/4QXH/0tVvdeF1tNyTix+hW1i+6m/88cNvPf2l4/68f3ZlLr6nth0L8GN217z8NsV+7/5lbeeNiuBje/unzsOzqd5+o7YdC/Bjd5I87IfSXLpyPy1YuXwjLtn7fV9sPhfgxug/+/TmE3li+tByW3fz7gdp+KMTfYvXe3TgP3dzV63vZ3XPbT7biz2tPZhyvy2THTfy5Pttxq3LdnKp+t32XD4X4lStu41nyRSwJuDcfvth3sPhPoK7Iu5YPhfilGO6e2wx/jD231thmSy8v95ncu1LvHx1sV8efXlxybHHhifXVE2lSnFu42z+/6za+at7506dWKl501ZOiFM65cQ7D2Hz4pTqnaa7eGfbLL/EL6R26/W49W/xKfDrI8CtF4JOD46iwffBi2qO2KYXPIMJvrGv5XeQkj9mH/24gx8mJ+BtE2C3TF7VNsl28i7bsF+Ovlsm5erVPMnePIZf7xJ/T+b0cJxGPKS6MOvbys7Tsm5sMuy85Tk7En1LRtoTetuwI8XeFp9frbeK0J52qdMRfP2nq8+x8+qjpV376mP3IcXIi/kR3HGlwOn4V5THi13fl7m2mxV9Pfeop0+Gfr7ndEPQx+5Hj5ET8lY75cBTjquKvgqnn6rPEf5Rpz6HxJ9855Fy+/QIbh/p99iTHyYn4SzK0Wnfskoo/2W9q/J3j6i+8h8XfdXcP+3Rd4Ooz56eO2ZMcJyfiD+rw2u6KVVAxukZExfRHzvkbIfeNX+5Xjp2cx8zxq3OXxx+OPJ++5Dg5ET9GIaPuS46TE/FjFDd++1aFPc27T2+pcXIifoxi6ewrbn1329349ZaKXPLbrH+x7ZbPvqzGyYn4YRbxwyzih1nED7NORvy8rhC5Ja8rnOv4eVEtshIvqp3b+P1LRBfXeEU5MkpeUe7bmtsX1Xr+yvQnyT+nQBblP6fwTR3nru+NFr/nT9J7YeE0MLOqJ9lZX6PGH5QnDMzqOFOd1PjxA3OC+GEW8cMs4odZxA+ziB9mET/MIn6YRfwwi/hhFvHDLOKHWcQPs4gfZhE/zCJ+mEX8MIv4YRbxwyzih1nED7OIH2YRP8z6D1mWG9eHFRwWAAAAAElFTkSuQmCC>

[image4]: <data:image/png;base64,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>