# Course Management System

A complete solution for managing courses and lessons, built with .NET 9 (backend) and React + Bootstrap (frontend).

## Architecture

- **Backend**: Clean Architecture / DDD (Domain, Infrastructure, Application, API)
- **Frontend**: Single Page Application (Vite + React)
- **Database**: MySQL with Entity Framework Core
- **Authentication**: JWT with ASP.NET Core Identity

## Prerequisites

- .NET 9.0 SDK
- Node.js (v18+)
- MySQL Server

## Setup Instructions

### 1. Database Configuration

1. Ensure MySQL is running.
2. Update the connection string in `CourseManagement.API/appsettings.json` if your credentials differ from the default:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=localhost;Database=CourseManagementDB;User=root;Password=root;"
   }
   ```

### 2. Backend Setup

1. Navigate to the API project:
   ```bash
   cd CourseManagement.API
   ```
2. Apply database migrations, if change of database (this will create the DB and seed data):
   ```bash
   dotnet ef migrations add InitialIdentity \--project ../CourseManagement.Infrastructure \--startup-project .
   dotnet ef database update \--project ../CourseManagement.Infrastructure \--startup-project .
   ```
3. Run the API:
   ```bash
   dotnet run
   ```
   The API will start on `http://localhost:5068`.
   Swagger UI is available at `http://localhost:5068/swagger`.

### 3. Frontend Setup

1. Navigate to the frontend project:
   ```bash
   cd client-app
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm run dev
   ```
   The application will be available at `http://localhost:5173` (or the port shown in terminal).

## Test Credentials

A default user is seeded automatically:

- **Email**: `test@example.com`
- **Password**: `Test123!`

## Running Tests

To run the backend unit tests:

```bash
cd CourseManagement.Tests
dotnet test
```

## Features

- **Authentication**: Login/Register with JWT.
- **Courses**: Create, Edit, Delete (Soft), Publish/Unpublish, Search, Filter.
- **Lessons**: Create, Edit, Delete (Soft), Reorder.
- **Business Rules**:
  - Cannot publish empty course.
  - Unique lesson order validation.
  - Soft delete implementation.
