 # How to Use React.js with Laravel to Build a Draggable Tasklist App

 ## How to Create Models and Migrations
 ```
php artisan make:model Project -m

php artisan make:model Task -m
 ```

## How to Create Seeders

```
php artisan make:seeder ProjectsSeeder

php artisan make:seeder TasksSeeder
```


## Database / Seeders
```
php artisan optimize

php artisan migrate:fresh --seed
```

## Service Injection

```
php artisan make:controller TaskController

```

- Manually create a app/Services/ProjectService.php service class, which will be responsible for the project-related logic.

- The second service class will be the app/Services/TaskService.php, which will be responsible for doing task manipulations:

- In the above TaskService class, you'll use the following functions in the TaskController.
```
> list: 
- fetches tasks for a given project ID, including the related project, and orders them by priority.

> getById: 
- retrieves a specific task by its ID, including the related project.

> store: 
- stores a new task, calculating the priority based on existing tasks for the same project.

> update: 
- updates an existing task by its ID.

> delete: 
- deletes a task by its ID and adjusts the priorities of remaining tasks in the same project.

> reorder: 
- changes the priorities of tasks within a project, (handles soft delete as well with deleted_at IS NULL).
```

## Web and API Routes

## Validation Requests + rules / authorize true

```
php artisan make:request Task/CreateTaskRequest

php artisan make:request Task/ListTasksRequest

php artisan make:request Task/ReorderTasksRequest

php artisan make:request Task/UpdateTaskRequest
``` 

## Write a Controller that Uses Services

## Test the API Routes with postman

```
php artisan serve
```
- Task Management API

> List Tasks
- http://localhost:8000/api/tasks?project_id=1

> Get Task
- http://localhost:8000/api/tasks/1

> Create Task
- http://localhost:8000/api/tasks?project_id=1

> Update Task
- http://localhost:8000/api/tasks/11

> Delete Task
- http://localhost:8000/api/tasks/11

> Reorder Tasks 
- http://localhost:8000/api/tasks



## Frontend: Install the Packages

```
npm i react-dom dotenv react-beautiful-dnd react-responsive-modal react-toastify @vitejs/plugin-react

npm i -D @types/react-dom @types/react-beautiful-dnd
```

## A Service for the API Requests
 
 - Just create (axiosConfig.ts) for the global Axios configuration
  
```
import axios from 'axios';

export default axios.create({ baseURL: '/api' });
```

- So below is the utils.ts file:

> getErrorMessage: 
- Returns the error message if the input is an instance of Error – otherwise, converts it to a string.

> getTasks: 
- Retrieves tasks for a given project ID using Axios. 
- Displays an error toast if the project ID is missing or if the API request is unsuccessful.

> reorderTasks: 
- Sends a PUT request to reorder tasks within a project based on start and end positions. 
- Displays a success or error toast based on the API response.
  
> editTask: 
- Sends a PUT request to update task information. 
- Validates that the task has an ID and a title before making the request. 
- Displays a success or error toast based on the API response.

> deleteTask: 
- Sends a DELETE request to delete a task by its ID. 
- Displays a success or error toast based on the API response.

> createTask: 
- Sends a POST request to create a new task for a given project ID. 
- Validates that the project ID is present, and the task has a title before making the request. 
- Displays a success or error toast based on the API response.


## React Components

## Final Results

- By visiting http://127.0.0.1:8000
  
```
npm run build && php artisan serve
```
