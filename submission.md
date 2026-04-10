# CSP451 Milestone 3 — Submission
**Student Name:** YOUR NAME
**Student ID:** XXXXXXX
**GitHub Repo:** https://github.com/YOUR_USERNAME/CSP451-milestone3
**Live URL:** http://cloudmart-XXXXXXX.canadacentral.azurecontainer.io

---

## 1. Azure Login and Resource Verification
az group show --name Student-RG-XXXXXXX -o table
az resource list --resource-group Student-RG-XXXXXXX -o table
Screenshot: Resource group overview showing ACI + Cosmos DB + ACR

## 2. Cosmos DB Setup
az cosmosdb show --name cloudmart-db-XXXXXXX ...
Screenshot: Data Explorer with products, cart, and orders containers

## 3. Application Development
Key files: main.py, database.py, models.py, seed_data.py
Local curl test output:
(paste your curl output for /health, /api/v1/products, /api/v1/categories)

## 4. Docker Build and Test
Screenshot: docker build output
Screenshot: App running locally at http://localhost:8080

## 5. Azure Deployment
Screenshot: ACI details (running, IP, FQDN)
Screenshot: curl /health and /api/v1/products
Screenshot: CloudMart homepage via public URL
Screenshot: Container logs

## 6. CI/CD Pipeline
Screenshot: GitHub Secrets settings page (9 secrets configured)
Screenshot: GitHub Actions CI + CD passing
Screenshot: ACR repository with image tags

## 7. End-to-End Testing
All 11 curl test outputs:
(paste your full test session output)
5 browser screenshots: Homepage, category filter, cart, order, /health

## 8. Reflection
1. How does the security model of a publicly exposed ACI container
   differ from the NSG-protected VMs in Milestone 1?
   What additional protections would you add in production?

2. How could you apply the monitoring techniques from Milestone 2
   (flow logs, IDS alerts) to this containerized deployment?

3. What is one thing you would change about this architecture
   if CloudMart had 10,000 concurrent users?
