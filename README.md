Student Grade Calculator
Project Description
A comprehensive grade calculator that processes multiple students' marks, calculates grades with personalized comments, and provides class statistics.
What I Learned
1. Conditional Logic: Using if/elif/else for decision making
2. Lists: Storing and manipulating collections of data
3. Loops: Using for and while loops for repetition
4. Error Handling: Using try-except to handle invalid inputs
5. Functions: Organizing code into reusable blocks

Features
•	Processes multiple students
•	Calculates grades based on custom grading system
•	Provides personalized comments for each student
•	Calculates class statistics (average, highest, lowest)
•	Formatted table output with color coding
•	Input validation for all user inputs
•	Error handling for edge cases
•	Search functionality for specific students
•	Certificate Progress:
•	Formatted table output with color coding
•	Input validation for all user inputs
•	Error handling for edge cases
•	Search functionality for specific students
•	Save results to file option







How to Run
bash
•	 Navigate to project folder
•	 cd week2-grade-calculator
•	 Run the program
•	 python grade_calculator.py
•	 Sample test with provided data
•	 python grade_calculator.py < test_students.txt
Grading System

•	A: 90-100 (Excellent!)
•	B: 80-89 (Very Good!)
•	C: 70-79 (Good)
•	D: 60-69 (Needs Improvement)
•	F: 0-59 (Failed - Please seek help)
•	Sample Output

















Code:

# Student Grade Calculator
# Week 2 Project - Control Flow & Data Structures

def calculate_grade(average):
    """Calculate grade based on average marks"""
    if average >= 90:
        return 'A', 'Excellent! Keep up the great work!'
    elif average >= 80:
        return 'B', 'Very Good! You\'re doing well.'
    elif average >= 70:
        return 'C', 'Good. Room for improvement.'
    elif average >= 60:
        return 'D', 'Needs Improvement. Please study more.'
    else:
        return 'F', 'Failed. Please seek help from teacher.'

def get_valid_number(prompt, min_val=0, max_val=100):
    """Get a valid number within specified range"""
    while True:
        try:
            value = float(input(prompt))
            if min_val <= value <= max_val:
                return value
            else:
                print(f"Please enter a number between {min_val} and {max_val}")
        except ValueError:
            print("Invalid input! Please enter a number.")

def main():
    print("=" * 50)
    print("      STUDENT GRADE CALCULATOR")
    print("=" * 50)
    print()
    
    # Get number of students with validation
    while True:
        try:
            num_students = int(input("Enter number of students: "))
            if num_students > 0:
                break
            else:
                print("Please enter a positive number!")
        except ValueError:
            print("Invalid input! Please enter a whole number.")
    
    # Initialize lists to store data
    student_names = []
    student_marks = []  # Will be list of lists
    student_results = []  # Will store (average, grade, comment)
    
    # Collect data for each student
    for i in range(num_students):
        print(f"\n=== STUDENT {i+1} ===")
        
        # Get student name
        name = input("Student name: ")
        while name.strip() == "":
            print("Name cannot be empty!")
            name = input("Student name: ")
        student_names.append(name)
        
        # Get marks for 3 subjects
        print("Enter marks (0-100):")
        math = get_valid_number("Math: ")
        science = get_valid_number("Science: ")
        english = get_valid_number("English: ")
        
        # Store marks
        student_marks.append([math, science, english])
        
        # Calculate average
        average = (math + science + english) / 3
        
        # Get grade and comment
        grade, comment = calculate_grade(average)
        
        # Store results
        student_results.append({
            'average': average,
            'grade': grade,
            'comment': comment
        })
    
    # Display results
    print("\n" + "=" * 50)
    print("            RESULTS SUMMARY")
    print("=" * 50)
    print(f"{'Name':<20} | {'Avg':>5} | {'Grade':^5} | Comment")
    print("-" * 60)
    
    for i in range(num_students):
        name = student_names[i]
        avg = student_results[i]['average']
        grade = student_results[i]['grade']
        comment = student_results[i]['comment']
        
        print(f"{name:<20} | {avg:>5.1f} | {grade:^5} | {comment}")
    
    # Calculate and display statistics
    if num_students > 0:
        averages = [result['average'] for result in student_results]
        class_avg = sum(averages) / len(averages)
        max_avg = max(averages)
        min_avg = min(averages)
        max_index = averages.index(max_avg)
        min_index = averages.index(min_avg)
        
        print("\n" + "=" * 50)
        print("          CLASS STATISTICS")
        print("=" * 50)
        print(f"Total Students: {num_students}")
        print(f"Class Average: {class_avg:.1f}")
        print(f"Highest Average: {max_avg:.1f} ({student_names[max_index]})")
        print(f"Lowest Average: {min_avg:.1f} ({student_names[min_index]})")
    
    print("\n" + "=" * 50)
    print("Thank you for using the Grade Calculator!")
    print("=" * 50)

