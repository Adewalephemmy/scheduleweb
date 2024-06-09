HOW TO RUN Web App
step1:  Create Database (databae name: scheduler) using MySql 
        Update the Application properties with the following: 
                1. Database name;
                2. Database password;
                3. Database username;
                4. Database url;

Step2:  Lunch the application
Step3: Insert the data into the database;
        user1: INSERT INTO ACCOUNT (account_number, balance)  VALUES(1234567890, 1000);
        user2  INSERT INTO ACCOUNT (account_number, balance)  VALUES(0987654321, 1000)

Step4: using postman to test the APIs (base url: http://localhost:8080/api) 
        1. TO TRASNFER : http://localhost:8080/api/transfer // TO POST using POSTMAN
            body   {
                    "fromAccountId": 1,
                    "toAccountId": 2,
                    "amount": 500.00
                    }

                    or 

                     {
                    "fromAccountId": 2,
                    "toAccountId": 1,
                    "amount": 500.00
                    }

        2.  REQUEST ALL TRANSACTION WITH DATE http://localhost:8080/api/transactions/summary?date=2024-06-09 // TO POST using POSTMAN OR WEB
            NOTE: Date can be changed to previous date or older date to view transaction.

        3.  REQUEST ALL TRANSACTION http://localhost:8080/api/transactions // GET ALL TRANSACTION HISTORY

        4.  Navigate to service package in the programe and locate ScheduleTasks class in the package, from the ScheduleTasks navigte down to the botton of the page and locate ScheduleDailyTask.
        There you can control when to run the cron task to run at the specified time of the day.
        cron = "0 57 14 * * ?" indicates (seconds(00), minutes(59), hours(23), days(7), days(weekly));