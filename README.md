## The BookCooper Repository

Our project is titled _The BookCooper - Virtual Book Exchange Platform_. Our team consists of Alex Liu (EE’25), Aidan Cusa (EE’26), and ~~Isaac Schertz (EE’26)~~. 

The project goal is to create a simple marketplace for book lovers, while not having to purchase a new book everytime and get no value for their old purchases. Here users have the ability to earn points for sending in undesired books, and then use points to purchase new ones. These points, called Book Bucks (B-Bucks for short) can also be purchased with real money. This Facebook-like online marketplace exchange is tailored made for all types of books. _The BookCooper_ will start small, being an exclusive marketplace for Cooper affiliated individuals, though will eventually reach to every book lover in the world!

## Steps
1. **Clone the Repository**
   ```bash
   git clone <repository-url>
    ```
2. Start the PostgreSQL server

    Make sure docker is installed and then run the following command:
   ```bash
   docker compose up --build
   ```
3. Connect to the PostgreSQL server using dbeaver or any other SQL client
    Information to connect to the database:
    ```bash
    Host: localhost
    Port: 5555
    Database: thebookcooper
    User: BCdev
    Password: password
    ```
    If it doesnt work double check that database is created:
    ```bash
    docker exec -it thebookcooper-db psql -U BCdev -l
    psql -h localhost -p 5555 -U BCdev -d thebookcooper


4. Go to postman and test the following API endpoints:

    # API Documentation

    This documentation provides a comprehensive guide to the API endpoints, categorized by resource classes. For easier navigation, use the hyperlinks below to jump to a specific class section.

    - [User Operations](#user-operations)
    - [Book Operations](#book-operations)
    - [Listing Operations](#listing-operations)
    - [Book Tag Operations](#book-tag-operations)

    ## User Operations

    ### Creating a New User

    - **POST** `http://localhost:8080/users/create`

    ```json
    {
        "userName": "test",
        "password": "password",
        "email": "test@gmail.com",
        "bBucksBalance": 1000.0
    }
    ```

    ### Updating a User

    - **PUT** `http://localhost:8080/users/update/{id}`

    ```json
    {
        "userName": "tester",
        "password": "passwords",
        "email": "tester@gmail.com",
        "bBucksBalance": 100000.0
    }
    ```

    ### Counting Users

    - **GET** `http://localhost:8080/users/count`

    ### Getting a User by ID

    - **GET** `http://localhost:8080/users/{id}`

    ### Deleting a User by ID

    - **DELETE** `http://localhost:8080/users/delete/{id}`

    Make sure that the `userId` is not in the `book_listings` table before deletion.

    ## Book Operations

    ### Creating a New Book

    - **POST** `http://localhost:8080/books/create`

    ```json
    {
        "title": "Everything you need to know about software engineering",
        "isbn": 12345678901,
        "publishDate": "2024-02-22",
        "author": "Chris Hong",
        "genre": "Amaaaazing",
        "bookCondition": "New",
        "price": 999.99
    }
    ```

    ### Updating a Book

    - **PUT** `http://localhost:8080/books/update/{id}`

    ```json
    {
        "title": "Everything you dont need to know about software engineering",
        "isbn": 11111111,
        "publishDate": "2020-02-20",
        "author": "Christopher Hong",
        "genre": "Cool",
        "bookCondition": "Old",
        "price": 999999.99
    }
    ```

    ### Counting Books

    - **GET** `http://localhost:8080/books/count`

    ### Getting a Book by ID

    - **GET** `http://localhost:8080/books/{id}`

    ### Deleting a Book by ID

    - **DELETE** `http://localhost:8080/books/delete/{id}`

    Make sure that the `bookId` is not in the `book_listings` table before deletion.

    ## Listing Operations

    ### Creating a New Listing

    - **POST** `http://localhost:8080/listings/create`

    ```json
    {
        "bookId": 1,
        "userId": 1,
        "listingStatus": "new"
    }
    ```

    ### Updating a Listing

    - **PUT** `http://localhost:8080/listings/update/{id}`

    ```json
    {
        "bookId": 2,
        "userId": 2,
        "listingStatus": "old"
    }
    ```

    ### Counting Listings

    - **GET** `http://localhost:8080/listings/count`

    ### Getting a Listing by ID

    - **GET** `http://localhost:8080/listings/{id}`

    ### Deleting a Listing by ID

    - **DELETE** `http://localhost:8080/listings/delete/{id}`

    ## Book Tag Operations

    ### Creating a New Book Tag

    - **POST** `http://localhost:8080/booktags/create`

    ```json
    {
        "tagName": "Science Fiction",
        "bookId": 1
    }
    ```

    ### Getting a Book Tag by ID

    - **GET** `http://localhost:8080/booktags/{id}`

    ### Getting Book Tags Count

    - **GET** `http://localhost:8080/booktags/count`

    ### Updating a Book Tag

    - **PUT** `http://localhost:8080/booktags/update/{id}`

    ```json
    {
        "tagName": "Fantasy",
        "bookId": 2
    }
    ```

    ### Deleting a Book Tag by ID

    - **DELETE** `http://localhost:8080/booktags/delete/{id}`

