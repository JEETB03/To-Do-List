

# To-Do List Application

This is a simple To-Do List application built using **Node.js**, **Express**, and **PostgreSQL**. It allows users to add, edit, and delete to-do items. The application connects to a PostgreSQL database to store and retrieve tasks, and displays them on a web page using **EJS** for templating.

## Features

- **Add tasks**: Users can add new tasks to the to-do list.
- **Edit tasks**: Users can update the title of existing tasks.
- **Delete tasks**: Users can delete tasks from the list.
- **Persistent storage**: Task data is stored in a PostgreSQL database.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Project Structure](#project-structure)
4. [Database Setup](#database-setup)
5. [API Endpoints](#api-endpoints)
6. [Technologies Used](#technologies-used)
7. [Contributing](#contributing)
8. [License](#license)

## Installation

### Prerequisites

- Node.js (v14 or higher)
- PostgreSQL (v12 or higher)

### Steps

1. **Clone the repository**:

   ```bash
   git clone https://github.com/JEETB03/To-Do-List.git
   cd todo-list-app
   ```

2. **Install dependencies**:

   Run the following command to install required Node.js dependencies.

   ```bash
   npm install
   ```

3. **Configure PostgreSQL**:

   Make sure PostgreSQL is installed and running on your machine. Update the `db` configuration in `index.js` with your PostgreSQL credentials.

4. **Run the server**:

   Start the Express server by running:

   ```bash
   npm start
   ```

   The app will be available at `http://localhost:3000`.

## Usage

Once the server is running, open a browser and go to `http://localhost:3000`. You'll see a simple to-do list where you can:

- Add a new task by typing in the input field and clicking **Add**.
- Edit an existing task by selecting the task, making your changes, and clicking **Update**.
- Delete a task by clicking the **Delete** button next to it.

All changes are stored in the PostgreSQL database and persist across sessions.

## Project Structure

```plaintext
├── public/                 # Static files (CSS, images)
├── views/                  # EJS templates for rendering HTML
│   └── index.ejs           # Main page template
├── index.js                # Main server file
├── package.json            # Project dependencies and scripts
└── README.md               # Project documentation
```

## Database Setup

1. Create a new PostgreSQL database called `To-Do List` (or any name of your choice):
   
   ```sql
   CREATE DATABASE "To-Do List";
   ```

2. Create the `items` table in the database to store tasks:
   
   ```sql
   CREATE TABLE items (
     id SERIAL PRIMARY KEY,
     title VARCHAR(255) NOT NULL
   );
   ```

3. Modify the PostgreSQL connection settings in `index.js` to match your local setup:

   ```javascript
   const db = new pg.Client({
     user: "your_postgres_username",
     host: "localhost",
     database: "To-Do List",
     password: "your_postgres_password",
     port: 5432,
   });
   ```

## API Endpoints

- `GET /` – Fetches and displays the list of to-do items.
- `POST /add` – Adds a new item to the to-do list.
  - Request body:
    - `newItem`: String (The title of the new item to be added).
- `POST /edit` – Updates an existing item.
  - Request body:
    - `updatedItemTitle`: String (The new title of the item).
    - `updatedItemId`: Integer (The ID of the item to be updated).
- `POST /delete` – Deletes an item from the to-do list.
  - Request body:
    - `deleteItemId`: Integer (The ID of the item to be deleted).

## Technologies Used

- **Node.js**: JavaScript runtime for the server-side.
- **Express.js**: Web framework for Node.js.
- **PostgreSQL**: Relational database for persistent storage.
- **EJS**: Templating engine for rendering dynamic HTML.
- **HTML/CSS**: Frontend for rendering the UI.

## Contributing

Contributions are welcome! If you’d like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch.
3. Make your changes.
4. Submit a pull request with a detailed description of your changes.


---

This `README.md` file provides a clear overview of the project, setup instructions, and detailed information on how to use the app. Feel free to modify it based on any additional features you add to the project!