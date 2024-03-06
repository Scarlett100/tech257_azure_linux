
# <center>The basics of Azure<center/>

Azure regions and availability zones: how they work and include up-to-date diagrams to help

## How is Azure structured/organised (resources you create on there)?

##  <center> simple architecture <center/>

![azure](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/enterprise-integration/_images/simple-enterprise-integration.png)

##  <center> More complex architecture <center/>

![azure](https://learn.microsoft.com/azure/architecture/browse/thumbs/aks-cicd-azure-pipelines-architecture.png)


### <center> 1. Cloud Computing Models: <center/>

Infrastructure as a Service (IaaS): This category provides on-demand virtual computing resources.Rent the computer building blocks (VMs, storage, networking) on-demand with IaaS. You control them directly, like building with Legos in the cloud! You have a lot of control over the underlying infrastructure.

Platform as a Service (PaaS): Tools like Azure App Service, Azure Functions, and Azure Kubernetes Service (AKS) allow you to build, deploy, and manage applications without managing the underlying infrastructure. Imagine a like a pre-built kitchen where you just focus on cooking (your code). No need to worry about setting up the  appliance (infrastructure).

Software as a Service (SaaS):  This category provides access to pre-built applications hosted by Microsoft & are accessed through a web browser or API and cover various functional areas like CRM, analytics, and productivity tools. Imagine renting software or a subscription rather than purchasing.


### <center> 2. Core Services: <center/>

![core services](https://k21academy.com/wp-content/uploads/2021/04/image.png)

These services form the foundation for building and deploying cloud solutions on Azure. They include:

Compute: Services for creating and managing virtual machines (VMs), containers, and serverless functions.
Storage: Solutions for storing data in various forms, including blobs, disks, databases, and archival storage.
Networking: Tools for creating and managing virtual networks, firewalls, load balancers, and other network components.
Databases: A variety of managed database services, including relational databases like SQL Database and NoSQL databases like Cosmos DB.


The Cloud Building Blocks:

Compute: Imagine these as the brains of your cloud applications. You can create virtual machines (like powerful PCs), containers (smaller, focused tasks), or serverless functions (code that runs on-demand) depending on your needs.
Storage: This is your cloud filing cabinet! Store all kinds of data, from pictures (blobs) to documents (disks) to organized information (databases).
Networking: Think of this as the cloud's highways and bridges. Connect all your cloud parts (VMs, databases, etc.) and control who can access them with firewalls and load balancers.
Databases: These are like organized filing cabinets in the cloud. Choose from familiar ones like SQL Database or more flexible options like Cosmos DB for different types of data.




3. Other Service Areas:

Beyond the core services, Azure offers a vast range of additional services catering to specific needs:

Machine Learning and Artificial Intelligence (AI): Services to build, train, and deploy machine learning models and leverage AI capabilities.
Internet of Things (IoT): Tools to connect, manage, and analyze data from IoT devices.
Migration and Management: Services to assist with migrating existing workloads to Azure and managing them effectively.
Security: A comprehensive suite of security services for protecting your data and applications in the cloud.
Data Management and Analytics: Tools for storing, managing, and analyzing large datasets.
Development and Integration: Services to streamline development workflows and integrate different applications and services.

## What types/categories of services does Azure provide?

# <center> The Azure Pricing Calculator? </center>

********* what is it***********************

![calc](https://static.packt-cdn.com/products/9781789614503/graphics/assets/db25ff5c-8bd2-4adb-8c45-edcd4e7598a0.png)

<center>You should use the Azure Pricing Calculator for several reasons: <center/>

## <center> Before deploying to Azure: <center/>

* **Cost estimation and budgeting**: <br>  
    * primary use case. <br>
    * calculator helps you estimate the potential costs for specific Azure services for your use case.<br>
    * Gets you a breakdown of costs once you enter resources such as instance types, database needs etc.<br>
    * Can now plan and adjust cloud budget realistically and accurately. Allowing for informed decisions.<br>


* **Service Comparison**: <br> 
    * The calculator allows you to compare pricing options for different Azure services. Helpful to see what works for you.

* **Identifying potential savings**: <br>
    * The calculator presents possible opportunities to optimise your costs. 
    * Possibly show you  more cost-effective service tiers or pricing models based on your usage patterns. eg. using spot instances for flexible workloads.

## <center> After deploying to Azure (for existing customers): <center/>

* **Cost monitoring and analysis**: <br>    
    * While the calculator is primarily for pre-deployment estimates, it can also be used to analyse existing Azure costs. 
    * If you're already using Azure, you can log in with your billing account to see a more precise cost breakdown based on usage. 
    * This helps you identify areas for potential cost reduction
    


<center> Azure Virtual Machines <center/>



1: Region

