
#### Update Application Properties:

Modify the application.properties file with your database details:
properties

spring.datasource.url=jdbc:mysql://localhost:3306/scheduler
spring.datasource.username=your_database_username
spring.datasource.password=your_database_password


### Step 2: Launch the Application

#### Build and Run:
Use Maven or your preferred build tool to package and run the application:

mvn clean install
mvn spring-boot:run


### Step 3: Insert Initial Data
#### Insert Data:
Use the following SQL commands to insert initial data into the database:
sql

INSERT INTO ACCOUNT (account_number, balance) VALUES (1234567890, 1000);
INSERT INTO ACCOUNT (account_number, balance) VALUES (0987654321, 1000);


### Step 4: Test APIs using Postman
#### Base URL: [http://localhost:8080/api](http://localhost:8080/api)

##### Transfer Funds:
##### Endpoint:  [POST /api/transfer](/api/transfer)

Body:
jsonCopy code{
  "fromAccountId": 1,
  "toAccountId": 2,
  "amount": 500.00
}

or

jsonCopy code{
  "fromAccountId": 2,
  "toAccountId": 1,
  "amount": 500.00
}


#### Get Transactions by Date:
#### Endpoint: GET /api/transactions/summary
#### Query Parameter: date=YYYY-MM-DD
##### Example: http://localhost:8080/api/transactions/summary?date=2024-06-09
#### Get All Transactions:
##### Endpoint: GET /api/transactions
##### Example: http://localhost:8080/api/transactions

### Step 5: Configure Scheduled Tasks

#### Locate ScheduleTasks Class:
##### Navigate to the service package and locate the ScheduleTasks class.
##### Configure Cron Job:
Adjust the ScheduleDailyTask method at the bottom of the ScheduleTasks class to control the cron schedule.

##### Example Cron Expression: cron = "0 57 14 * *?" indicate (seconds(00), minutes(59), hours(23), days(7), days(weekly) order;
### Step 6: CI/CD Pipeline for Production

A YAML file is prepared to manage the CI/CD pipeline. Below is a brief overview of the pipeline steps:
#### Build Phase:

Build the codebase using Maven (or your specified build tool).
Install dependencies.
Create build artifacts.

#### Test Phase:

Execute unit tests.
Perform integration tests.
Run any additional relevant tests.

#### Deployment Phase:

Prepare the update for deployment upon successful build and tests.
Deploy the application to the production environment.
Conduct post-deployment checks to ensure smooth operation.