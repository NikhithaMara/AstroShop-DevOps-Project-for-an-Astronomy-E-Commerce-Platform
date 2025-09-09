# 🧠 Why I Chose This Project
In today's world, almost every company  from brands like Nike to platforms like Amazon has an online store to sell products. This makes building an eCommerce application a common and highly relevant real-world scenario. Most modern applications are built using a microservices architecture, with each service written in a different programming language. This project gave me hands-on exposure to:
Containerizing multiple microservices using Docker
Managing communication between services via REST APIs
Implementing a reverse proxy (Envoy) to route and validate requests before they reach backend services
Using load generation tools to simulate real-world traffic
Applying CI/CD pipelines, monitoring, and infrastructure automation
This project reflects a full DevOps workflow applied to a real-world system, helping me strengthen my practical skills in deployment, scalability, and infrastructure management.

# 🛒 Project Overview
I chose the E-Commerce Demo Project open-sourced by OpenTelemetry, which simulates an online store selling astronomy products like telescopes.
This project is built using a microservices architecture, with each service implemented in a different language or framework. Below is a list of the microservices and their descriptions:
# Microservice    	     Language	             Description
frontend    	           TypeScript	           Serves the website through an HTTP server. Does not require sign-up/login and generates session IDs automatically.
product-catalog	        Go	                   Provides a list of products from a JSON file. Supports search and retrieval of individual products.
cart	                  .NET	                  Stores and retrieves items in a user’s shopping cart using Valkey(open source in memory Caching Service similar to Redis) .
shipping	               Rust	                 Calculates shipping cost estimates based on the contents of the cart and destination address.
quote                  	PHP	                  Calculates shipping cost based on the number of items to be shipped.
checkout	               Go                   	Orchestrates order processing: retrieves the cart, processes payment, manages shipping, and triggers email confirmation.
currency	               C++	                  Converts monetary values between currencies using real-time rates from the European Central Bank. High QPS service.
payment	                JavaScript	           Credit card payment processing and returns a transaction ID.
email	                  Ruby	                 Sends order confirmation emails to users.
ad	                     Java	                 Serves text-based ads based on context keywords.
recommendation	         Python	               Recommends products based on the current cart contents.
accounting	            .NET                  	Processes completed orders and tracks the total sales.
load-generator	         Python	               Simulates realistic shopping behavior by continuously sending requests to the frontend.
react-native-app	       TypeScript	           React Native mobile application providing a UI for the shopping services.

🏗️ Project Architecture
<img width="580" height="386" alt="image" src="https://github.com/user-attachments/assets/b48c92f6-48a7-45e9-8cc4-a077ea43a5ad" />


# 🎨 Design Questions I Got When I Started

# 🤔 Why choose microservice architecture over monolithic?
Scalability: Microservices allow independent scaling of components based on demand, unlike monoliths which scale as a whole.
Flexibility: Different services can use different technologies best suited for their tasks.
Faster Deployment: Smaller, focused teams can develop, test, and deploy services independently, speeding up release cycles.
Fault Isolation: Failures in one microservice don’t necessarily bring down the entire system.

# ⚖️ Can’t I use a load balancer instead of a reverse proxy?
Load balancer distributes incoming traffic across multiple servers using simple algorithms (e.g., round-robin), ensuring even load distribution.
Reverse proxy can act as a load balancer but offers additional features like User authentication and validation, URL interception and routing, SSL termination
and Caching
In short, a reverse proxy not only balances load but also adds flexibility and security layers, making it a more versatile choice.

🔍 For a detailed explanation of Monolithic architecture & Proxies, please check the Prerequisites folder.




