# Book Search Engine
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![ExpressJS](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![Apollo-GraphQL](https://img.shields.io/badge/-ApolloGraphQL-311C87?style=for-the-badge&logo=apollo-graphql)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)
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
* [JWT Tokens](#jwt-tokens)
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
5. Run `npm run develop` to start the server and react app.

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

### Mutations
Multiple mutations are used in order to update the database.

- `LOGIN_USER`:
```js
mutation login($email: String!, $password: String!) {
        login(email: $email, password: $password) {
            token
            user {
                _id
                username
                email
            }
        }
    }
```

- `ADD_USER`:
```js
mutation addUser($username: String!, $email: String!, $password: String!) {
        addUser(username: $username, email: $email, password: $password) {
            token
            user {
                _id
                username
                email
            }
        }
    }
```

- `SAVE_BOOK`:
```js
mutation saveBook($details: BookDetails!) {
        saveBook(details: $details) {
            _id
            username
            email
            bookCount
            savedBooks {
                bookId
                title
                description
                authors
                link
            }
        }
    }
```

- `REMOVE_BOOK`:
```js
mutation removeBook($bookId: String!) {
        removeBook(bookId: $bookId) {
            _id
            username
            bookCount
            savedBooks {
                bookId
                title
                authors
            }
        }
    }
```

### Resolvers
The resolvers in `resolvers.js` interact with the database in order for the mutations to take effect. Each resolver excluding `addUser` and `login` takes in `context` as a parameter to decode the JWT token to ensure authorization before performing the mutation.

## JWT Tokens
This application uses JWT Tokens to create/login users as well as verify that actions like saving books are authorized. Tokens are signed after a new user is created or en existing user logs in. 

The token is saved to `localStorage`, so it can be found and decoded when authorization is required.

## License
Licensed under the [MIT](https://choosealicense.com/licenses/mit/) license.

## Questions
- [GitHub](https://github.com/kg-phantom)