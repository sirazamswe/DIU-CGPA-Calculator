🎓 Java Grade Management SystemA robust, console-based Java application designed to calculate, classify, and persistently store student Cumulative Grade Point Averages (CGPA). Built with clear, straightforward logic, this project features strict input validation, real-time calculation, and file-handling capabilities.🔄 System FlowchartThe following diagram illustrates the execution flow of the application, from user input validation to file generation and the restart loop.flowchart TD
    Start([Start Program]) --> UserInfo[/Enter Student Info:\nName, ID, Semester/]
    UserInfo --> ValidateInfo{Valid/NotEmpty?}
    ValidateInfo -- No --> UserInfo
    ValidateInfo -- Yes --> NumCourses[/Enter Number of Courses/]
    
    NumCourses --> ValidateNum{Valid Number > 0?}
    ValidateNum -- No --> NumCourses
    ValidateNum -- Yes --> CourseLoop((Course\nLoop))
    
    CourseLoop --> CourseInfo[/Enter Course Name,\nCredit 1-4, Grade/]
    CourseInfo --> ValidateCourse{Valid Inputs?}
    ValidateCourse -- No --> CourseInfo
    ValidateCourse -- Yes --> StoreCourse[Store in Course Array]
    
    StoreCourse --> CheckLoop{All Courses\nEntered?}
    CheckLoop -- No --> CourseLoop
    CheckLoop -- Yes --> Calc[Calculate Total GP,\nCredits, & CGPA]
    
    Calc --> Classify[Determine Classification\nOutstanding/Excellent/etc.]
    Classify --> Print[Print Transcript\nto Console]
    Print --> SaveFile[(Append to\nresult.txt)]
    
    SaveFile --> PromptRestart{Calculate Again?\n(Y/N)}
    PromptRestart -- Yes --> UserInfo
    PromptRestart -- No --> End([End Program])
    
    style Start fill:#4CAF50,stroke:#388E3C,color:white
    style End fill:#f44336,stroke:#d32f2f,color:white
    style SaveFile fill:#2196F3,stroke:#1976D2,color:white
🚀 FeaturesInteractive Command-Line Interface (CLI): Seamlessly prompts users for student details and course specifics.Strict Input Validation: * Prevents empty inputs for names, IDs, and semesters.Validates numeric inputs to prevent crash-inducing formatting errors.Restricts course credits to a valid range of 1.0 to 4.0.Enforces a strict set of accepted letter grades.Automated CGPA Calculation: Computes the total grade points based on course credits and the corresponding letter grade weight.Performance Classification: Automatically categorizes the final CGPA into distinct performance brackets.Persistent Storage: Automatically generates and appends to a result.txt file. Each saved record includes a generated timestamp.Continuous Execution Loop: Allows users to calculate grades for multiple students in a single session.📋 Grading Scale & ClassificationThe system uses a standard 4.0 scale to convert letter grades into grade points:Letter GradeGrade PointCGPA RangeClassificationA+4.003.75 - 4.00OutstandingA3.753.50 - 3.74ExcellentA-3.503.00 - 3.49GoodB+3.252.00 - 2.99PassB3.00Below 2.00FailB-2.75C+2.50C2.25D2.00F0.00⚙️ Prerequisites & InstallationTo compile and run this application, you need the Java Development Kit (JDK) installed on your system (Java 8 or higher is required for the java.time API).Compile the Code:Open your terminal, navigate to the folder containing GradeManagementSystem.java, and run:javac GradeManagementSystem.java
Run the Application:Execute the compiled Java program by running:java GradeManagementSystem
📄 Example Output (result.txt)When you complete a calculation, the system generates a formatted transcript and appends it to result.txt:Student: Monira
ID: 242-35-637
Semester: 5
Date: 2026-04-05 12:13:20
---------------------------------------------
OOP             3.0      B        3.00      
OOP Lab         1.0      A        3.75      
Algo            3.0      A+       4.00      
---------------------------------------------
Final CGPA = 3.54
Classification: Excellent
🏗️ Project StructureCourse.java / Course Class: A data structure holding individual course attributes (name, credit, grade) and a getGradePoint() method for scale conversion.GradeManagementSystem.java: The main driver class. It handles standard I/O via Scanner, input validation loops, calculation logic, and file writing using FileWriter.
