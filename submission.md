# CSP451 Milestone 3 — Submission
**Student Name:** Sophia Lolong
**Student ID:** 1238436248
**GitHub Repo:** https://github.com/nobrainc55-cell/CSP451-milestone3
**Live URL:** http://cloudmart-2050172.canadacentral.azurecontainer.io/

---

## 1. Azure Login and Resource Verification
az group show --name Student-RG-2050172 -o table
az resource list --resource-group Student-RG-2050172 -o table
Screenshot: Resource group overview showing ACI + Cosmos DB + ACR
<img width="1919" height="869" alt="image" src="https://github.com/user-attachments/assets/b88a73e7-4051-4485-ac2b-e7f4558193a6" />


## 2. Cosmos DB Setup
az cosmosdb show --name cloudmart-db-2050172 ...
Screenshot: Data Explorer with products, cart, and orders containers
<img width="1917" height="751" alt="image" src="https://github.com/user-attachments/assets/99be6b46-9233-4db4-a1bd-d958d166b2c5" />


## 3. Application Development
Key files: main.py, database.py, models.py, seed_data.py
Local curl test output:
(paste your curl output for /health, /api/v1/products, /api/v1/categories)
<img width="1919" height="866" alt="image" src="https://github.com/user-attachments/assets/a0f55ea7-3b3c-4142-b2b1-d7894520bd04" />


## 4. Docker Build and Test

Screenshot: GitHub Actions CD pipeline building Docker image  
<img width="1919" height="820" alt="image" src="https://github.com/user-attachments/assets/58eb1efa-7e5b-4450-8ece-29739122ed41" />

Screenshot: GitHub Actions showing successful push to Azure Container Registry (ACR)  
<img width="1919" height="820" alt="image" src="https://github.com/user-attachments/assets/b1ad2858-8e2e-41df-a259-0ad39dbababc" />


## 5. Azure Deployment
Screenshot: ACI details (running, IP, FQDN)
<img width="1919" height="301" alt="image" src="https://github.com/user-attachments/assets/9c822478-4a34-41eb-ad14-2e44f3a1693e" />

Screenshot: curl /health and /api/v1/products
<img width="1919" height="874" alt="image" src="https://github.com/user-attachments/assets/2ce155c5-e174-4395-930d-6c34b96fd622" />

Screenshot: CloudMart homepage via public URL
<img width="1919" height="789" alt="image" src="https://github.com/user-attachments/assets/14b170ed-1183-4101-a2b7-0735f5c08b71" />

Screenshot: Container logs
<img width="1919" height="875" alt="image" src="https://github.com/user-attachments/assets/68e60ead-aea7-47e9-8ddd-b6726ad44b7b" />


## 6. CI/CD Pipeline
Screenshot: GitHub Secrets settings page (9 secrets configured)
<img width="1919" height="886" alt="image" src="https://github.com/user-attachments/assets/ea6f3255-999a-4514-a2dc-75dfa8a375e9" />

Screenshot: GitHub Actions CI + CD passing
<img width="1919" height="848" alt="image" src="https://github.com/user-attachments/assets/b490dc7a-7cec-4f83-8856-286c5302b62d" />

Screenshot: ACR repository with image tags
<img width="1918" height="507" alt="image" src="https://github.com/user-attachments/assets/f5a119b1-3895-4d6c-b9bf-e59a87e370d7" />


## 7. End-to-End Testing
All 11 curl test outputs:
(paste your full test session output)
5 browser screenshots: Homepage, category filter, cart, order, /health
<img width="1919" height="439" alt="image" src="https://github.com/user-attachments/assets/bc148b9b-607a-42c0-94be-18d6a30315b8" />
<img width="1919" height="473" alt="image" src="https://github.com/user-attachments/assets/7c5e259d-fc6e-4175-b5ac-4914bc8a181b" />
<img width="1918" height="682" alt="image" src="https://github.com/user-attachments/assets/864a06e5-315b-43fb-9818-e041c80cde98" />
<img width="1919" height="873" alt="image" src="https://github.com/user-attachments/assets/b44ac165-f0b0-4eb5-923b-3c9028e85564" />
<img width="1918" height="391" alt="image" src="https://github.com/user-attachments/assets/07212701-6fde-46c2-8765-f736ec43fd94" />


## 8. Reflection
1. How does the security model of a publicly exposed ACI container
   differ from the NSG-protected VMs in Milestone 1?
A publicly exposed ACI container is directly accessible over the internet, while NSG-protected VMs have stricter network-level controls that filter traffic. In production, I would add authentication, restrict public access using private endpoints, and use a firewall or API gateway for extra protection.
   What additional protections would you add in production?
   In production, I would add additional protections such as restricting access using private endpoints or virtual networks, placing the container behind an API gateway or load balancer, enabling authentication and authorization (like Azure AD or JWT tokens), and enforcing HTTPS with proper firewall rules to reduce exposure to attacks.


3. How could you apply the monitoring techniques from Milestone 2
   (flow logs, IDS alerts) to this containerized deployment?
   Flow logs and IDS alerts could be used to monitor traffic going to the container and detect unusual or malicious requests. Logs from Azure Container Instances and Cosmos DB could also be sent to Azure Monitor or Log Analytics to track performance and errors in real time.

4. What is one thing you would change about this architecture
   if CloudMart had 10,000 concurrent users?
   If CloudMart had 10,000 users, I would move to a scalable solution like Azure Container Apps or Kubernetes with autoscaling. I would also add caching (Redis), a load balancer (Azure Front Door), and increase database throughput in Cosmos DB.
