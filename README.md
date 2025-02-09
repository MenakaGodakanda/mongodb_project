# MongoDB CRUD API with Node.js and Express

This project demonstrates a MongoDB-based REST API using Node.js and Express.js. The API allows users to Create, Read, Update, and Delete (CRUD) book records in a MongoDB database.

## Overview

<img width="1303" alt="Screenshot 2025-02-10 at 5 50 44 am" src="https://github.com/user-attachments/assets/059e3148-5647-457b-b5b5-0f90a4429268" />

### Flow Explanation:
- The Client sends HTTP requests (`GET`, `POST`, `PUT`, `DELETE`) using Postman or cURL.
- The Express.js Server receives and routes the requests.
- The Controller Layer (`bookController.js`) processes the business logic.
- The Routes Layer (`bookRoutes.js`) defines and maps the API endpoints.
- The MongoDB database (via Mongoose) stores and manages book records.

## Features
- Create a new book entry
- Retrieve all books
- Retrieve a book by ID
- Update book details
- Delete a book

## Tech Stack
- Ubuntu: Operating System
- MongoDB:  NoSQL Database
- Node.js: Backend Server
- Express.js: Web Framework
- Mongoose: MongoDB ODM
- Postman: API Testing

## Installation & Setup

### 1. Clone the Repository
```
git clone https://github.com/MenakaGodakanda/mongodb_project.git
cd mongodb_project
```

### 2. Install Dependencies
```
npm install
```

### 3. Set Up Environment Variables

Create a `.env` file in the root directory:
```
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/booksdb
```

### 4. Start MongoDB Service
```
sudo systemctl start mongod
```

### 5. Run the Server
```
npm start
```
- The server should be running at `http://localhost:5000`.
- You should see output similar to this:

## API Endpoints

### 1. Create a New Book (POST)

Endpoint: `POST /api/books`
```
curl -X POST http://localhost:5000/api/books \
     -H "Content-Type: application/json" \
     -d '{"title": "The Great Gatsby", "author": "F. Scott Fitzgerald", "pages": 180, "publishedYear": 1925}'
```

Response:


### 2. Retrieve All Books (GET)

Endpoint: `GET /api/books`
```
curl -X GET http://localhost:5000/api/books
```

Response:


### 3. Retrieve a Book by ID (GET)

Endpoint: `GET /api/books/:id`
```
curl -X GET http://localhost:5000/api/books/65b3f1e5f0a1a5c4b6d8e1a7
```

Response:


### 4. Update a Book (PUT)

Endpoint: `PUT /api/books/:id`
```
curl -X PUT http://localhost:5000/api/books/65b3f1e5f0a1a5c4b6d8e1a7 \
     -H "Content-Type: application/json" \
     -d '{"title": "The Great Gatsby", "author": "F. Scott Fitzgerald", "pages": 200, "publishedYear": 1925}'
```

Response:

### 5. Delete a Book (DELETE)

Endpoint: `DELETE /api/books/:id`
```
curl -X DELETE http://localhost:5000/api/books/65b3f1e5f0a1a5c4b6d8e1a7
```

Response:

### 5. Database View (MongoDB)
To see the stored books, run:
```
mongosh
use booksdb
db.books.find().pretty()
```
Example Output:


## Troubleshooting

- Check if MongoDB is running:
```
sudo systemctl status mongod
```

- Check logs for errors:
```
npm run dev
```
- Manually start MongoDB shell:
```
mongosh
```

## Project Structure
```
mongodb_project/
│── .env              # Environment variables
│── server.js         # Main entry point
│── package.json      # Node.js dependencies
│── models/
│   └── Book.js       # Mongoose schema
│── routes/
│   └── bookRoutes.js # API routes
│── config/
│   └── db.js         # Database connection
│── controllers/
│   └── bookController.js # CRUD logic
```

## License

This project is licensed under the MIT License.
