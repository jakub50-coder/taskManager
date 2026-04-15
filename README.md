This project (a personal task manager) is a full-stack AI-powered task manager built using Spring Boot and Java.
It allows users to create, update, and manage tasks while also using an AI model to automatically suggest the task’s priority and status based on the task title and description.

The goal of this project is to demonstrate:
  
  -REST API development using Spring Boot
  
  -Integration with an AI model (GPT-4)
  
  -Frontend interaction using HTML + JavaScript (Fetch API)
  
  -Unit testing using JUnit
  
  -Clean backend structure using controllers, services, and DTOs

Technologies Used:

  -Java 17
  
  -Spring Boot
  
  -Maven
  
  -REST APIs
  
  -OpenAI GPT-4 API
  
  -HTML + JavaScript (Fetch API)
  
  -JUnit 5
  
  -H2 In-Memory Database

Users can:

  -Create tasks
  
  -View all tasks
  
  -Update tasks
  
  -Delete tasks
  
  -Automatically generate AI-based priority and status recommendations 
  
  The AI analyzes the task text and classifies it as:
  
      -HIGH priority (urgent, deadlines, exams, etc.)
      
      -MEDIUM priority (normal tasks)
      
      -LOW priority (small personal tasks like groceries or cleaning)

Clone the repository

git clone https://github.com/jakubcholko23/taskManager.git
cd taskManager


Run the project:

./mvnw spring-boot:run

Running test: 

./mvnw test

Setup steps

Clone the repository: 

    git clone https://github.com/jakubcholko23/taskManager.git
    
    cd taskManager

Set up OpenAI API key:

    set OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxx

Check to make sure that the key works:

    echo %OPENAI_API_KEY%   # Windows
    
    echo $OPENAI_API_KEY    # Mac/Linux

Run and build the project:

     ./mvnw clean spring-boot:run
  
AI-Powered Endpoint
POST /api/ai/suggest
This endpoint sends the task title and description to GPT-4 and returns a recommended priority and status.

Example Request
{
  "title": "Finish project tonight",
  "description": "The deadline is tomorrow morning"
}
Example Response
{
  "suggestedPriority": "HIGH",
  "suggestedStatus": "TODO",
  "message": "This task is urgent because it has a deadline tomorrow."
}

Other API Endpoints
1. Get All Tasks
GET /api/tasks

Example Response
[
  {
    "id": 1,
    "title": "Buy groceries",
    "description": "Milk, eggs, and bread",
    "priority": "LOW",
    "status": "TODO"
  }
]

2. Get Task By ID
GET /api/tasks/{id}

Example
GET /api/tasks/1
Response
{
  "id": 1,
  "title": "Buy groceries",
  "description": "Milk, eggs, and bread",
  "priority": "LOW",
  "status": "TODO"
}

3. Create a Task
POST /api/tasks

Example Request
{
  "title": "Study for exam",
  "description": "Exam is next week",
  "priority": "HIGH",
  "status": "TODO"
}
Example Response
{
  "id": 2,
  "title": "Study for exam",
  "description": "Exam is next week",
  "priority": "HIGH",
  "status": "TODO"
}

4. Update a Task
PUT /api/tasks/{id}

Example
{
  "title": "Study for exam",
  "description": "Exam tomorrow",
  "priority": "HIGH",
  "status": "IN_PROGRESS"
}

5. Delete a Task
DELETE /api/tasks/{id}

Example
DELETE /api/tasks/2
Response
Task deleted successfully
