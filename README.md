#### 👋 About Me
Hi, I’m Nikhitha Mara , an aspiring DevOps Engineer passionate about learning AWS and deploying projects to build real-world DevOps skills. I’m actively working on hands-on projects and sharpening my knowledge to break into DevOps roles. This repo documents my learning journey and showcases projects focused on cloud infrastructure, automation, CI/CD, and monitoring.

#### 🧠 Why I Chose This Project
In today's world, almost every company from brands like Nike to platforms like Amazon has an online store to sell products. This makes building an eCommerce application a common and highly relevant real-world scenario. This project gave me hands-on exposure to:
* Containerizing multiple microservices written in different progarmming languagues using Docker
* Managing communication between services via API calls
* Implementing a reverse proxy (Envoy) to route and validate requests before they reach backend services
* Using load generation tools to simulate real-world traffic
* Applying CI/CD pipelines, monitoring, and infrastructure automation
This project reflects a full DevOps workflow applied to a real-world system, helping me strengthen my practical skills in deployment, scalability, and infrastructure management using AWS, IAM, EC2, S3, DynamoDB, Docker, Docker Compose, k8s, EKS.

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

#### 🚀 Deployed E-commerce Application on EKS Using Terraform
✅ Terraform Best Practices Followed:
* 🔒 Remote state is stored securely in Amazon S3, with DynamoDB used for state locking to avoid concurrent operations.
* 🚫 State files are not committed to GitHub, as they may contain sensitive information such as IPs, resource IDs, and secrets.
* 🧑‍🤝‍🧑 Shared remote state enables team collaboration and prevents resource duplication or conflicts.
* 🔐 AWS authentication is handled through the configured AWS CLI, ensuring secure and authorized access to AWS services.
* 📁 A separate backend.tf file is used for backend configuration, improving readability and separation of concerns.

🚀 **CI/CD** — Automates build, test, and deployment using tools like GitHub Actions & ArgoCD.  
🔁 **CI** ensures the code is built and tested; **CD** delivers it to Kubernetes — faster, safer, and more efficient.  
✅ Implemented CI/CD for microservices architecture.
<img width="887" height="398" alt="image" src="https://github.com/user-attachments/assets/68708853-6577-46fc-abc8-83ade21c4c45" />

#### 🎨 Design Questions I Got When I Started

#### 🤔 Why choose microservice architecture over monolithic?
Scalability: Microservices allow independent scaling of components based on demand, unlike monoliths which scale as a whole.
Flexibility: Different services can use different technologies best suited for their tasks.
Faster Deployment: Smaller, focused teams can develop, test, and deploy services independently, speeding up release cycles.
Fault Isolation: Failures in one microservice don’t necessarily bring down the entire system.

#### ⚖️ Can’t I use a load balancer instead of a reverse proxy?
Load balancer distributes incoming traffic across multiple servers using simple algorithms (e.g., round-robin), ensuring even load distribution.
Reverse proxy can act as a load balancer but offers additional features like User authentication and validation(example block this ip address), URL interception and smart routing, SSL termination and Caching In short, a reverse proxy not only balances load but also adds flexibility and security layers, making it a more versatile choice.

#### 🧩 Why can't I just use Docker instead of Kubernetes?
Docker was introduced to solve the problem of "it works on my machine but not on yours." Containers package your application with all its dependencies, making it portable and consistent across environments. Containers are also lightweight, spin up quickly, and make better use of system resources compared to running multiple full VMs. This allows for more efficient resource utilization, especially in cloud or virtualized environments. However, Docker alone is not enough for production-grade deployments.
##### 🚨 Limitations of Docker without Kubernetes:
Containers are ephemeral (short-lived). If one crashes, it must be restarted manually or with basic Docker tools.
Networking is fragile. If one container communicates with another using its IP, and that container restarts, its IP may change — breaking communication.
Docker doesn't natively provide service discovery, load balancing, high availability, or self-healing.

#### ✅ Why Kubernetes?
Kubernetes was designed to orchestrate containers at scale. It handles:
* Service discovery and stable networking between containers
* Automatic restarts, scaling, and self-healing of failed containers
* Load balancing traffic
* High availability through clusters
* Disaster recovery features

#### 🌐 My Use Case
For local development and testing, Docker is great. But for production, I used a managed Kubernetes service (Elastic Kubernetes Service(EKS)) to ensure
Stability, Scalability, High availability and Easier maintenance and disaster recovery

#### 🔍 For a detailed explanation of Monolithic/Microservice architecture & Proxies, please check the Prerequisites folder.

#### ✅ Issues Faced 
##### Used Docker Compose for testing whole application with dependent microservices on EC2 instance and EC2 ran into a no space issue.
* Increased the size of the attached EBS volume from 8 GB to 30 GB using AWS.
* Checked disk storage with df -h and block devices with lsblk.
* Installed cloud-utils to enable resizing of partitions and file systems: sudo apt install cloud-utils
* Verified which partition is mounted on root (/).
* Increased the partition size and then resized the file system to utilize the expanded storage: sudo growpart /dev/xvda 1 — increase partition 1 on disk /dev/xvda sudo resize2fs /dev/xvda1 — resize the filesystem on partition 1

##### 🔁 Difference Between Docker Compose & Kubernetes
* Docker Compose simply executes multiple containers together through a single command by putting all services in one file, instead of running each one separately and     manually handling dependencies.
* Kubernetes (K8s), on the other hand, is a container orchestration tool that provides high availability, service discovery, disaster recovery, auto-scaling,
  and self-healing.

##### How I Resolved a Merge Conflict in Git (GitHub)
* Encounter the Conflict:
  A merge conflict happens when two branches modify the same line of code.
* Open Conflicting Files:
  Git marks the conflicting files as unmerged and shows conflict markers (<<<<<<<, =======, >>>>>>>).
* Resolve the Conflict:
  I resolved the conflict by opening the file and reviewing the changes in both branches, choosing the necessary changes to keep and discarding the ones that weren't needed,
  and removing the conflict markers (<<<<<<<, =======, >>>>>>>) after making the necessary edits.
* Stage the Files:
  After resolving the conflicts, I staged the resolved files using git add.
* Commit and Push:
  I committed the resolved files with a clear message and then pushed the changes back to the remote repository.

  

  
