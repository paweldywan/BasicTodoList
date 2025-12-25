# BasicTodoList

A full-stack task management application built with ASP.NET Core 8 and React with TypeScript. This application provides a modern, secure, and user-friendly interface for managing daily tasks with authentication and authorization.

**Live Application:** https://basictodolist.paweldywan.com/

**Development URL:** https://localhost:7227

## Overview

BasicTodoList is a comprehensive todo list application featuring a clean separation of concerns using a three-tier architecture. The backend is built with ASP.NET Core 8, implementing RESTful APIs with Entity Framework Core for data persistence using PostgreSQL. The frontend utilizes React with TypeScript and Vite for a fast, responsive user experience. The application includes full user authentication and authorization using ASP.NET Core Identity, ensuring that each user's tasks remain private and secure.

## Key Features

- **User Authentication & Authorization**: Secure user registration and login using ASP.NET Core Identity
- **Personal Task Management**: Each user has their own private task list
- **CRUD Operations**: Create, read, update, and delete tasks
- **Task Ordering**: Move tasks up and down to prioritize your work
- **Task Properties**: 
  - Title
  - Due date (optional)
  - Completion status
  - Custom ordering
- **RESTful API**: Well-structured API endpoints for all task operations
- **Responsive UI**: Modern React-based interface with Bootstrap styling
- **API Documentation**: Interactive Swagger UI for API exploration
- **Docker Support**: Container-ready with Docker configuration
- **Database Seeding**: Sample data for development and testing

## Architecture

The solution follows a clean three-tier architecture pattern:

```
BasicTodoList
|
+-- BasicTodoList.Server (Web API / Presentation Layer)
|   |-- Controllers
|   |   +-- TaskController.cs
|   |-- Areas
|   |   +-- Identity (ASP.NET Core Identity Pages)
|   +-- Program.cs
|
+-- BasicTodoList.BLL (Business Logic Layer)
|   |-- Contracts
|   |   +-- ITaskService.cs
|   +-- Services
|       +-- TaskService.cs
|
+-- BasicTodoList.DAL (Data Access Layer)
|   |-- Entities
|   |   +-- Task.cs
|   |-- Configuration
|   |   +-- Entity
|   |       +-- TaskConfiguration.cs
|   |-- Migrations
|   |-- SampleData
|   |   +-- BasicTodoListSeeder.cs
|   +-- BasicTodoListContext.cs
|
+-- basictodolist.client (React Frontend)
    |-- src
    +-- package.json
```

### Project Responsibilities

**BasicTodoList.Server**
- Hosts the Web API and serves the React SPA
- Implements API controllers
- Handles authentication and authorization
- Configures middleware pipeline
- Manages dependency injection

**BasicTodoList.BLL**
- Contains business logic and service layer
- Implements service contracts/interfaces
- Handles data validation and business rules
- Manages user-specific data filtering

**BasicTodoList.DAL**
- Defines entity models
- Configures Entity Framework Core DbContext
- Manages database migrations
- Provides data seeding functionality
- Implements data access patterns

**basictodolist.client**
- React-based single-page application
- TypeScript for type safety
- Vite for fast development and building
- Bootstrap/Reactstrap for styling
- FontAwesome for icons

## Getting Started

### Prerequisites

- .NET 8 SDK
- Node.js (v18 or higher)
- PostgreSQL database
- Docker (optional, for containerized deployment)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/paweldywan/BasicTodoList.git
cd BasicTodoList
```

2. Configure the database connection:
   - Set up your PostgreSQL connection string in user secrets or appsettings.json
   - The default configuration expects PostgreSQL

3. Apply database migrations:
```bash
cd BasicTodoList.Server
dotnet ef database update
```

4. Install client dependencies:
```bash
cd ../basictodolist.client
npm install
```

### Running the Application

#### Option 1: Using Visual Studio
1. Open the solution file in Visual Studio 2022
2. Set BasicTodoList.Server as the startup project
3. Press F5 to run

#### Option 2: Using Command Line

1. Start the backend server:
```bash
cd BasicTodoList.Server
dotnet run
```

2. In a separate terminal, start the frontend development server:
```bash
cd basictodolist.client
npm run dev
```

3. Open your browser and navigate to:
   - **Application**: https://localhost:7227
   - **API Documentation**: https://localhost:7227/swagger

#### Option 3: Using Docker

```bash
docker build -t basictodolist .
docker run -p 8080:8080 -p 8081:8081 basictodolist
```

## Technology Stack

### Backend
- **Framework**: ASP.NET Core 8
- **Language**: C# 12 with nullable reference types
- **Database**: PostgreSQL
- **ORM**: Entity Framework Core 8.0.10
- **Authentication**: ASP.NET Core Identity
- **API Documentation**: Swashbuckle (Swagger)
- **Data Protection**: ASP.NET Core Data Protection with EF Core

### Frontend
- **Framework**: React 18.3.1
- **Language**: TypeScript
- **Build Tool**: Vite
- **UI Framework**: Bootstrap 5.3.3 / Reactstrap 9.2.3
- **Icons**: FontAwesome 6.6.0
- **Date Handling**: Moment.js 2.30.1

### Development Tools
- **Linting**: ESLint with TypeScript support
- **Code Generation**: ASP.NET Core Scaffolding
- **Containerization**: Docker

## API Documentation

The API follows RESTful conventions and is fully documented using Swagger. When running the application in development mode, access the interactive API documentation at:

**https://localhost:7227/swagger**

### Main Endpoints

All task endpoints require authentication (Bearer token).

#### Tasks

- **GET** `/api/task` - Get all tasks for the authenticated user
- **GET** `/api/task/{id}` - Get a specific task by ID
- **POST** `/api/task` - Create a new task
- **PUT** `/api/task` - Update an existing task
- **DELETE** `/api/task/{id}` - Delete a task
- **PUT** `/api/task/moveUp` - Move a task up in the order
- **PUT** `/api/task/moveDown` - Move a task down in the order

### Task Model

```json
{
  "id": 0,
  "title": "string",
  "dueDate": "2024-01-01T00:00:00Z",
  "isCompleted": false,
  "userId": "string",
  "orderIndex": 0
}
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please ensure your code follows the existing coding style and includes appropriate tests.

## License

This project is available for use under standard software development practices. Please contact the author for specific licensing terms.

## Author

**Pawel Dywan**

- GitHub: [@paweldywan](https://github.com/paweldywan)
- Website: [https://paweldywan.com/](https://paweldywan.com/)

## Acknowledgments

- ASP.NET Core team for the excellent framework and documentation
- React team for the powerful UI library
- Entity Framework Core team for the robust ORM
- The open-source community for the various libraries and tools used in this project
- Bootstrap team for the responsive CSS framework
- Vite team for the fast build tool
