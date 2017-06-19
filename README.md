# Log Emailer
AMPscript based email template for sending records of a Data Extension to an audience

This email template can be used to easily display the records of in a tabular format.

This is primarily used Automations that sends a daily "Log" Data Extension to a recipient list, but can be adapted to any purpose

![alt text](https://raw.githubusercontent.com/ccarswell/log-emailer/master/screenshot.jpg)

## Installation in Salesforce Marketing Cloud 

1) Locate source Data Extension to use
2) Ensure this Data Extension has a "Date" type column (for ordering) and a "Constant" column. This Data Extension requires a numeric field with a default value of 1.  This allows retrieval of all records in the Data Extension. Example: ConstantForLog
3) Create an HTML based email and insert the main.html code
4) Update the following variables to suit your solution:

Variable Name | Description | Example Value
------------ | ------------- | -------------
@DEName = "" | Configure Data Extension name here (not External Key) | "JourneyLog"
@NumberOfRecords = 250 | Number of records to display in the email. Set to 0 to display up to 2000 max | 250
@DateField = "" | Date field to order by descending. | "SFMC_DateCreatedCST"
@ConstantField = "" | "Constant" field in Data Extension. | "ConstantForLog"
@Subject = "" | Email subjectline | CONCAT (@DEName," Log")
@TimeZoneModifier = 17 | All dates in the Data Extension are recorded in CST. Change this value to display results in your time zone. | 17 (Sydney, Australia)
@Logo = "" | Set a URL of your company logo here | <a href="https://upload.wikimedia.org/wikipedia/en/b/b6/Salesforce_Marketing_Cloud_Logo.png">Link</a>
@DEFieldDisplay1 = "" | Header row value for the column | "First Name"
@DELookupField1 = "" | Data Extension Field Name for the column | "FirstName"
@DEFieldDisplay2 = "" | Header row value for the column | "Last Name"
@DELookupField2 = "" | Data Extension Field Name for the column | "LastName"
@DEFieldDisplay3 = "" | Header row value for the column | "Email Address"
@DELookupField3 = "" | Data Extension Field Name for the column | "EmailAddress"
@AlertText = "" | The alert in the email for when no records have been found. | "NO RECORDS HAVE BEEN FOUND SINCE YESTERDAY!"

5) Set your Email Subject Line to %%=v(@SubjectLine)=%%
6) Send Preview
7) Use as part of a daily automation to send to a list of subscribers
