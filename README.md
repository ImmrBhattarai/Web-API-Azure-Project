# Web-API-Azure-Project | DIO Project | Microsoft Cloud Native Bootcamp
Project focused on creating an API focused on payments, with an emphasis on security and access management using Azure resources.

# What I learned:

## ✅ End-to-End Summary: Python-Based Payment API with Azure App Service & API Management
### 🔧 1. App Service (Backend) Setup

-  Created a Web App in Azure using:
  
      Runtime stack: Python 3.13
   
      OS: Linux
   
      Publish type: Code (not container)
   
     ![Screenshot From 2025-05-06 10-30-57](https://github.com/user-attachments/assets/0305809a-473f-4f9f-a9ea-bc7ff53d4e1a)

-  Accessed the web app file system via Kudu Bash console.

     ![Screenshot From 2025-05-07 01-18-11](https://github.com/user-attachments/assets/bd3a7b22-2f14-4961-a83e-0854de9b2eb2)

     ![Screenshot From 2025-05-07 10-49-07](https://github.com/user-attachments/assets/d7c1d032-e673-44bf-a647-b3d35d381e8d)

-  Created backend logic using Flask, including:
  
      app.py to return mock JSON data
   
      requirements.txt for Python dependencies (flask, gunicorn)
   
      Startup.txt to run the app using Gunicorn
   
      ![Screenshot From 2025-05-07 11-00-28](https://github.com/user-attachments/assets/be4480e3-2c18-4404-819d-e71c75387bc3)

-  Configured Startup Command in App Service → Configuration → General Settings:

      startup.txt
   
      ![Screenshot From 2025-05-07 11-02-32](https://github.com/user-attachments/assets/47d1802b-185a-47f6-b57f-387c7bc3af21)

-  Installed dependencies and restarted the service to test responses at:

        https://webapppayment.azurewebsites.net/api/payment

        https://webapppayment.azurewebsites.net/api/payment/v1

### 🌐 2. API Management (Frontend/API Gateway) Setup

-    Created an API Management Service named APImanagement-payment.
  
     ![Screenshot From 2025-05-06 00-16-40](https://github.com/user-attachments/assets/218f48d5-cde8-4f8f-9d33-3f8be9479f69)

-    Created a new API using the “Import from App Service” option:

        Imported the backend App Service: webapppayment

        Set:

            Base URL: https://apimanagement-payment.azure-api.net/payment

            Version identifier: v1

            Versioning scheme: Path
     
        ![Screenshot From 2025-05-06 10-38-42](https://github.com/user-attachments/assets/f1cafaac-6efa-4b44-ad44-886d370d6d9d)

-    Linked this API again manually via App Service > API Management tab to ensure exposure through API Management.
  
     ![Screenshot From 2025-05-07 01-00-15](https://github.com/user-attachments/assets/03ce3903-41f7-4e7f-ad6d-2b82829a4bb7)

### 🔒 3. Network and Security Configuration

-    Created a Virtual Network (VNet) for future integrations.

-    Configured networking rules for the web app:

        Inbound traffic access: Set to Allow (No Restrictions)
     
        ![Screenshot From 2025-05-06 23-05-20](https://github.com/user-attachments/assets/8a737965-d970-41f7-87e6-8b9570b7f21a)


-    Enabled CORS for cross-origin access in the Web App settings.
  
     ![Screenshot From 2025-05-06 22-59-19](https://github.com/user-attachments/assets/a7c28938-47cd-4a33-b53b-d94e32955944)

-    Enabled and generated a new subscription key for the API Management service to authorize requests.
  
     ![Screenshot From 2025-05-07 00-02-22](https://github.com/user-attachments/assets/eb898c7e-9451-4b4d-8dd9-1c0a57404a57)
     
     ![Screenshot From 2025-05-07 00-07-27](https://github.com/user-attachments/assets/304bb91c-653c-47b5-a81a-377d25388833)


-    Tested GET request from Postman using this key:

        Verified 200 OK status and correct JSON response.
     
        ![Screenshot From 2025-05-07 15-07-49](https://github.com/user-attachments/assets/d1f27501-c41e-4ea7-a87c-31c1810248c2)

### 🛡️ 4. Authentication and Authorization (Security)

-    Applied a validate-jwt policy in the Inbound processing of the API Management service to enforce JWT-based access control.
  
     ![Screenshot From 2025-05-07 16-21-34](https://github.com/user-attachments/assets/02fe5f64-9c38-42cf-91f2-780e02e86755)
     
     ![Screenshot From 2025-05-07 16-39-35](https://github.com/user-attachments/assets/778adacb-30e4-4d83-851c-d0d5ea6076a7)
     
     ![Screenshot From 2025-05-07 16-39-40](https://github.com/user-attachments/assets/00728949-6647-41e1-9f71-c72ebc569566)


### ✅ 5. Final Validation

-    Successfully accessed the API via:

        Direct App Service endpoint

        Azure API Management endpoint

-    Confirmed secure, authenticated API responses using subscription keys and JWT validation.

-    Backend properly responds at versioned endpoints like:

        https://apimanagement-payment.azure-api.net/payment/v1


## What I learned?
### Cloud Native Backend Development with Python (i.e. Setting up Backend Python (Flask) service)
  - built a Python-based REST API using Flask, deploying it not on your local machine, but on a scalable cloud platform (Azure App Service).
  - learned to manage application files in a cloud environment using tools like Kudu Bash and basic Linux commands.
  - understood how to serve production-grade apps using Gunicorn, and configure startup behavior in a Linux-hosted web app.

### API Design and Versioning Best Practices
  - implemented clean REST endpoints like /api/payment and /api/payment/v1, which reflects good API design principles.
  - observed how versioning via URL paths (/v1) can help maintain backwards compatibility in production APIs.

### Azure API Management (APIM) as an API Gateway
  - used Azure API Management to expose your backend API securely and professionally.
  - learned how to:
    
        Import APIs from App Services
        Apply base paths and version identifiers
        Enable authentication policies and subscription management

  - had first-hand experience in creating a full API lifecycle management system — including consumption control and analytics capabilities.

### Security and Access Control in the Cloud
  - configured CORS to allow secure cross-origin requests, a crucial part of any frontend-backend integration.
  - applied JWT validation policies and learned how to work with subscription keys — exposing you to real-world API authentication and access strategies.

### Azure Networking and Resource Linking
  - created and understood the role of a Virtual Network (VNet), even if not heavily used in this scenario, preparing you for more complex architectures.
  - explored how different Azure services (App Service, APIM, Networking) interconnect to form a unified, secure, and scalable platform.

### Debugging and Cloud Troubleshooting Skills
  - practiced cloud debugging techniques like:

        Using the Kudu console
        Viewing Log Streams
        Modifying startup behavior and verifying routes

  - learned how to identify and fix issues like 404 errors, missing Python runtimes, and incorrect routing or configuration.
