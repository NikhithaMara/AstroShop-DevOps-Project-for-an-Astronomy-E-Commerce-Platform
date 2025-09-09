# 🧠 Why I Chose This Project

In today's world, almost every company  from brands like Nike to platforms like Amazon has an online store to sell products. This makes building an eCommerce application a common and highly relevant real-world scenario. This project gave me hands-on exposure to:
* Containerizing multiple microservices written in different progarmming languagues using Docker 
* Managing communication between services via API calls
* Implementing a reverse proxy (Envoy) to route and validate requests before they reach backend services
* Using load generation tools to simulate real-world traffic
* Applying CI/CD pipelines, monitoring, and infrastructure automation

This project reflects a full DevOps workflow applied to a real-world system, helping me strengthen my practical skills in deployment, scalability, and infrastructure management.

# 🛒 Project Overview

I chose the E-Commerce Demo Project open-sourced by OpenTelemetry, which simulates an online store selling astronomy products like telescopes.
This project is built using a microservices architecture, with each service implemented in a different language or framework. Below is a list of the microservices and their descriptions:

### 🧩 Microservices Overview

| **Microservice**      | **Language**     | **Description** |
|-----------------------|------------------|-----------------|
| `frontend`            | TypeScript       | Serves the website via HTTP. Automatically generates session IDs. |
| `product-catalog`     | Go               | Lists/searches products from a JSON file. |
| `cart`                | .NET             | Stores and retrieves shopping cart data using Valkey. |
| `shipping`            | Rust             | Estimates shipping cost based on the cart and address. |
| `quote`               | PHP              | Calculates shipping based on item count. |
| `checkout`            | Go               | Handles full order flow: cart, payment, shipping, email. |
| `currency`            | C++              | Converts between currencies using ECB rates. High QPS. |
| `payment`             | JavaScript       | Mocks credit card transactions. |
| `email`               | Ruby             | Sends order confirmation emails. |
| `ad`                  | Java             | Displays contextual ads. |
| `recommendation`      | Python           | Suggests products based on the cart. |
| `accounting`          | .NET             | Aggregates order values. |
| `load-generator`      | Python           | Simulates user shopping flows for testing. |
| `react-native-app`    | TypeScript       | Mobile UI for shopping services. |

# 🏗️ Project Architecture
<img width="580" height="386" alt="image" src="https://github.com/user-attachments/assets/b48c92f6-48a7-45e9-8cc4-a077ea43a5ad" />

# 🌐 Application Flow:

   * Requests from the internet first hit a reverse proxy (server-side), which Validates traffic, Load balances requests and Routes them to the frontend service
   * The frontend serves the UI and communicates with backend microservices over HTTP/gRPC protocold
   * Microservices handle specific business logic like Cart, Shipping, Payment, Product Catalog, Email, etc.
   * A load generator simulates user traffic for testing and observability.
   * A React Native mobile app interacts with the backend via the same APIs.

# 🎨 Design Questions I Got When I Started

# 🤔 Why choose microservice architecture over monolithic?
* Scalability: Microservices allow independent scaling of components based on demand, unlike monoliths which scale as a whole.
* Flexibility: Different services can use different technologies best suited for their tasks.
* Faster Deployment: Smaller, focused teams can develop, test, and deploy services independently, speeding up release cycles.
* Fault Isolation: Failures in one microservice don’t necessarily bring down the entire system.

# ⚖️ Can’t I use a load balancer instead of a reverse proxy?
* Load balancer distributes incoming traffic across multiple servers using simple algorithms (e.g., round-robin), ensuring even load distribution.
* Reverse proxy can act as a load balancer but offers additional features like User authentication and validation(example block this ip address), URL interception and smart    routing, SSL termination and Caching
In short, a reverse proxy not only balances load but also adds flexibility and security layers, making it a more versatile choice.

# 🔍 For a detailed explanation of Monolithic architecture & Proxies, please check the Prerequisites folder.




