# To-Do App

A simple full-stack to-do application built with React (frontend) and Express.js (backend).

## Features

- Add new tasks
- View all pending tasks
- Delete tasks
- Responsive design

## Tech Stack

- **Frontend:** React.js, Axios
- **Backend:** Node.js, Express.js
- **Styling:** CSS

## Installation

1. Clone the repository:
   ```
   git clone <repository-url>
   cd to-do-app-main
   ```

2. Install backend dependencies:
   ```
   cd backend
   npm install
   ```

3. Install frontend dependencies:
   ```
   cd ../frontend
   npm install
   ```

## Usage

1. Start the backend server:
   ```
   cd backend
   node index.js
   ```
   The backend will run on http://localhost:4000

2. Start the frontend development server:
   ```
   cd frontend
   npm start
   ```
   The frontend will run on http://localhost:3000

3. Open your browser and navigate to http://localhost:3000 to use the app.

## API Endpoints

- `GET /tasks` - Retrieve all tasks
- `POST /tasks` - Add a new task (body: { task_id, task_name })
- `DELETE /tasks/:id` - Delete a task by ID

## Project Structure

```
to-do-app-main/
├── backend/
│   ├── index.js
│   ├── package.json
│   └── build/ (static files)
├── frontend/
│   ├── src/
│   │   ├── App.js
│   │   ├── App.css
│   │   └── apis.js
│   ├── public/
│   └── package.json
└── README.md
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## License

This project is licensed under the ISC License.
