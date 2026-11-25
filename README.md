DAY 5 ASSIGNMENT
A. User Manual Procedure
Title: How to Set Up a GitHub Repository from Scratch and Make the First Commit
1. Prerequisites
Before starting, ensure that you have:
- A computer with internet access.
- A GitHub account.
- Git installed on your computer.
- Visual Studio Code installed.
- Basic knowledge of using a computer.
- A project folder containing at least one file.
2. Procedure
Step 1: Open the GitHub website.
- Action: Open your web browser and visit https://github.com.
- Expected result: The GitHub homepage appears.
Step 2: Sign in to your GitHub account.
- Action: Enter your GitHub username and password.
- Expected result: Your GitHub dashboard opens.
Step 3: Create a new repository.
- Action: Click the New button or the New repository option.
- Expected result: The repository creation page appears.
Step 4: Enter the repository name.
- Action: Type a name for your repository in the Repository name field.
- Expected result: The repository name appears in the field.
Step 5: Configure repository visibility.
- Action: Select either Public or Private.
- Expected result: Your preferred repository visibility is selected.
Step 6: Create the repository.
- Action: Click the Create repository button.
- Expected result: GitHub creates the repository and displays its page.
Step 7: Open your project folder in Visual Studio Code.
- Action: Open Visual Studio Code and select File, then Open Folder.
- Expected result: Your project folder appears in the VS Code Explorer.
Step 8: Open the terminal.
- Action: Select Terminal, then New Terminal.
- Expected result: The integrated terminal appears.
Step 9: Initialize Git.

- Action: Run the following command:
git init


- Expected result: Git initializes a repository in your project folder.

Step 10: Add project files.

- Action: Run:
git add .


- Expected result: Git stages the project files for committing.

Step 11: Create the first commit.

- Action: Run:
git commit -m "Initial commit"


- Expected result: Git creates the first commit.

Step 12: Connect the local repository to GitHub.

- Action: Run the following command, replacing the URL with your repository URL:
git remote add origin https://github.com/USERNAME/REPOSITORY.git


- Expected result: Your local Git repository is connected to GitHub.

Step 13: Rename the branch to main.

- Action: Run:
git branch -M main


- Expected result: Your current branch is named main.

Step 14: Upload the project to GitHub.

- Action: Run:
git push -u origin main


- Expected result: Your project files appear in your GitHub repository.
3. Screenshot Description
Screenshot 1: Show the GitHub repository creation page with the repository name and visibility options.

Screenshot 2: Show the VS Code terminal displaying the successful git commit command.

Screenshot 3: Show the GitHub repository page displaying the uploaded project files.
4. Troubleshooting
Problem: Git displays the error Author identity unknown.

Cause: Git does not have the user's name and email configured.

Solution: Run these commands:
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"


Then repeat the commit command:
git commit -m "Initial commit"



B. API Reference Entry
Title: Create a New Task API
1. Endpoint Information
Item	Description
API Name	Create a New Task
HTTP Method	POST
Endpoint	/api/v1/tasks
Authentication	Required
Content Type	JSON

2. Description
This endpoint allows an authenticated user to create a new task in the project management application.

The task is automatically associated with the authenticated user who submits the request.
3. Request Parameters
Path Parameters

This endpoint does not require any path parameters.

Query Parameters
Parameter	Type	Required	Description
None	N/A	No	No query parameters are required.

Body Parameters
Parameter	Type	Required	Description
title	String	Yes	The title of the task.
description	String	No	A detailed explanation of the task.
due_date	String	No	The task deadline in YYYY-MM-DD format.
priority	String	Yes	The task priority: low, medium, or high.
status	String	No	The task status: pending, in_progress, or completed.

4. Required Headers
Header	Required	Description
Authorization	Yes	Contains the user's authentication token.
Content-Type	Yes	Must be application/json.
Accept	No	Indicates that the client accepts JSON responses.

Example:
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Accept: application/json


5. Example Request Body
{
  "title": "Complete Technical Writing Assignment",
  "description": "Prepare and submit the Day 5 assignment.",
  "due_date": "2026-11-30",
  "priority": "high",
  "status": "pending"
}


6. Successful Response
201 Created
Description: The task was successfully created.

Example response:
{
  "success": true,
  "message": "Task created successfully.",
  "data": {
    "id": 105,
    "user_id": 24,
    "title": "Complete Technical Writing Assignment",
    "description": "Prepare and submit the Day 5 assignment.",
    "due_date": "2026-11-30",
    "priority": "high",
    "status": "pending",
    "created_at": "2026-11-25T10:30:00Z"
  }
}


7. HTTP Response Codes
Status Code	Meaning	Condition
201	Created	The task was successfully created.
400	Bad Request	The request contains invalid data or malformed JSON.
401	Unauthorized	The authentication token is missing or invalid.
403	Forbidden	The authenticated user is not permitted to create tasks.
404	Not Found	The requested API route does not exist.
405	Method Not Allowed	An unsupported HTTP method was used.
409	Conflict	The request conflicts with an existing resource or application rule.
415	Unsupported Media Type	The request does not use JSON content type.
422	Unprocessable Entity	One or more fields fail validation.
429	Too Many Requests	The user has exceeded the allowed request limit.
500	Internal Server Error	An unexpected server error occurred.

8. Important Notes
- Users must authenticate before creating tasks.
- The task title and priority are required.
- The priority must be low, medium, or high.
- The status must be pending, in_progress, or completed.
- The user ID is obtained from the authenticated session and should not be supplied by the client.