# Book Search Engine
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![ExpressJS](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![Apollo-GraphQL](https://img.shields.io/badge/-ApolloGraphQL-311C87?style=for-the-badge&logo=apollo-graphql)
![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=for-the-badge&logo=heroku&logoColor=white)


[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://choosealicense.com/licenses/mit/)

## Description
A book search engine that allows users to find new books to read and save them to their book list.

![Screenshot of the Book Search Engine search page](./assets/images/book-search-sc.PNG)
![Screenshot of your books page](./assets/images/your-books-sc.PNG)

## Table of Contents
* [Link](#link)
* [Installation](#installation)
* [Usage](#usage)
* [Apollo Server](#apollo-server)
* [License](#license)
* [Questions](#questions)

## Link
[Click here](https://my-google-books-library101.herokuapp.com/) to go to the deployed application.

## Installation
To install the app on your machine for development:

1. Install [Node.js](https://nodejs.org/en/) and [MongoDB](https://www.mongodb.com/) if you haven't already.
2. Clone this repository onto your computer.
3. Navigate to the root of this repository on the command line.
4. Run `npm install` on the command line.

## Usage
1. Go to the deployed application at [https://my-google-books-library101.herokuapp.com/](https://my-google-books-library101.herokuapp.com/).
2. Enter a book title to search for books.
3. Click on 'Login/Signup' to login or create an account.
4. Once logged in, you can save books to your library.
5. Click on 'See Your Books' to view your saved books.
6. On the saved books page, click on the delete button to delete a book from your library.

## Apollo Server
Originally, this app utilized Express API routes to communicate with the database. This updated application has been refactored with Apollo and GraphQL to provide a cleaner way to access and update the MongoDB database.

### Queries
This app uses one query to render the user's saved books information. This query returns a `User` type.
```js
query {
    me {
        _id
        username
        bookCount
        savedBooks {
            bookId
            title
            authors
            description
            image
            link
        }
    }
}
```


## License
Licensed under the [MIT](https://choosealicense.com/licenses/mit/) license.

## Questions
- [GitHub](https://github.com/kg-phantom)