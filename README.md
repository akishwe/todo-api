# Task Management API

This API allows you to manage tasks with basic CRUD (Create, Read, Update, Delete) functionality. It provides endpoints to list tasks, create new tasks, update existing tasks, retrieve details of a specific task, and delete tasks.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [API Endpoints](#api-endpoints)
  - [Get All Tasks](#get-all-tasks)
  - [Get Task by ID](#get-task-by-id)
  - [Create a Task](#create-a-task)
  - [Update a Task](#update-a-task)
  - [Delete a Task](#delete-a-task)
- [Request & Response Examples](#request--response-examples)

## Requirements

- PHP 7.4+ or 8.x
- Laravel 8.x or later
- Composer
- Database (MySQL, PostgreSQL, etc.)

## Installation

1. Clone the repository and navigate into the project folder:

    ```sh
    git clone <repository_url>
    cd <project_folder>
    ```

2. Install dependencies:

    ```sh
    composer install
    ```

3. Set up environment variables by creating a `.env` file:

    ```sh
    cp .env.example .env
    ```

4. Update your database settings in the `.env` file.

5. Run migrations to create the required database tables:

    ```sh
    php artisan migrate
    ```

6. Start the local development server:

    ```sh
    php artisan serve
    ```

## API Endpoints

### Get All Tasks

- **URL**: `/api/tasks`
- **Method**: `GET`
- **Query Parameters**:
  - `completed` (optional): A boolean value (`true` or `false`) to filter tasks based on their completion status.
- **Response**: A list of tasks.

### Get Task by ID

- **URL**: `/api/tasks/{id}`
- **Method**: `GET`
- **URL Parameters**:
  - `id` (required): The ID of the task to retrieve.
- **Response**: Details of the specific task.

### Create a Task

- **URL**: `/api/tasks`
- **Method**: `POST`
- **Request Body** (JSON):
  - `title` (string, required): The title of the task. Max 255 characters.
  - `description` (string, optional): The description of the task.
  - `completed` (boolean, optional): The completion status of the task (defaults to `false` if not provided).
- **Response**: The created task along with a success message.

### Update a Task

- **URL**: `/api/tasks/{id}`
- **Method**: `PUT` or `PATCH`
- **URL Parameters**:
  - `id` (required): The ID of the task to update.
- **Request Body** (JSON):
  - `title` (string, optional): The updated title of the task. Max 255 characters.
  - `description` (string, optional): The updated description of the task.
  - `completed` (boolean, optional): The updated completion status of the task.
- **Response**: The updated task along with a success message.

### Delete a Task

- **URL**: `/api/tasks/{id}`
- **Method**: `DELETE`
- **URL Parameters**:
  - `id` (required): The ID of the task to delete.
- **Response**: A success message indicating the task was deleted.

## Request & Response Examples

### Get All Tasks

**Request**:
```http
GET /api/tasks?completed=true
