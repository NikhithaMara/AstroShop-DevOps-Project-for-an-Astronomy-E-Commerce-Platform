# AstroShop-DevOps-Project-for-an-Astronomy-E-Commerce-Platform:
An end-to-end DevOps project for an astronomy-themed eCommerce platform. Features microservices architecture, CI/CD pipelines, container orchestration with Kubernetes, Infrastructure as Code using Terraform, and full observability with Prometheus and Grafana.

# 🧠 Why I Chose This Project
In today's world, almost every company  from brands like Nike to platforms like Amazon has an online store to sell products. This makes building an eCommerce application a common and highly relevant real-world scenario. Most modern applications are built using a microservices architecture, with each service written in a different programming language. This project gave me hands-on exposure to:
# Containerizing multiple microservices using Docker
# Managing communication between services via REST APIs
# Implementing a reverse proxy (Envoy) to route and validate requests before they reach backend services
# Using load generation tools to simulate real-world traffic
# Applying CI/CD pipelines, monitoring, and infrastructure automation

This project reflects a full DevOps workflow applied to a real-world system, helping me strengthen my practical skills in deployment, scalability, and infrastructure management.
 
# 🎨 Design Questions I Got When I Started
🤔 Why choose microservice architecture over monolithic?
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




