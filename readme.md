We are going build a Library Management App from Scratch!!

Here are the first **user actions** of our app:

** Core Features **

[ ] As a librarian, I can add a new book
[ ] As a librarian, I can list all the books, sorted by author
[ ] As a librarian, I can mark a book as loaned
[ ] As a librarian, I can see all loaned books that are overdue
[ ] As a librarian, I can list all the book loans
[ ] As a librarian, I can mark a loaned book as returned


**Things to Consider**

The application is designed for **a single library**, so no need to build for a multi-library one (e.g. we don't need a `Library` model).

Let's think through the core model of our library app, the book

## Book Model

A library is pretty much useless without books, so we need a way to represent what a book is and how it should behave.

Data & Behavior
---------------
Each book should have:
-an id,
-a name
-an author.

The book model should also:

- let us know about whether if it's loaned or not
- When loaned, it should have a return date
- When loaned, we should be able to check if the
loan is overdue (the return date is before the current date)

### 1.2 - Book Repository

Now that we have a model representing our books, we need a repository to store them.

This repository is initialized with a CSV file path. It reads/writes the meals from the CSV file and holds them as objects in an array. The behavior we want for the repository is to:

- Add a new book
- Get all the books
- Get all the books that are loaned
- Get all the book that are loaned and overdue
- Mark a book as loaned
- Mark a book as returned (which means is no longer loaned)
- Find a specific book thanks to its id

Write some code to implement this and crash-test your repository. You should create your own `books.csv` CSV file inside a `data`folder.

### 1.3 - Router and App

As you know from previous exercises, we need a router and we need to fill in the `app.rb` file.

The router is responsible for displaying the tasks that the librarian can do and routing the user's choice to the corresponding action of the matching controller.

The `app.rb` file is responsible for requiring all the necessary files, instanciating a router and executing its `run` method to launch the app.

Fill in the `router.rb` and `app.rb` files to implement this. If you're stuck, you can go back to the solutions of the cookbook and the food delivery app, download the solution to get some inspiration.


### 1.4 - Book Controller

Let's move to the controller. Let's go back to the features
we want to implement, and break down everything the
controller needs to do in small steps

### As a librarian, I can add a new book

The controller should..
- tell the view to get the information needed for
a new book from the user
- instantiate a new book
- tell the repository to add the newly instantiated book



### As a librarian, I can list all the books, sorted by author
The controller should..
- tell the repository to grab all books
- Sort them by the author
- send them to the view to be displayed

### As a librarian, I can mark a book as loaned
The controller should..
- Tell the view to display all books that are not loaned
- Tell the view to ask the user to select a book index
- Use that index to tell the repository which book should
be marked as loaned. The repository should update its csv
after the book has been marked

### As a librarian, I can see all loaned books that are overdue
The controller should..
- Tell the repository to fetch all books that are loaned
and which loan date is overdue
- Tell the view to display all the books the repository sent

Remember that the role of the controller is to delegate and coordinate the work to the other components of our app (model, repository and view)!


## 3 - Optional Features

- As a librarian, I can log in to the app

- If you are comfortable with CSV already, try making the
repositories speak SQL. You need to set up a database with a
books table instead of a books.csv. Also, think about
the new dependencies that you need

## 4 - Advanced features

Only spend time on this if you are very comfortable with OOP and
database design already!

### As a librarian, I can write a recommendation about a book.

( Note: a book could have many recommendations, written by
different librarians - Therefore, a recommendation is a
separate class in its own right )

### As a librarian, I can extend a loan.

Things to think about for this one:
* How do you capture the new return date?
* How do you make sure the new return date given by the
librarian is valid?
* How do you make sure the new return date is an extension,
and the librarian cannot shorten the time period of the loan?
* Once the date is valid, do other fields in the model
get impacted?

### As a librarian, I can create reading lists.

A reading list would:
- Have a topic
- Have a few books inside

- A reading list has many books
- At the same time, a given book could be in many
reading lists
- The relationship is many to many (N:N),
how could you model that in your database and
repositories?




