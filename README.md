# My-Classroom-Backend

## Setting Up

### Requirements

- node: 16.13.0
- npm: 9.1.2

### Configuring Local Database

This process can and should be followed for instantiating both the local development and local testing database.

Install MySQL (and MySQL Workbench recommended): https://dev.mysql.com/doc/mysql-getting-started/en/
Pay attention to setting of the root user password, and take note of what is necessary.

In the Command Line:
1. MySQL as root user: `mysql -u root -p`
2. Create a User: `CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';`
3. Create a Table: `CREATE DATABASE 'database_name';`
4. Grant Permissions: `GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';`
5. Check Success: `SHOW DATABASES;`

If having issues, refer to the MySQL Getting Started Guide: https://dev.mysql.com/doc/mysql-getting-started/en/

If you need to reset your local dev or test databases, login to MySQL as the root user (step 1), and run `DROP DATABASE database_name;`. Then, rerun steps 3 and 4. 

### Configuring Local Environment

Copy the `.env.example` file into a `.env` file

Configure the database environment variables to match the database name, user, and password used when setting up the databases for development and test

## Starting the Application

`npm run start`

## Testing the Application

Testing the application is easy. The Jest testing framework is used to write tests for the system. A script has been added to the package.json file to run tests locally:

`npm run test`

If you run into issues, ensure you have done the following:

1. Created a local test database
2. Properly instantiated all env variables for the test environment

## Configuring Services

### Emailer

The application is configured to use Courier notification infastructure to message users. In order to use the application's mailer, create an account at https://www.courier.com/. Follow Courier's setup instructions and prompts.

The process should yield a bearer token in the HTTPS request Courier generates. Copy this token, and paste it in the application environment as `COURIER_AUTH_TOKEN`. That's it! You should be able to interact with the configured emailer through Courier.

It's worth noting that the application is only configured for email use through Courier, but Courier supports a variety of modern notification methods.