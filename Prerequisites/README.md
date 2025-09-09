When we have an e-commerce application, for example, amazon.com, it includes multiple business functionalities or requirements such as user authentication, product catalog, cart, shipping, and order confirmation email.
* If we include all these functionalities in a single codebase as modules, and every module shares variables and common libraries, then we cannot separate them easily. This creates problems:
If we change one module, it may affect others due to dependencies.
* For example, if we modify the cart module, since everything is bundled together, we need to rebuild and redeploy the entire application.
* We also cannot scale functions independently. For example, if the shipping module experiences more traffic, we cannot scale just shipping; we must scale the whole application.
  This is called a monolithic application.

In contrast, in a microservices architecture, business functions are split into independent services, each with its own codebase and possibly implemented in different technologies (e.g., different programming languages).
* These services can be scaled independently based on traffic.
* They communicate with each other through API calls (HTTP or other protocols).
* Each service exposes an endpoint (e.g., a URL, or internally an IP and port) that allows others to interact with it.
* Standard protocols (like GET or POST) are used for communication; otherwise, the service would not understand the requests.

### Monolithic vs Microservices

| **Monolithic Application**                                   | **Microservices**                                              |
|--------------------------------------------------------------|----------------------------------------------------------------|
| Single codebase                                              | Multiple codebases                                             |
| Working in a team requires close collaboration, as changes
may affect other modules                                      | Easier teamwork since services are independent                |
| One Git repository for the entire project                   | Can have a single repo with folders for each service, or multiple repos |
| CI/CD triggers for the whole application                    | CI/CD triggers only for the changed service                   |
| Cannot scale/build/deploy independently                     | Can scale/build/deploy independently                           |

### Forward Proxy
* Sits in front of the client (before reaching the internet).
* Intercepts requests, checks for malicious URLs, and is often used in companies for security.

### Reverse Proxy
* Sits in front of the server.
* Handles SSL/TLS encryption internally within Kubernetes networks, performs security checks, and routes traffic based on URLs.
* Functions as a load balancer and can also handle caching.

### Load Balancer
* Balances incoming traffic across servers using simple routing algorithms (e.g., round-robin, which distributes requests equally among servers).
* Typically handles external traffic to the application using encryption, but not internal traffic within Kubernetes networks.
* Cannot forward requests based on URL content.
* Does not handle caching; it only distributes traffic.
