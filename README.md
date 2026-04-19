<div align="center"><h1>🎓 Java Grade Management System</h1><p><b>A robust, console-based Java application designed to calculate, classify, and persistently store student Cumulative Grade Point Averages (CGPA).</b></p><!-- Badges --></div>📖 Table of ContentsAbout the ProjectSystem ArchitectureKey FeaturesGrading Scale & ClassificationGetting StartedUsage ExampleProject StructureContributing🔎 About the ProjectThe Java Grade Management System is built with clear, straightforward logic, making it an excellent tool for academic tracking and an ideal reference for Object-Oriented Programming (OOP) concepts. It features strict input validation, real-time calculations, and persistent file-handling capabilities to maintain reliable academic records.🔄 System ArchitectureThe following flowchart illustrates the application's execution flow, highlighting the validation loops and file generation process.flowchart TD
    Start([Start Program]) --> UserInfo[/Enter Student Info:\nName, ID, Semester/]
    UserInfo --> ValidateInfo{Valid/NotEmpty?}
    ValidateInfo -- No --> UserInfo
    ValidateInfo -- Yes --> NumCourses[/Enter Number of Courses/]
    
    NumCourses --> ValidateNum{Valid Number > 0?}
    ValidateNum -- No --> NumCourses
    ValidateNum -- Yes --> CourseLoop((Course\nLoop))
    
    CourseLoop --> CourseInfo[/Enter Course Name,\nCredit 1.0-4.0, Grade/]
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
✨ Key FeaturesInteractive CLI: A seamless and guided command-line interface for data entry.Strict Input Validation: * Prevents null or empty inputs for essential metadata (names, IDs).Safely handles InputMismatchException risks by verifying numeric formats.Enforces business rules (e.g., course credits bounded strictly between 1.0 and 4.0).Automated Calculation Engine: Accurately computes cumulative metrics based on weighted grade points.Persistent Storage: Automatically writes transaction logs to result.txt, complete with system-generated timestamps for auditing.Session Persistence: Loop-driven execution allows multiple sequential student entries without restarting the JVM.📊 Grading Scale & ClassificationThe system utilizes a standard 4.0 university grading scale.Letter GradeGrade PointCGPA RangeClassificationA+4.003.75 - 4.00🌟 OutstandingA3.753.50 - 3.74🏆 ExcellentA-3.503.00 - 3.49👍 GoodB+3.252.00 - 2.99✅ PassB3.00< 2.00❌ FailB-2.75C+2.50C2.25D2.00F0.00🚀 Getting StartedPrerequisitesTo compile and run this application, ensure you have the following installed:Java Development Kit (JDK): Version 8 or higher (required for java.time API).Installation & ExecutionClone the repository or download the source files:Ensure GradeManagementSystem.java is in your working directory.Compile the Java source code:javac GradeManagementSystem.java
Execute the application:java GradeManagementSystem
📄 Usage ExampleUpon completing a student's data entry, the system generates a formatted transcript in the console and appends identical data to result.txt.Output Extract (result.txt):Student: Monira
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
🏗️ Project StructureThe codebase is intentionally kept minimalistic to demonstrate clear Object-Oriented principles.Course.java / class Course: The primary data model representing an academic course. Encapsulates properties (name, credit, grade) and houses the getGradePoint() conversion logic.GradeManagementSystem.java: The main driver class. Responsible for the UI loop, Scanner I/O handling, input validation, aggregation logic, and file manipulation using FileWriter.🤝 ContributingContributions, issues, and feature requests are welcome!Feel free to check the issues page if you want to contribute.
