#### 👋 About Me
Hi, I’m Nikhitha Mara , an aspiring DevOps Engineer passionate about learning AWS and deploying projects to build real-world DevOps skills. I’m actively working on hands-on projects and sharpening my knowledge to break into DevOps roles. This repo documents my learning journey and showcases projects focused on cloud infrastructure, automation, CI/CD, and monitoring.

#### 🧠 Why I Chose This Project
In today's world, almost every company from brands like Nike to platforms like Amazon has an online store to sell products. This makes building an eCommerce application a common and highly relevant real-world scenario. This project gave me hands-on exposure to:

Containerizing multiple microservices written in different progarmming languagues using Docker
Managing communication between services via API calls
Implementing a reverse proxy (Envoy) to route and validate requests before they reach backend services
Using load generation tools to simulate real-world traffic
Applying CI/CD pipelines, monitoring, and infrastructure automation
This project reflects a full DevOps workflow applied to a real-world system, helping me strengthen my practical skills in deployment, scalability, and infrastructure management.

#### 🛒 Project Overview
I chose the E-Commerce Demo Project open-sourced by OpenTelemetry, which simulates an online store selling astronomy products like telescopes. 
This project is built using a microservices architecture, with each service implemented in a different language or framework so devopsifying this
project gives me handson on different devops tools used in real world projects. Below is a list of the microservices and their descriptions:

#### 🧩 Microservices Overview
| Microservice        | Language     | Description                                                  |
|---------------------|--------------|--------------------------------------------------------------|
| frontend            | TypeScript   | Serves the website via HTTP. Automatically generates session IDs. |
| product-catalog     | Go           | Lists/searches products from a JSON file.                    |
| cart                | .NET         | Stores and retrieves shopping cart data using Valkey.        |
| shipping            | Rust         | Estimates shipping cost based on the cart and address.       |
| quote               | PHP          | Calculates shipping based on item count.                     |
| checkout            | Go           | Handles full order flow: cart, payment, shipping, email.     |
| currency            | C++          | Converts between currencies using ECB rates. High QPS.       |
| payment             | JavaScript   | Mocks credit card transactions.                              |
| email               | Ruby         | Sends order confirmation emails.                             |
| ad                  | Java         | Displays contextual ads.                                     |
| recommendation      | Python       | Suggests products based on the cart.                         |
| accounting          | .NET         | Aggregates order values.                                     |
| load-generator      | Python       | Simulates user shopping flows for testing.                   |
| react-native-app    | TypeScript   | Mobile UI for shopping services.                             |


#### 🏗️ Project Architecture

<img width="584" height="392" alt="image" src="https://github.com/user-attachments/assets/5b4f5891-02b8-4075-b250-2de56ef04e54" />

#### 🌐 Application Flow:
Requests from the internet first hit a reverse proxy (server-side), which Validates traffic, Load balances requests and Routes them to the frontend service
The frontend serves the UI and communicates with backend microservices over HTTP/gRPC protocold
Microservices handle specific business logic like Cart, Shipping, Payment, Product Catalog, Email, etc.
A load generator simulates user traffic for testing and observability.
A React Native mobile app interacts with the backend via the same APIs.

#### 🚀 Dockerfile Creation Approach
This project contains multiple microservices organized within a single GitHub repository, with each microservice in its own folder.
* 📖 Reviewed the documentation in each microservice’s folder to understand how to build and run the service.
* 🖥️ Initially built and ran each microservice on an EC2 instance to verify functionality.
* 🛠️ Since the microservices are developed using different languages Java, Python, and Go. I created customized Dockerfiles for each service based on their specific requirements.
* This approach ensured all microservices are properly containerized and run smoothly in their respective environments.

#### 🎨 Design Questions I Got When I Started

#### 🤔 Why choose microservice architecture over monolithic?
Scalability: Microservices allow independent scaling of components based on demand, unlike monoliths which scale as a whole.
Flexibility: Different services can use different technologies best suited for their tasks.
Faster Deployment: Smaller, focused teams can develop, test, and deploy services independently, speeding up release cycles.
Fault Isolation: Failures in one microservice don’t necessarily bring down the entire system.

#### ⚖️ Can’t I use a load balancer instead of a reverse proxy?
Load balancer distributes incoming traffic across multiple servers using simple algorithms (e.g., round-robin), ensuring even load distribution.
Reverse proxy can act as a load balancer but offers additional features like User authentication and validation(example block this ip address), URL interception and smart routing, SSL termination and Caching In short, a reverse proxy not only balances load but also adds flexibility and security layers, making it a more versatile choice.

#### 🔍 For a detailed explanation of Monolithic/Microservice architecture & Proxies, please check the Prerequisites folder.

#### ✅ Issues Faced
EC2 ran into a no space issue.
* Increased the size of the attached EBS volume from 8 GB to 30 GB using AWS.
* Checked disk storage with df -h and block devices with lsblk.
* Installed cloud-utils to enable resizing of partitions and file systems: sudo apt install cloud-utils
* Verified which partition is mounted on root (/).
* Increased the partition size and then resized the file system to utilize the expanded storage: sudo growpart /dev/xvda 1 — increase partition 1 on disk /dev/xvda sudo resize2fs /dev/xvda1 — resize the filesystem on partition 1
