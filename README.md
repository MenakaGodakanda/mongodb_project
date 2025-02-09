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
- **Ubuntu**: Operating System
- **MongoDB**:  NoSQL Database
- **Node.js**: Backend Server
- **Express.js**: Web Framework
- **Mongoose**: MongoDB ODM
- **Postman**: API Testing

## Installation

### 1. Install MongoDB
- Import MongoDB GPG Key
```
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-server-keyring.gpg
```

- Add the MongoDB repository
```
echo "deb [signed-by=/usr/share/keyrings/mongodb-server-keyring.gpg] http://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

- Update package lists and install MongoDB
```
sudo apt update
sudo apt install -y mongodb-org
```

- Start and Enable MongoDB
```
sudo systemctl start mongod
sudo systemctl enable mongod
```

### 2. Install Node.js and Required Packages
- Install Node.js and npm
```
sudo apt install -y nodejs npm
```

- Verify Installation
```
node -v
npm -v
```

## Setup Environment

### 1. Clone the Repository
```
git clone https://github.com/MenakaGodakanda/mongodb_project.git
cd mongodb_project
```

### 2. Initialize a Node.js project
```
npm init -y
```
![Screenshot 2025-02-10 063459](https://github.com/user-attachments/assets/3bf3b020-fc4c-4b69-9e62-50b784f52fc7)

### 3. Install Dependencies
```
npm install express mongoose dotenv cors
```
- **express** → For creating the server and handling API routes.
- **mongoose** → For interacting with the MongoDB database.
- **dotenv** → For loading environment variables (e.g., MongoDB connection string).
- **cors** → For handling Cross-Origin Resource Sharing (useful if frontend and backend are separate).


### 4. Set Up Environment Variables

Create a `.env` file in the root directory:
```
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/booksdb
```

### 3. Start MongoDB Service
```
sudo systemctl start mongod
```

### 4. Run the Server
```
npm start
```
- The server should be running at `http://localhost:5000`.
- You should see output similar to this:
![Screenshot 2025-02-10 051944](https://github.com/user-attachments/assets/1da30f88-51fe-42b8-b068-a89eb5448eb0)

## API Endpoints

### 1. Create a New Book (POST)

Endpoint: `POST /api/books`
```
curl -X POST http://localhost:5000/api/books \
     -H "Content-Type: application/json" \
     -d '{"title": "The Great Gatsby", "author": "F. Scott Fitzgerald", "pages": 180, "publishedYear": 1925}'
```

Response:
![Screenshot 2025-02-10 051224](https://github.com/user-attachments/assets/5cf4d2e5-6e05-40ad-b7c7-a4627c73b2dd)


### 2. Retrieve All Books (GET)

Endpoint: `GET /api/books`
```
curl -X GET http://localhost:5000/api/books
```

Response:
![Screenshot 2025-02-10 051233](https://github.com/user-attachments/assets/71853215-6729-4966-97cc-0bedb36bfe19)

![Screenshot 2025-02-10 051630](https://github.com/user-attachments/assets/f57497e8-d8cd-49b7-8db1-1ace101bbe8f)

### 3. Retrieve a Book by ID (GET)

Endpoint: `GET /api/books/:id`
```
curl -X GET http://localhost:5000/api/books/67a91aa24aae761b36478d94
```

Response:
![Screenshot 2025-02-10 061129](https://github.com/user-attachments/assets/f67527ea-e71c-46fe-8408-113a3572131b)


### 4. Update a Book (PUT)

Endpoint: `PUT /api/books/:id`
```
curl -X PUT http://localhost:5000/api/books/67a919454aae761b36478d8d \
     -H "Content-Type: application/json" \
     -d '{"title": "The Great Gatsby", "author": "F. Scott Fitzgerald", "pages": 200, "publishedYear": 1925}'
```

Response:
![Screenshot 2025-02-10 051817](https://github.com/user-attachments/assets/eeba9f66-1361-4f6b-8f07-a6f4dbf7c96e)

### 5. Delete a Book (DELETE)

Endpoint: `DELETE /api/books/:id`
```
curl -X DELETE http://localhost:5000/api/books/67a919454aae761b36478d8d
```

Response:
![Screenshot 2025-02-10 051901](https://github.com/user-attachments/assets/3138a735-af2e-4af6-925c-63e0eaca5bdd)

### 5. Database View (MongoDB)
To see the stored books, run:
```
mongosh
use booksdb
db.books.find().pretty()
```
Example Output:
![Screenshot 2025-02-10 052039](https://github.com/user-attachments/assets/d60b7684-f9f6-4be6-9b34-0b1cc27664c0)


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
