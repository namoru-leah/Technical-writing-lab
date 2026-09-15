# Exercise B: API Reference Entry

## Creating a New Task in a Project Management Application

### Overview

The project management application provides an API endpoint that allows an authenticated user to create a new task inside an existing project. An API, or Application Programming Interface, allows different software applications to communicate with each other.

In this case, a developer can send a request to the project management application's API, provide the required task information, and receive a response confirming whether the task was successfully created.

The endpoint uses the HTTP `POST` method because the purpose of the request is to create a new resource.

### Endpoint

```text
POST /api/v1/projects/{projectId}/tasks
```

The `{projectId}` portion of the URL identifies the project where the new task should be created. The API requires authentication so that only authorized users can create tasks.

### Endpoint Description

The `POST /api/v1/projects/{projectId}/tasks` endpoint creates a new task within the specified project. The authenticated user must provide a task title, an assignee, a due date, and a priority level. The task description is optional and can be used to provide additional information about the work that needs to be completed.

For example, if the project ID is `PRJ-1001`, the complete endpoint would be:

```text
POST /api/v1/projects/PRJ-1001/tasks
```

The API processes the request and, if all required information is valid and the user has permission to create the task, returns a response containing the newly created task.

### Path Parameter

The endpoint contains one path parameter called `projectId`. This parameter is required because the API needs to know which project should contain the new task. The parameter uses a string data type and represents the unique identifier of the project.

For example:

```text
projectId = PRJ-1001
```

In this example, `PRJ-1001` identifies the project in which the new task will be created.

### Request Headers and Authentication

The endpoint requires two request headers. The first is the `Authorization` header. This header is required because the endpoint only allows authenticated users to create tasks. The authentication token is provided using the Bearer authentication scheme.

The authorization header should be written as:

```text
Authorization: Bearer <access_token>
```

The `<access_token>` represents a valid authentication token issued to the user. The server uses this token to determine whether the user is authenticated and whether the user has permission to perform the requested action.

The second required header is the `Content-Type` header. It informs the server that the request body is written in JSON format.

```text
Content-Type: application/json
```

Both headers are important because the server needs to authenticate the user and correctly interpret the request body.

### Request Body

The request body contains the information needed to create the new task.

The `title` field is required and contains the name of the task as a string. The `description` field is optional and contains additional information about the task. The `assigneeId` field is required and identifies the user who will be responsible for completing the task.

The `dueDate` field is required and specifies the date by which the task should be completed. The date must use the `YYYY-MM-DD` format.

The `priority` field is also required. It identifies how important the task is. The API accepts three possible values: `low`, `medium`, and `high`.

### Example Request

A complete API request would contain the endpoint, authentication information, content type, and JSON request body.

The request could be written as:

```text
POST /api/v1/projects/PRJ-1001/tasks
Authorization: Bearer <access_token>
Content-Type: application/json
```

The JSON request body would be:

```json
{
  "title": "Complete project proposal",
  "description": "Finish and submit the project proposal.",
  "assigneeId": "USR-1024",
  "dueDate": "2026-09-30",
  "priority": "high"
}
```

In this example, the API is being asked to create a task called "Complete project proposal." The task belongs to project `PRJ-1001` and is assigned to user `USR-1024`. The task is due on September 30, 2026, and has a high priority. The description provides additional information about the work.

The `description` field is optional, so a developer can leave it out when no additional information is necessary. However, the `title`, `assigneeId`, `dueDate`, and `priority` fields must be included.

### HTTP Response Codes

The API uses HTTP status codes to communicate the result of each request.

A **201 Created** response means that the task was successfully created. This is the expected response when all required information is valid and the authenticated user has permission to create the task.

A **400 Bad Request** response means that the request contains invalid information or is missing one or more required fields. For example, this could occur if the request does not include a task title or contains an invalid priority value.

A **401 Unauthorized** response means that the request does not contain a valid authentication token. This could happen when the token is missing, expired, or invalid.

A **403 Forbidden** response means that the user has been successfully authenticated but does not have permission to create a task in the specified project.

A **404 Not Found** response means that a resource required by the request could not be found. For example, the specified project ID or assignee ID may not exist.

A **409 Conflict** response means that the request conflicts with the current state of a resource. This could occur if another operation has created a conflicting resource or if the current project state prevents the requested operation.

A **422 Unprocessable Entity** response means that the server understands the request but one or more values do not meet the application's validation requirements.

A **500 Internal Server Error** response means that an unexpected problem occurred on the server while processing the request. This generally indicates a server-side problem rather than an error in the developer's request.

### Successful Response

When the task is successfully created, the API returns a `201 Created` status code. The response body provides information about the newly created task. It contains information supplied in the original request as well as information generated by the server.

An example successful response is:

```json
{
  "id": "TASK-2045",
  "projectId": "PRJ-1001",
  "title": "Complete project proposal",
  "description": "Finish and submit the project proposal.",
  "assigneeId": "USR-1024",
  "dueDate": "2026-09-30",
  "priority": "high",
  "status": "open",
  "createdAt": "2026-09-15T10:30:00Z"
}
```

The `id` field contains the unique identifier generated for the newly created task. The `projectId` identifies the project containing the task. The `title` and `description` contain the information provided in the original request.

The `assigneeId` identifies the user who has been assigned the task, while `dueDate` and `priority` provide the task's deadline and importance level.

The `status` field shows the current state of the task. In this example, the newly created task has an `open` status, meaning that the task has been created but has not yet been completed.

The `createdAt` field records when the task was created. The timestamp uses the ISO 8601 format, which provides a standardized way of representing dates and times.

### Error Handling

If the request fails, the API should return an appropriate HTTP status code and provide enough information for the developer to understand what went wrong.

For example, a missing required field could result in a `400 Bad Request` response, while an invalid or missing authentication token could result in a `401 Unauthorized` response. A user who is authenticated but does not have permission to create a task could receive a `403 Forbidden` response.

Clear error handling is an important part of API documentation because developers need to know how their applications should respond to different situations. By documenting the possible response codes, the API makes it easier for developers to identify and correct problems without having to guess what caused the request to fail.

### Conclusion

The `POST /api/v1/projects/{projectId}/tasks` endpoint provides a structured method for creating a new task within a project management application. The endpoint requires authentication and uses a project ID to determine where the task should be created.

The request must include a title, assignee ID, due date, and priority, while the description is optional. The API documentation also explains the required headers, request format, possible HTTP response codes, and the structure of a successful response.

Providing this information allows developers to understand exactly how to use the endpoint without having to guess the required parameters or expected results. Clear and complete API documentation reduces integration errors, saves development time, and makes the software easier and more reliable to use.
