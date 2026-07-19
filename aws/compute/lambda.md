AWS Lambda
What is Lambda?
AWS Lambda is a serverless compute service.
Instead of creating and managing a server, you upload your code and AWS runs it whenever it's needed.
________________________________________
Traditional way
Application

↓

EC2 Server

↓

Your code
You manage:
•	Server 
•	Updates 
•	Scaling 
•	Security patches 
________________________________________
Lambda
Application

↓

Lambda Function

↓

Your code
AWS manages:
•	Servers 
•	Scaling 
•	Availability 
•	Infrastructure 
You only focus on writing the code.
________________________________________
Example
Imagine someone uploads a profile picture.
Upload Image

↓

S3 Bucket

↓

Lambda

↓

Resize Image

↓

Save Thumbnail
The Lambda function runs automatically when the image is uploaded.
________________________________________
Another example
A user submits a contact form.
Website

↓

API Gateway

↓

Lambda

↓

Send Email
No server needs to be running continuously.
________________________________________
Supported languages
Lambda supports:
•	JavaScript (Node.js) 
•	TypeScript (compiled to JavaScript) 
•	Python 
•	Java 
•	C# 
•	Go 
•	Ruby 
________________________________________
Why companies use Lambda
•	No server management 
•	Automatic scaling 
•	Pay only when the function runs 
•	Ideal for event-driven workloads 
•	Easy integration with many AWS services 
________________________________________
Skills for Care example
Although the main ASC-WDS application uses a Node.js backend, Lambda could be used for background tasks such as:
•	Processing uploaded files 
•	Sending notification emails 
•	Running scheduled jobs 
•	Generating reports 
•	Integrating with other AWS services 
________________________________________
CloudFront vs Lambda
CloudFront	Lambda
Content Delivery Network (CDN)	Serverless compute service
Speeds up content delivery	Runs code without managing servers
Caches files globally	Executes functions in response to events
Used for websites, images, CSS, JS	Used for APIs, automation, image processing, notifications
Improves performance	Performs backend processing
________________________________________
Simple Interview Answers
What is AWS CloudFront?
"CloudFront is AWS's Content Delivery Network. It caches website content such as HTML, CSS, JavaScript, and images at edge locations around the world, so users receive content from the location nearest to them. This reduces latency, improves website performance, and decreases the load on the origin server."
What is AWS Lambda?
"AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers. You upload your function, configure a trigger—such as an API request or an S3 file upload—and AWS automatically executes and scales the function as needed. You only pay for the compute time your code actually uses."


