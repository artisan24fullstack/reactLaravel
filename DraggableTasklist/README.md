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