if __name__ == "__main__":
    main()



Algorithm flow of project

Algorithm – Student Grade Calculator
Step 1: Start the Program
•	Display the title "Student Grade Calculator". 
Step 2: Get Number of Students
•	Ask the user to enter the number of students. 
•	Validate the input: 
o	It must be a positive integer. 
o	If invalid, display an error message and ask again. 
Step 3: Initialize Data Structures
Create three lists:
•	student_names → Store student names. 
•	student_marks → Store marks of each student. 
•	student_results → Store average, grade, and comment. 
Step 4: Repeat for Each Student
For every student:
1.	Ask for the student's name. 
2.	Validate that the name is not empty. 
3.	Ask for marks in: 
o	Math 
o	Science 
o	English 
4.	Validate each mark: 
o	Must be between 0 and 100. 
5.	Store the marks. 
6.	Calculate the average: 
Average=Math+Science+English3Average = \frac{Math + Science + English}{3}Average=3Math+Science+English 
7.	Determine the grade: 
o	Average ≥ 90 → Grade A 
o	Average ≥ 80 → Grade B 
o	Average ≥ 70 → Grade C 
o	Average ≥ 60 → Grade D 
o	Otherwise → Grade F 
8.	Store: 
o	Average 
o	Grade 
o	Comment 
Step 5: Display Student Results
Print a table showing:
•	Student Name 
•	Average Marks 
•	Grade 
•	Comment 
Step 6: Calculate Class Statistics
Calculate:
•	Class Average 
•	Highest Average 
•	Lowest Average 
•	Student with Highest Average 
•	Student with Lowest Average 
Step 7: Display Statistics
Print:
•	Total Students 
•	Class Average 
•	Highest Average 
•	Lowest Average 
Step 8: End Program
Display a thank-you message and terminate the program.

                





Flowchart (Text Format)


              START
                   │
                   ▼
      Display Program Title
                   │
                   ▼
     Enter Number of Students
                   │
        Is Input Valid?
          /            \
        No              Yes
        │                │
Show Error Message       ▼
        │       Initialize Lists
        └───────────────►│
                          ▼
               More Students Left?
                    /          \
                  Yes           No
                   │             │
                   ▼             ▼
           Enter Student Name   Display Results
                   │             │
         Name Empty?             ▼
           /     \        Calculate Statistics
         Yes     No             │
          │       │             ▼
 Ask Again        ▼     Display Statistics
                  │             │
                  ▼             ▼
         Enter Math Marks       Thank You
                  │             │
           Validate Marks       ▼
                  │            END
                  ▼
        Enter Science Marks
                  │
           Validate Marks
                  │
                  ▼
        Enter English Marks
                  │
           Validate Marks
                  │
                  ▼
         Calculate Average
                  │
                  ▼
          Calculate Grade
                  │
                  ▼
        Store Student Result
                  │
                  └──────────────► Repeat
