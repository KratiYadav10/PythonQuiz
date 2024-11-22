import time

# In-memory data for users (username, password)
users = {}

# DBMS Questions
dbms_quiz = [
    {
        "question": "What is a primary key in a database?",
        "options": ["A unique identifier for a record", "A foreign key", "A data type", "An index"],
        "answer": "A unique identifier for a record"
    },
    {
       'question': 'What is the primary function of DBMS?',
            'options': ['To manage files', 'To manage networks', 'To manage databases', 'To manage applications'],
            'answer': 'To manage databases'
    },
    {
        "question": "Which SQL statement is used to extract data from a database?",
        "options": ["SELECT", "UPDATE", "INSERT", "DELETE"],
        "answer": "SELECT"
    },
    {
         'question': 'Which is the following is a popular DBMS ?',
            'options': ['oracle', 'microsoft excel', 'google chrome', 'mozilla firefox'],
            'answer': 'oracle'
    },
    {
        'question': 'Which of the following is a type of database model?',
            'options': ['Hierarchical Model', 'Relational Model', 'Network Model', 'All of the above'],
            'answer': 'All of the above'
        },
    
]

# Data Structures Questions
ds_quiz = [
    {
         'question': 'What is the primary purpose of a stack data structure?',
            'options': [' To store data in a sorted order', 'To optimize search operations', 'To follow the LIFO (Last-In-First-Out) principle', ' To implement recursive algorithms'],
            'answer': 'To follow the LIFO (Last-In-First-Out) principle'
    },
    {
        "question": "Which data structure uses LIFO (Last In, First Out) order?",
        "options": ["Stack", "Queue", "Linked List", "Tree"],
        "answer": "Stack"
    },
    {
        "question": "Which algorithm is used for finding the shortest path in a graph?",
        "options": ["Dijkstra’s Algorithm", "Quick Sort", "Bubble Sort", "Merge Sort"],
        "answer": "Dijkstra’s Algorithm"
    },
    {
        "question": "What is the time complexity of accessing an element in an array?",
        "options": ["O(1)", "O(n)", "O(log n)", "O(n^2)"],
        "answer": "O(1)"
    },
    {
        'question': 'Which data structure is used to implement a priority queue?',
            'options': ['array', 'linked list', 'heap', 'graph'],
            'answer': 'heap'
    }
]

# Function for user registration
def register_user():
    print("\n--- Register ---")
    username = input("Enter a username: ")
    password = input("Enter a password: ")
    
    if username in users:
        print("Username already exists! Please choose a different username.")
    else:
        users[username] = password
        print("Registration successful! You can now log in.\n")

# Function for user login
def login_user():
    print("\n--- Login ---")
    username = input("Enter your username: ")
    password = input("Enter your password: ")
    
    if username in users and users[username] == password:
        print("Login successful!\n")
        return username
    else:
        print("Invalid credentials! Please try again.\n")
        return None

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

# Main function to control the flow
def main():
    print("Welcome to the Quiz Program!\n")
    print("1. Register\n2. Login")
    choice = input("Choose an option (1/2): ")

    # Register or Login
    if choice == '1':
        register_user()
        return main()  # Restart the main menu after registration
    elif choice == '2':
        username = login_user()
        if not username:
            return main()  # Restart the main menu if login failed
    else:
        print("Invalid choice! Exiting the program.")
        return

    # After login, allow the user to choose a course and take a quiz
    print(f"Welcome back, {username}!\n")
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
