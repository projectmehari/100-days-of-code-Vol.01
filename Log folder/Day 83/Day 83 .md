# Day 83

Tags: Backend development
Date: October 5, 2023
Status: Done

**Review of Backend essentials**

Tasks of the day

- Node.js
- PostgreSQL

Exercises

- Cli Apps
- Simple CRUD

---

### Node.js

Node.js is an open-source and cross-platform JavaScript runtime environment. It is a popular tool for almost any kind of project! Node.js runs the V8 JavaScript engine, Google Chrome’s core, outside the browser. This allows Node.js to be very performant. A Node.js app runs in a single process, without creating a new thread for every request. Node.js provides a set of asynchronous I/O primitives in its standard library that prevent JavaScript code from blocking and generally, libraries in Node.js are written using non-blocking paradigms, making blocking behavior the exception rather than the norm.

**Why Node.js**

A common task for a web server can be to open a file on the server and return the content to the client.

Here is how PHP or ASP handles a file request:

1. Sends the task to the computer's file system.
2. Waits while the file system opens and reads the file.
3. Returns the content to the client.
4. Ready to handle the next request.

Here is how Node.js handles a file request:

1. Sends the task to the computer's file system.
2. Ready to handle the next request.
3. When the file system has opened and read the file, the server returns the content to the client.

Node.js eliminates the waiting, and simply continues with the next request.

Node.js runs single-threaded, non-blocking, asynchronous programming, which is very memory efficient.

**What can Node.js do?**

- Node.js can generate dynamic page content
- Node.js can create, open, read, write, delete, and close files on the server
- Node.js can collect form data
- Node.js can add, delete, modify data in your database

**What is a Node.js file?**

- Node.js files contain tasks that will be executed on certain events
- A typical event is someone trying to access a port on the server
- Node.js files must be initiated on the server before having any effect
- Node.js files have extension ".js"

Visit the following resources to learn more:

