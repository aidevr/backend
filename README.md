# TODO App Backend

This is a simple Node.js backend for a TODO application. It provides RESTful APIs to manage todos (create, read, update, delete) using Express.js. Todos are stored in memory.

## Available Endpoints
- `GET /todos` - List all todos
- `POST /todos` - Create a new todo
- `PUT /todos/:id` - Update a todo
- `DELETE /todos/:id` - Delete a todo

## Getting Started
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the server:
   ```bash
   npm start
   ```

The server will run on `http://localhost:3000` by default.

## Running the Application

To run the application using Docker:

1. Build the Docker image:
   ```bash
   docker build -t node-app .
   ```

2. Run the container with the desired port (e.g., 4000):
   ```bash
   docker run -e PORT=4000 -p 4000:4000 node-app
   ```

The application will be accessible at `http://localhost:4000`.

## API Usage with `curl`

### 1. Get all todos
```bash
curl -X GET http://localhost:3000/todos
```

### 2. Create a new todo
```bash
curl -X POST http://localhost:3000/todos \
-H "Content-Type: application/json" \
-d '{"title": "New Todo", "completed": false}'
```

### 3. Update a todo
```bash
curl -X PUT http://localhost:3000/todos/1 \
-H "Content-Type: application/json" \
-d '{"title": "Updated Todo", "completed": true}'
```

### 4. Delete a todo
```bash
curl -X DELETE http://localhost:3000/todos/1
```
