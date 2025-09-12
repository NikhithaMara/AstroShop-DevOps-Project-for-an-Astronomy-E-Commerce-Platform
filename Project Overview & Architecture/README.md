
### 🛒 Project Overview

I chose the E-Commerce Demo Project open-sourced by OpenTelemetry, which simulates an online store selling astronomy products like telescopes.
This project is built using a microservices architecture, with each service implemented in a different language.

#### 🧩 Microservices Overview

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

### 🏗️ Project Architecture
<img width="580" height="386" alt="image" src="https://github.com/user-attachments/assets/b48c92f6-48a7-45e9-8cc4-a077ea43a5ad" />

#### 🌐 Application Flow:

   * Requests from the internet first hit a reverse proxy (server-side), which Validates traffic, Load balances requests and Routes them to the frontend service
   * The frontend serves the UI and communicates with backend microservices over HTTP/gRPC protocold
   * Microservices handle specific business logic like Cart, Shipping, Payment, Product Catalog, Email, etc.
   * A load generator simulates user traffic for testing and observability.
   * A React Native mobile app interacts with the backend via the same APIs.

* Increased the partition size and then resized the file system to utilize the expanded storage:
  sudo growpart /dev/xvda 1 — increase partition 1 on disk /dev/xvda
  sudo resize2fs /dev/xvda1 — resize the filesystem on partition 1
