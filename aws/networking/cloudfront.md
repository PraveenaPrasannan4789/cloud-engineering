AWS CloudFront
What is CloudFront?
we all interact with cdns every day.
eg:instagram, if a person in Australia uploads an image,suppose  a central system, which manages the storage and access(without the cdn),the image to get accessed by the user, it has to send over multiple ports.Loading time is more. They use cdn for this.CDN creates the local copies of the image.Now instead of storing the images in the central location the image gets stored in the edge locations.
CloudFront is AWS's Content Delivery Network (CDN).
It makes websites load faster by caching content at locations around the world.
Without CloudFront
User (London)
      |
      |
AWS Server (Ireland)
Every request goes to the main server.
________________________________________
With CloudFront
User (London)
      |
      |
CloudFront Edge Location (London)
      |
      |
AWS Server (Ireland)
The first request goes to the server.
CloudFront stores (caches) the content.
The next user receives it from the nearby edge location, making the website much faster.
________________________________________
What can CloudFront cache?
•	Images 
•	CSS 
•	JavaScript 
•	Videos 
•	PDF files 
•	Static websites 
•	API responses (if configured) 
________________________________________
Example
Suppose your Angular application is hosted on an S3 bucket.
Angular App
      |
      |
S3 Bucket
If 10,000 users visit:
Every user downloads files from S3.
Instead, use:
Angular App
      |
CloudFront
      |
S3 Bucket
Now CloudFront serves cached copies, reducing latency and lowering the load on S3.
________________________________________
Why companies use CloudFront
•	Faster websites 
•	Lower latency 
•	Reduced load on backend servers 
•	Global content delivery 
•	HTTPS support 
•	DDoS protection (integrates with AWS Shield) 
If your company website is hosted on AWS:
User

↓

CloudFront

↓

S3 (Angular App)

↓

Node API

↓

PostgreSQL
Users download the frontend from CloudFront instead of directly from S3.
