# BasicTodoList

A simple full-stack Todo List application built with ASP.NET Core (C#) for the backend and React (TypeScript) for the frontend.

## Features
- Add, edit, and delete tasks
- View all tasks in a table
- Backend API with Entity Framework Core
- Modern React frontend with Vite

## Project Structure

- `BasicTodoList.BLL/` - Business logic layer (C#)
- `BasicTodoList.DAL/` - Data access layer, Entity Framework Core, migrations, and seed data (C#)
- `BasicTodoList.Server/` - ASP.NET Core Web API server (C#)
- `basictodolist.client/` - React frontend (TypeScript, Vite)

## Getting Started

### Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [Node.js & npm](https://nodejs.org/)

### Backend Setup
1. Navigate to the solution root:
   ```sh
   cd BasicTodoList
   ```
2. Restore and build the solution:
   ```sh
   dotnet restore
   dotnet build
   ```
3. Apply database migrations:
   ```sh
   dotnet ef database update --project BasicTodoList.DAL --startup-project BasicTodoList.Server
   ```
4. Run the server:
   ```sh
   dotnet run --project BasicTodoList.Server
   ```

### Frontend Setup
1. Navigate to the client folder:
   ```sh
   cd basictodolist.client
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm run dev
   ```

The frontend will be available at [http://localhost:5173](http://localhost:5173) by default.

## API Endpoints
The backend exposes RESTful endpoints for managing tasks. See `TaskController.cs` for details.

## Demo
[Live Demo](https://basictodolist.paweldywan.com/)

## License
MIT