- **[Official Website](https://nodejs.org/en/about/)**
- **[Learn Node.js Official Website](https://nodejs.dev/en/learn/)**
- **[Node.JS Introduction](https://www.w3schools.com/nodejs/nodejs_intro.asp)**
- **[Node.js and Express.js Full Course](https://www.youtube.com/watch?v=Oe421EPjeBE)**

---

### [PostgreSQL](https://www.postgresql.org)

PostgreSQL, also known as Postgres, is a free and open-source relational database management system emphasizing extensibility and SQL compliance.

---

### CLI app exercise #1

Create a CLI application that takes a URL and a CSS selector arguments and prints the text content of the element that matches the selector. **Hint** you can use **[cheerio](https://github.com/cheeriojs/cheerio)**

1. **Set Up Your Development Environment:**
    
    Make sure you have Node.js and npm (Node Package Manager) installed on your system. You can download them from the official Node.js website: [https://nodejs.org/](https://nodejs.org/)
    

1. **Initialize Your Project:**
    
    Create a new directory for your project and navigate to it in the terminal. Then, initialize a new Node.js project by running the following command:
    
    ```bash
    npm init -y
    ```
    

1. **Install Cheerio:**
    
    Install the Cheerio library by running the following command in your project directory:
    
    ```bash
    npm install cheerio
    ```
    
2. **Create Your CLI Script:**
    
    Create a JavaScript file (e.g., **`cli_app.js`**) with the following code:
    
    ```jsx
    const axios = require('axios');
    const cheerio = require('cheerio');
    const readline = require('readline');
    
    // Create an interface for reading user input from the command line
    const rl = readline.createInterface({
      input: process.stdin,
      output: process.stdout,
    });
    
    rl.question('Enter the URL: ', async (url) => {
      try {
        // Send an HTTP GET request to the specified URL
        const response = await axios.get(url);
    
        // Load the HTML content into Cheerio
        const $ = cheerio.load(response.data);
    
        rl.question('Enter the CSS selector: ', (selector) => {
          // Find the element that matches the CSS selector
          const selectedElement = $(selector);
    
          if (selectedElement.length > 0) {
            // Extract and print the text content of the selected element
            console.log(selectedElement.text());
          } else {
            console.log('Element not found with the provided CSS selector.');
          }
    
          rl.close();
        });
      } catch (error) {
        console.error(`Error: ${error.message}`);
        rl.close();
      }
    });
    ```
    
3. **Run the CLI Application:**
    
    Open your terminal and navigate to the directory where you saved **`cli_app.js`**. Then, run the script using Node.js:
    
    ```bash
    node cli_app.js
    ```
    
    The application will prompt you to enter the URL of the web page you want to extract text from and then the CSS selector to target the desired element.
    For example:
    
    ```mathematica
    Enter the URL: https://example.com
    Enter the CSS selector: .main-content p
    ```
    

---

### CLI application #2

Creating an application that fetches and prints the most starred GitHub projects within a specified date range requires several steps. You'll need to use GitHub's search API and a programming language like Python for this task. Here's a step-by-step guide:

1. **Set Up Your Development Environment**:
- Install Python if you haven't already: [https://www.python.org/downloads/](https://www.python.org/downloads/)
- Choose a code editor or IDE (Integrated Development Environment) like Visual Studio Code, PyCharm, or Jupyter Notebook.
1. **Create a GitHub Personal Access Token**:
- Go to your GitHub account settings: [https://github.com/settings/tokens](https://github.com/settings/tokens)
- Generate a personal access token with the "public_repo" scope. This token will be used for authentication when making API requests. Keep it secure.

1. **Install Required Libraries**:
- You'll need to use the **`requests`** library to interact with the GitHub API. Install it using pip:
    
    ```bash
    pip install requests
    ```
    

1. **Write the Python code:**
    
    Here's a sample Python script that fetches the most starred GitHub projects in a given date range:
    
    ```bash
    import requests
    from datetime import datetime
    
    def get_most_starred_projects(start_date, end_date):
        # Convert dates to ISO 8601 format
        start_date_str = start_date.strftime("%Y-%m-%dT%H:%M:%SZ")
        end_date_str = end_date.strftime("%Y-%m-%dT%H:%M:%SZ")
    
        # Create a search query for GitHub API
        query = f'stars:>=1 created:{start_date_str}..{end_date_str}'
    
        # Define the GitHub API URL
        url = 'https://api.github.com/search/repositories'
        params = {
            'q': query,
            'sort': 'stars',
            'order': 'desc'
        }
    
        # Set up authentication with your GitHub Personal Access Token
        headers = {
            'Authorization': 'Bearer YOUR_PERSONAL_ACCESS_TOKEN'
        }
    
        # Make the API request
        response = requests.get(url, params=params, headers=headers)
    
        if response.status_code == 200:
            data = response.json()
            return data.get('items', [])
        else:
            print(f"Error: {response.status_code}")
            return []
    
    if __name__ == "__main__":
        start_date = datetime(2023, 1, 1)  # Replace with your desired start date
        end_date = datetime(2023, 12, 31)  # Replace with your desired end date
    
        most_starred_projects = get_most_starred_projects(start_date, end_date)
    
        print("Most Starred GitHub Projects in the Date Range:")
        for index, project in enumerate(most_starred_projects, start=1):
            print(f"{index}. {project['name']} - {project['stargazers_count']} stars")
    ```
    
    Make sure to replace **`'YOUR_PERSONAL_ACCESS_TOKEN'`** with the access token you generated in step 2, and adjust the **`start_date`** and **`end_date`** to your desired date range.
    
2. **Run the application:** Execute the Python script in your chosen development environment.
3. **View the Results:** The script will fetch and print the most starred Github projects within the specified date range.

---

### CLI application #3

Creating a CLI application to bulk rename files in a directory using Node.js is a great idea. You can use the **`fs`** and **`path`** modules for file system operations and path manipulation. Here's a simple example of such an application:

```jsx
#!/usr/bin/env node
const fs = require('fs');
const path = require('path');
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

function bulkRenameFiles(directory, oldPattern, newPattern) {
  fs.readdir(directory, (err, files) => {
    if (err) {
      console.error(`Error reading directory: ${err}`);
      rl.close();
      return;
    }

    files.forEach((file) => {
      const oldFilePath = path.join(directory, file);
      const newFilePath = path.join(directory, file.replace(oldPattern, newPattern));

      fs.rename(oldFilePath, newFilePath, (err) => {
        if (err) {
          console.error(`Error renaming file ${file}: ${err}`);
        } else {
          console.log(`Renamed ${file} to ${path.basename(newFilePath)}`);
        }
      });
    });

    rl.close();
  });
}

rl.question('Enter the directory path: ', (directory) => {
  rl.question('Enter the old pattern to replace: ', (oldPattern) => {
    rl.question('Enter the new pattern: ', (newPattern) => {
      bulkRenameFiles(directory, oldPattern, newPattern);
    });
  });
});
```

Save this code to a file (e.g., **`bulk-rename.js`**), and make it executable by running **`chmod +x bulk-rename.js`**. Then, you can use it from the command line like this:

```bash
./bulk-rename.js
```

This script will ask you for the directory path, old pattern to replace, and the new pattern. It will then rename all files in the specified directory that match the old pattern with the new pattern.

---

### CRUD

**CRUD** stands for **Create, Read, Update, and Delete**. These are the four basic operations you can perform on any data when working with web applications, databases, and APIs.

Now that you know about programming language and the databases, you should be able to build a simple CLI application that interacts with database. We haven’t talked about the APIs yet but you don’t need an API to practice CRUD operations. Here are some of the CLI applications you can build to practice CRUD operations:

A simple todo list application for the CLI with the following options:

- `-new` to add a new todo item
- `-list [all|pending|done]` to list the todo items
- `-done [id]` to update a todo item
- `-delete [id]` to delete a todo item
- `-help` to list all the available options
- `-version` to print the version of the application

Creating a simple CLI todo list application that interacts with a database involves several steps. In this example, we'll use Python and SQLite for the database operations. Here's a step-by-step guide to building such an application:

1. Set up the project structure:

```
todo_app/
│   todo.py
│   database.db
```

1. Install the required Python libraries (if not already installed):

```bash
pip install click
```

1. Create the **`todo.py`** script:

```python
import click
import sqlite3
from tabulate import tabulate

# Database setup
conn = sqlite3.connect('database.db')
cursor = conn.cursor()

# Create the 'todos' table if it doesn't exist
cursor.execute('''
    CREATE TABLE IF NOT EXISTS todos (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        task TEXT,
        status TEXT
    )
''')
conn.commit()

@click.group()
def cli():
    pass

@click.command()
@click.argument('task')
def new(task):
    """
    Add a new todo item.
    """
    cursor.execute("INSERT INTO todos (task, status) VALUES (?, ?)", (task, 'pending'))
    conn.commit()
    click.echo(f"Added task: {task}")

@click.command()
@click.option('--filter', type=click.Choice(['all', 'pending', 'done']), default='all')
def list(filter):
    """
    List todo items.
    """
    if filter == 'all':
        cursor.execute("SELECT * FROM todos")
    else:
        cursor.execute("SELECT * FROM todos WHERE status=?", (filter,))
    
    todos = cursor.fetchall()
    if not todos:
        click.echo("No todo items found.")
    else:
        headers = ["ID", "Task", "Status"]
        click.echo(tabulate(todos, headers, tablefmt="grid"))

@click.command()
@click.argument('id', type=int)
def done(id):
    """
    Mark a todo item as done.
    """
    cursor.execute("UPDATE todos SET status='done' WHERE id=?", (id,))
    conn.commit()
    click.echo(f"Marked task {id} as done.")

@click.command()
@click.argument('id', type=int)
def delete(id):
    """
    Delete a todo item.
    """
    cursor.execute("DELETE FROM todos WHERE id=?", (id,))
    conn.commit()
    click.echo(f"Deleted task {id}.")

@click.command()
def help():
    """
    List all available options.
    """
    click.echo(cli.get_help())

@click.command()
def version():
    """
    Print the version of the application.
    """
    click.echo("Todo App v1.0")

# Add commands to the CLI
cli.add_command(new)
cli.add_command(list)
cli.add_command(done)
cli.add_command(delete)
cli.add_command(help)
cli.add_command(version)

if __name__ == '__main__':
    cli()
```

1. Make the script executable

```bash
chmod +x todo.py
```

Now, you can use the CLI application as follows:

- Add a new todo item:

```bash
./todo.py new "Buy groceries"
```

- List todo items:

```bash
./todo.py list all
```

- Mark a todo item as done:

```bash
./todo.py done 1
```

- Delete a todo item:

```bash
./todo.py delete 1
```

- List of all available options

```bash
./todo.py help
```

- Print the version of the application:

```bash
./todo.py version
```

This simple CLI todo list application allows you to perform CRUD operations on your todo items using the command line interface.