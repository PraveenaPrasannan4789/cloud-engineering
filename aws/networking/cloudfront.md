### AWS CloudFront
What is CloudFront?
we all interact with cdns every day.
eg:instagram, if a person in Australia uploads an image,suppose  a central system, which manages the storage and access(without the cdn),the image to get accessed by the user, it has to send over multiple ports.Loading time is more. They use cdn for this.CDN creates the local copies of the image.Now instead of storing the images in the central location the image gets stored in the edge locations.
CloudFront is AWS's Content Delivery Network (CDN).(to reduce latency, security and cost)
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


### How does a purchased domain connect to CloudFront?

Your assumption:

"We get an IP address from S3 and point the domain to that IP"

This is the part that is not correct.

S3 does not give you a fixed IP address.

AWS services like S3 and CloudFront use dynamic infrastructure, so you do not map your domain to an S3 IP.

The actual flow is:

User
 |
 |
 types:
www.example.com
 |
 v
DNS (Route 53)
 |
 v
CloudFront Distribution
 |
 v
S3 Bucket
Complete AWS flow

Let's say you buy:

www.praveenawebsite.com

You create:

Step 1: Upload website to S3

Your bucket:

my-website-bucket

Contains:

index.html
style.css
app.js
images/
Step 2: Create CloudFront distribution

CloudFront gives you a domain:

d111111abcdef8.cloudfront.net

Your flow currently:

User
 |
 v
d111111abcdef8.cloudfront.net
 |
 v
S3 Bucket
Step 3: Buy your own domain

Example:

praveenawebsite.com

from:

Route 53
GoDaddy
Namecheap
etc.
Step 4: Point domain to CloudFront

In DNS you create a record:

www.praveenawebsite.com

        |
        v

d111111abcdef8.cloudfront.net

Usually using:

A Record (Alias)

or:

CNAME

depending on the setup.

Now the final architecture:

                 User
                   |
                   |
        www.praveenawebsite.com
                   |
                   |
              Route 53 DNS
                   |
                   |
          CloudFront Distribution
                   |
                   |
             S3 Origin Bucket
                   |
                   |
          Static Website Files
What happens when a user types your domain?

Example:

www.example.com
Step 1: DNS lookup

Browser asks:

"Where is www.example.com?"

DNS responds:

"Go to CloudFront."

Step 2: CloudFront receives request

CloudFront checks cache:

Do I have index.html?

If yes:

CloudFront Cache → User

If no:

CloudFront → S3 → CloudFront Cache → User
Where does the IP address come into this?

The browser ultimately connects using IP addresses, but you don't manage those IPs.

The process is:

Domain Name
      |
      v
DNS Resolution
      |
      v
CloudFront Edge IP (managed by AWS)
      |
      v
S3 Origin

AWS manages the IP changes behind the scenes.