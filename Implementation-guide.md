Serverless REST API

OBJECTIVE:
Create a REST API using DynamoDB, Lambda & API gateway
Benefits: You can expose a REST API to your applications (whether they are hosted in a traditional manner or in a completely serverless environment). Customers/Clients can access this REST API and consume data via their own application logic.

![alt text](https://github.com/tinkrbay/serverless-rest-api/blob/master/Serverless-API-Lab.png)

Create a new S3 bucket in North Virginia

Name this bucket as myrestapi-XXXXXX-lab, where XXXXXX are your initials

Download the function.zip file from the below URL. This function.zip is the lambda code packaged with all dependent packages that need to be presented with the lambda code.

https://s3.amazonaws.com/labs.thecloudgarage.com/serverless-rest-api/function.zip

Upload this function.zip file into myrestapi-XXXXXX-lab bucket

Download the template.yaml file from the below URL. This is the main CloudFormation template that will create the DynamoDB table, Lambda function & the API gateway. The CloudFormation template while creating the Lambda function will download the function.zip to extract the required code/packages for the Lambda creation.

https://s3.amazonaws.com/labs.thecloudgarage.com/serverless-rest-api/template.yaml

Edit the template (preferably with notepad++) Replace only the bucket name on line number 19 & 46
Save the file and close

NOTE::::: ONLY IF YOU DO NOT HAVE NOTEPAD++:::::::::::::::::::::::::::::::::::::::::::::::::::::::::

If you do not have a notepad++ then you have to carefully execute a find/replace with usual notepad

Be careful YAML is extremely sensitive to formatting

Open the YAML file with notepad (DON'T CHANGE ANYTHING., THE FORMATTING LOOKS WEIRD BUT IGNORE THAT)

Simply click on "edit" and "replace"

In the Find What type
replacewithyourbucketname

In the Replace With type ((PLEASE NOTE XXXXX is your firstnamelastname)
myrestapi-XXXXXX-lab 

And then click on save

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

Next go to CloudFormation services in North Virginia and create a new stack.

Upload the template.yaml and name the stack as myrestapi

Click on the acknowledge boxes and also the create change set actions along with execute

Thereafter create the stack

Go to the management console in North Virginia. Services > CloudFormation > Select the myrestapilab stack > outputs
You will see an output URL, which is created by the CloudFormation template. This output represents endpoint for the API gateway
Copy that URL and save it somewhere!
Go to services > DynamoDB
Select the table myrestapi. You can see a blank table with an option to add items
An item is nothing but a JSON documented stored as an array of fields. It appears as a row entry., however in reality the entire row for a item is a JSON array document.
Click on Items and add items.
You can now add fields to this item
First start by adding the value = 00001 for the primary key, i.e. Product ID.
Add the following fields by clicking on + and append

Field name	Type	  Value
Company    	String	ABC-1
Brand	      String	XYZ-1
Price	      String	10

And save

Select the item and actions "duplicate item"... Change the value of ProductID to 002 and other attributes can be randomly changed

Likewise create 4 to 5 items (keep appending the ProductID to 003, 004, 005 and so on)

Pass the API URL to your consumers who can connect and retrieve this data from your DynamoDB tables using API gateway and Lambda



