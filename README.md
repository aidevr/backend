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



## Generating SBOM for the Current Application

To generate a Software Bill of Materials (SBOM) for this application using CycloneDX, follow these steps:

### Step 1: Validate `package.json`
Ensure the `package.json` file in the project is valid and does not contain unexpected or malformed fields. You can validate it using:
```bash
npm run validate
```

### Step 2: Install CycloneDX CLI
Install CycloneDX globally to ensure it is available for use:
```bash
npm install -g @cyclonedx/bom
```

### Step 3: Run CycloneDX in Debug Mode
If you encounter issues, enable debug mode to get more details:
```bash
DEBUG=cyclonedx-bom npx @cyclonedx/bom -o sbom.json
```

### Step 4: Check for Unsupported Fields
Inspect the `package.json` for custom or non-standard fields. Remove them temporarily to test if CycloneDX works.

### Step 5: Use a Minimal Project
If the issue persists, create a minimal `package.json` with only essential fields and dependencies:
```json
{
  "name": "todo-backend",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.2",
    "cors": "^2.8.5"
  }
}
```

### Step 6: Update CycloneDX
Ensure you are using the latest version of CycloneDX:
```bash
npm install -g @cyclonedx/cyclonedx-npm@latest
```

### Step 7: Generate SBOM
Once resolved, generate the SBOM for this application using:
```bash
npx cyclonedx-npm -o sbom.json
```

The generated `sbom.json` file will contain the Software Bill of Materials for the current application.