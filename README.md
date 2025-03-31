# Best Practices and Prompt Engineering with GitHub Copilot

## 💫 Overview

GitHub Copilot is an AI-powered code completion tool that helps developers write code faster and with fewer errors. It uses machine learning to suggest code snippets, functions, and even entire classes based on the context of the code being written. This repository contains best practices and prompt engineering techniques to get the most out of GitHub Copilot.

## Prompt engineering for GitHub Copilot

### Start General then Get Specific

When writing prompts for GitHub Copilot, start with a general description of what you want to achieve, then narrow it down to specific details. This helps the model understand the context and generate more relevant suggestions.

An example of a general prompt is:
Open GitHub Copilot Chat and ask:

```plaintext
@workspace I want to create a feature to update the status of a task. The function should take a task ID and a new status as parameters and update the task's status in the database. For example, if the task ID is 1 and the status is "IN_PROGRESS", it should update the task with ID 1 to have the status "IN_PROGRESS".
```

### Give Examples

When asking GitHub Copilot to generate code, provide examples of the input and output you expect. This helps the model understand the desired format and structure of the code.

An example of a prompt that provides an example is:
Open GitHub Copilot Chat and ask:

```plaintext
@workspace I want to add a new functionality to fetch tasks by their status. The function should take a status parameter and return an array of tasks that match the status. For example, if the status is "OPEN", it should return all OPEN tasks. Expected Input: { status: "OPEN" } Expected Output: [ { id: 1, title: "Task 1", status: "OPEN", "user": {"id": 1, "name": "John Doe", "email": "john.doe@example.com"}}, { id: 2, title: "Task 2", status: "OPEN", "user": {"id": 2, "name": "Jane Doe", "email": "jane.doe@example.com"}} ]
```

This prompt provides a clear description of the desired functionality, along with an example of the expected input and output. This helps GitHub Copilot understand what you are looking for and generate relevant code suggestions.

### Break Complex Tasks Into Simpler Tasks

When working on complex tasks, break them down into smaller, more manageable tasks. This makes it easier for GitHub Copilot to generate relevant code snippets and helps you stay focused on one task at a time.

An example of a complex task is:
Open GitHub Copilot Chat and ask:

```plaintext
@workspace Implement a new feature for task assignment and notification system in the project management app. The feature should allow users to assign tasks to team members and send notifications when a task is assigned.
```

This prompt is complex and may lead to confusion. Instead, break it down into smaller tasks:

Open GitHub Copilot Chat and ask:

1. **Assigning Tasks**

```plaintext
@workspace Create a function to assign a task to a user. The function should take a task ID and a user ID as parameters and update the task's assigned user.
```

2. **Notification System**

```plaintext
@workspace Create a function to send a notification when a task is assigned. The function should take a user ID and a task ID as parameters and send a notification to the user. Integrate a third-party notification service like SendGrid or Nodemailer to send the notification.
```

3. **Testing**

```plaintext
@workspace Write unit tests for the task assignment and notification functions. Use a testing framework like Jest or Mocha to write the tests.
```

This approach allows GitHub Copilot to focus on one task at a time, making it easier to generate relevant code snippets and suggestions.

### Avoid Ambiguity

When writing prompts, avoid using ambiguous language or vague descriptions. Be as specific as possible about what you want to achieve. This helps GitHub Copilot generate more accurate and relevant code suggestions.

An example of an ambiguous prompt is:

Open GitHub Copilot Chat and ask:

```plaintext
What does this?
```

This prompt is ambiguous because it does not specify what "this" refers to. Instead, provide a specific code snippet or function name to clarify your request.

Open the `userService.ts` file or reference the file in your prompt using the #file tag. Then ask:

```plaintext
What does `createUser` do? #file:userService.ts
```

This prompt is more specific and provides context for GitHub Copilot to understand what you are asking.

### Indicate relevant code

When asking GitHub Copilot to generate code, indicate any relevant code that should be considered. This helps the model understand the context and generate more relevant suggestions.

#### Open Relevant Files

Open relevant files: These are the files that are directly related to the task you're working on. For example, if you're working on a feature related to user creation, open files such as `user.controller.ts`, `user.service.ts`, or `user.entity.ts`. Having these files open gives Copilot more context, helping it understand your codebase better and provide accurate suggestions based on the code in those files.

#### Close Irrelevant Files

Close irrelevant files: These are files that are not related to the current task. For example, if you're working on a user feature, files related to UI components or unrelated services may distract Copilot from offering useful suggestions. Closing these files allows Copilot to focus on the relevant context, which improves the quality of its suggestions.

#### Highlight Code

Highlight code: To ensure that Copilot Chat understands the context of your inquiry, open the specific file or highlight the section of code you want it to reference. By using the #selection variable to specify the highlighted code, you allow Copilot Chat to analyze the precise context, making its suggestions and answers more accurate and tailored to your needs.

An example of a prompt that highlights code is:

Open the `userService.ts` file and highlight the `createUserWithRole` function. Then ask to GitHub Copilot Chat:

```plaintext
@workspace /explain #selection What does this function do?
```

This prompt provides a clear context for GitHub Copilot to understand what you are asking. By highlighting the specific code, you ensure that Copilot focuses on the relevant section and provides an accurate explanation.

#### Specify which Files to Reference

Specify which files to reference: You can instruct Copilot Chat to focus on particular files in your project. For instance, in Visual Studio Code, you can use the #file variable to indicate a specific file or the @workspace participant to reference all files in the current workspace. This helps the chat to draw upon the correct context, enabling it to provide more relevant guidance based on the specified code or file.

Ask to GitHub Copilot Chat:

```plaintext
@workspace What are the main functions in this file? #file:userService.ts
```

### Keep History Relevant

Copilot Chat uses the chat history to get context about your request. To give Copilot only the relevant history:

Use threads to start a new conversation for a new task
![alt text](./assets/copilot-chat-start-conversation.png)

Delete requests that are no longer relevant or that didn’t give you the desired result

![alt text](./assets/remove-request.png)
