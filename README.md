import time

# DBMS Questions
dbms_quiz= [
        
            {
            'question': 'What is the full form of DBMS?',
            'options': ['Database Management System', 'Data Management System', 'Database Machine System', 'Data Base Machine System'],
            'answer': 'Database Management System'
        },
             {
            'question': 'What is the primary function of DBMS?',
            'options': ['To manage files', 'To manage networks', 'To manage databases', 'To manage applications'],
            'answer': 'To manage databases'
        },
        {
            'question': 'Which of the following is a type of database model?',
            'options': ['Hierarchical Model', 'Relational Model', 'Network Model', 'All of the above'],
            'answer': 'All of the above'
        },
         {
            'question': 'Which is the following is a popular DBMS ?',
            'options': ['oracle', 'microsoft excel', 'google chrome', 'mozilla firefox'],
            'answer': 'oracle'
        },
         {
            'question': 'What is a primary key in a relational database?',
            'options': ['A unique identifier for each row', 'A foreign key that references another table','A composite key made up of multiple columns','An index used for faster querying'
],
            'answer': ' A unique identifier for each row'
        }

        

    ]
# Data structure questions
ds_quiz = [
        {
            'question': 'Which of the following is not a linear data structure?',
            'options': ['Array', 'Queue', 'Stack', 'Tree'],
            'answer': 'Tree'
        },
        {
            'question': 'What is the time complexity of accessing an element in an array?',
            'options': ['O(1)', 'O(n)', 'O(log n)', 'O(n^2)'],
            'answer': 'O(1)'
        },
        
        {
            'question': 'In a linked list, each node contains?',
            'options': ['Data and a pointer to the next node', 'Only data', 'Only pointer', 'Data and a pointer to the previous node'],
            'answer': 'Data and a pointer to the next node'
        },
        {
            'question': 'Which data structure is used to implement a priority queue?',
            'options': ['array', 'linked list', 'heap', 'graph'],
            'answer': 'heap'
        },
        {
            'question': 'What is the primary purpose of a stack data structure?',
            'options': [' To store data in a sorted order', 'To optimize search operations', 'To follow the LIFO (Last-In-First-Out) principle', ' To implement recursive algorithms'],
            'answer': 'To follow the LIFO (Last-In-First-Out) principle'
        }
    ]




# Function to conduct the quiz
def conduct_quiz(quiz, course_name):
    print(f"\nStarting {course_name} Quiz...\n")
    score = 0

    for i, question in enumerate(quiz):
        print(f"Q{i + 1}: {question['question']}")
        for idx, option in enumerate(question['options'], start=1):
            print(f"{idx}. {option}")
        
        answer = input("Your answer (1/2/3/4): ")
        
        if question["options"][int(answer) - 1] == question["answer"]:
            print("Correct!\n")
            score += 1
        else:
            print(f"Incorrect. The correct answer is: {question['answer']}\n")
        
        time.sleep(1)

    return score

def main():
    print("Welcome to the Quiz Program!\n")
    print("Choose a course to start the quiz:\n1. DBMS\n2. Data Structures")
    choice = input("Enter your choice (1/2): ")
    
    if choice == "1":
        score = conduct_quiz(dbms_quiz, "DBMS")
    elif choice == "2":
        score = conduct_quiz(ds_quiz, "Data Structures")
    else:
        print("Invalid choice! Exiting the program.")
        return

    print(f"\nYour final score: {score}/{len(dbms_quiz) if choice == '1' else len(ds_quiz)}")
    print("Thank you for participating in the quiz!")

if __name__ == "__main__":
    main()
