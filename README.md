# Monolithic Applications

A monolithic application refers to a software application that is built as a single, self-contained unit with all its components tightly integrated together. In a monolithic architecture, all the modules and components of the application are combined into a single executable file or codebase, and they all run within a single process. This means that all the features and functionalities of the application are packaged and deployed together, and any changes or updates to the application require modifying and redeploying the entire monolithic application.

Examples of typical monolithic applications in different programming languages that run on Linux and Windows are:

- .NET Monolithic Application: An example of a monolithic application in .NET could be a traditional ASP.NET Web Forms application written in C# using the [.NET framework](https://learn.microsoft.com/en-us/dotnet/framework/get-started/) where the entire application logic, including the UI, business logic, and data access, runs in [Internet Information Services (IIS)](https://learn.microsoft.com/en-us/troubleshoot/developer/webapps/iis/iis-welcome) or is bundled into a single executable file. All the application components run within a single process, for example, an IIS application pool or a Windows service, and are tightly coupled.
- WCF service: a service-oriented application built using the [Windows Communication Foundation(WCF)](https://learn.microsoft.com/en-us/dotnet/framework/wcf/whats-wcf) framework using the full .NET framework. WCF is supported in the [.NET framework](https://learn.microsoft.com/en-us/dotnet/framework/get-started/), but not in [.NET 5+](https://learn.microsoft.com/en-us/dotnet/standard/glossary#net-5-and-later-versions).
- Java Monolithic Application: an enterprise [Java](https://en.wikipedia.org/wiki/Java_(programming_language) application built using the [Java Enterprise Edition (Java EE)](https://www.oracle.com/java/technologies/java-ee-glance.html) platform, where the entire application, including the web tier, business logic, and data access, is packaged into a single WAR (Web Archive) file or EAR (Enterprise Archive) file and deployed to a Java application server, such as [Apache Tomcat](https://tomcat.apache.org/) or [IBM WebSphere](https://www.ibm.com/products/websphere-application-server).
- Other examples of monolithic applications in different programming languages and platforms could include a [single-page application (SPA)](https://en.wikipedia.org/wiki/Single-page_application) built using a monolithic [JavaScript](https://en.wikipedia.org/wiki/JavaScript) framework like [AngularJS](https://angular.io/) or [React](https://react.dev/), a Content Management System (CMS) application where all the components are bundled together, or an ERP (Enterprise Resource Planning) application where all the modules are tightly integrated into a single executable or codebase.

A monolithic application uses a layered design, with separate tiers for the UI, application logic, and data access. As a monolithic application grows, it can start suffering from the following problems:

- Individual components and subsystems cannot be scaled independently from one another because they are tightly coupled.
- It is hard to maintain a single codebase because of tight coupling and hidden dependencies between the libraries used by the monolithic application.
- Testing becomes harder, increasing the likelihood of introducing vulnerabilities.
- Software components and libraries need to be written using the same programming language.

These problems can become a challenge and obstacle to future growth and stability. Teams could be wary of making changes, especially if the original developers are no longer working on the project and design documents are sparse or outdated.

In the early phases of development, monoliths are easier to create because there is a single shared codebase to test and maintain. Still, as the application grows in complexity, they become progressively harder to build, debug, deploy, monitor, and support. When problems outweigh the benefits, migrating the application to a microservices architecture is better. Unlike monoliths, microservices are typically decentralized, loosely coupled units of execution. A [microservice-based architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/microservices) provides the following advantages over a monolithic application:

- Services can evolve independently based on user needs.
- Specific teams build and maintain separate services using different technology stacks and programming languages.
- Services can scale independently to keep up with the traffic conditions.
- Services are isolated and are more tolerant of failure.
- A single service that fails will not bring down the entire application.

Migrating a monolithic application to a microservice-based architecture requires significant time and investment. For this reason, when bringing a monolithic application to Azure, a customer usually starts with a lift-and-shift approach where the monolithic application and its database are hosted in a set of Windows or Linux virtual machines using an [Infrastructure as a Service (IaaS)](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-azure/azure-iaas/#overview) approach. 

The next step in the cloud journey consists in containerizing and hosting a monolithic application in a PaaS computing platform such as [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes), [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview), [Azure Container Instances (ACI)](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview), or [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview) and the database in an Azure fully-managed database like [Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/sql-database-paas-overview?view=azuresql) or [Azure Database for PostgreSQL](https://learn.microsoft.com/en-us/azure/postgresql/) that provides advantages like automatic patching or backups.

The final step is refactoring the application using a microservice-based approach and hosting the application in [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes) or [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview). If not already present in the organization, this step requires to acquire specific skills in many different areas, such as [Kubernetes](https://kubernetes.io/) or [DevOps](https://en.wikipedia.org/wiki/DevOps). For more information, see [Migrate a monolithic application to microservices using domain-driven design](https://learn.microsoft.com/en-us/azure/architecture/microservices/migrate-monolith).

## Personas

The following table contains the common personas involved in a software monolithic project hosted in Azure, along with their roles, tools, and responsibilities:

| Persona | Role and responsibilities |
|-|-|
| Technical Decision Maker | Technical decision makers and architects are responsible for making high-level technical decisions about the project, such as which technology stack to use, how to structure the architecture, and how to integrate with other systems. They also provide guidance to the development and operations teams. The tools they might use include tools such as [Microsoft Visio](https://www.microsoft.com/en-ww/microsoft-365/visio/flowchart-software) to create architecture diagrams and [Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) for planning activities. |
| Developer | Developers are responsible for writing the code for the project. They use programming languages such as C#, Java, or Python, and often use integrated development environments (IDEs) such as [Visual Studio](https://learn.microsoft.com/en-us/visualstudio/get-started/visual-studio-ide) or [Visual Studio Code](https://code.visualstudio.com/). They also use Azure services such as [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes) or [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview) to deploy and test their code on Azure. Developers also write automated tests to ensure the quality of their code. |
| Operations and DevOps |  System engineers use infrastructure as code  (IaC) technologies such as Terraform and Bicep to deploy resources to Azure. Operations and DevOps engineers are responsible for deploying and maintaining the application in production. DevOps engineers use tools such as [Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) and [GitHub Actions](https://docs.github.com/en/actions) to build and deploy applications to Azure. When hosting the application on [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes), DevOps engineers can also use Kubernetes-specific tools such as [kubectl](https://kubectl.docs.kubernetes.io/guides/introduction/kubectl/) deploy and manage applications on Kubernetes, or [Helm](https://helm.sh/) to package and deploy applications, or [GitOps](https://www.weave.works/technologies/gitops/) technologies such as [Flux](https://fluxcd.io/) or [Argo CD](https://argo-cd.readthedocs.io/en/stable/) as a continuous delivery tool for Kubernetes. Operations engineers are also responsible to monitor the health and performance of the application and underlying infrastructure on Azure using tools such as [Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/overview) or third party tools like [Datadog](https://www.datadoghq.com/solutions/azure/), and respond to any incidents that occur. Operations engineers work closely with the development team to ensure that the application is built with operational concerns in mind. |

Overall, the goal of all these personas is to ensure that the application is developed, deployed, and maintained in a secure, scalable, and reliable manner in Azure.

## Azure Services

The following table compares hosting a monolithic application on different hosting platforms on Azure.

| | [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes) | [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview) | [Azure Container Instances (ACI)](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview) | [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview) |
|-|-|-|-|-|
| Definition | [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes) provides a fully managed Kubernetes option in Azure. It supports direct access to the Kubernetes API and runs any Kubernetes workload. The full cluster resides in your subscription, with the cluster configurations and operations within your control and responsibility. Teams looking for a fully managed version of Kubernetes in Azure, Azure Kubernetes Service is an ideal option. AKS supports running Windows containers on Windows Server node pools | [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview) enables you to run and operate microservice-based applications or containerized monolithic applications. It supports Kubernetes-style apps and microservices with features like [service discovery](https://learn.microsoft.com/en-us/azure/container-apps/connect-apps), [traffic splitting](https://learn.microsoft.com/en-us/azure/container-apps/revisions) or [Kubernetes Event-Driven Autoscaling (KEDA)](https://keda.sh/), but it doesn't provide direct access to the underlying Kubernetes APIs. [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview) does not support [Windows containers](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/) | [Azure Container Instances (ACI)](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview) offers the fastest and simplest way to run a container in Azure, without having to manage any virtual machines and without having to adopt a higher-level service. Azure Container Instances is a great solution for any scenario that can operate in isolated containers, including monolithic applications, task automation, and build jobs. For more information, see [ACI Considerations](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview#considerations). | [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview) is an HTTP-based service for hosting web applications, REST APIs, and mobile back ends. You can develop in your favorite language, be it .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python. Azure App Service does not require containerizing a web application.  |
| Scenarios | [Azure Kubernetes Service (AKS)](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes) is the recommended hosting platform when you need full container orchestration, including service discovery across multiple containers, automatic scaling, load balancing, and coordinated application upgrades for both Linux and Windows monolithic applications. | [Azure Container Apps (ACA)](https://learn.microsoft.com/en-us/azure/container-apps/overview) is an ideal alternative to Azure Kubernetes Service (AKS) for hosting Linux-based monolithic applications when the development and operations teams don't have the necessary expertise to deploy, operate, and maintain a full-fledged Kubernetes project. | [Azure Container Instances (ACI)](https://learn.microsoft.com/en-us/azure/container-instances/container-instances-overview) is a great solution for any scenario that can operate in isolated containers, including Linux or Windows monolithic applications that don't to need to dynamically scale out or scale in, task automation, and build jobs. ACI is good hosting platform for Windows services, task automation, or CI/CD agents, but it's not a good fit for hosting web applications that need load balancing and autoscaling.  | [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview) is an ideal solution for hosting a web application developed with the .NET framework or Java, while it's not ideal for hosting a monolithic application that does not expose a web interface, for example a backend application running in a Windows service. |

## Personas x Azure Services x Monolith points of concern

The following table compares the different points of concern on hosting monolith apps on Azure container services according to personas

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th>Azure Kubernetes Service (AKS)</th>
    <th>Azure Container Apps (ACA)</th>
    <th>Azure Container Instances (ACI)</th>
    <th>Azure App Service</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Persona</td>
    <td>Category</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="3">Developer</td>
    <td>Tooling</td>
    <td>- Any Kubernetes-compatible client tool works<br>(kubectl, VsCode, Visual Studio, etc...)<br>- Azure native tools (Portal, CLI)</td>
    <td>- VsCode, Azure CLI, Portal</td>
    <td>- VsCode, Azure CLI, Portal</td>
    <td>- VsCode, Azure CLI, Portal</td>
  </tr>
  <tr>
    <td>Session management</td>
    <td>- <a href="https://azure.github.io/application-gateway-kubernetes-ingress/features/cookie-affinity/" target="_blank" rel="noopener noreferrer">Session affinity is supported</a></td>
    <td>- <a href="https://learn.microsoft.com/azure/container-apps/sticky-sessions?pivots=azure-portal#configure-session-affinity" target="_blank" rel="noopener noreferrer">Session affinity is supported</a></td>
    <td>- Stateless apps only</td>
    <td>- Session affinity is supported</td>
  </tr>
  <tr>
    <td>App configuration<br>- File system vs environment variables</td>
    <td>- </td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="2">Technical Decision Maker</td>
    <td>Cost</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Management overhead</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Operations and DevOps</td>
    <td>Scalability<br>- Ingress<br>- Vertical Scaling (scaling UP) vs Horizontal Scaling (scaling OUT)</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Deployment<br>- CI/CD tooling<br>- Support for statefulsets (mention Databases, messaging components)</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Networking<br>- Private link support?<br>- Service mesh support</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Container operating system support<br>- Windows vs Linux</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Web-server<br>- Apache, NGINX, IIS</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Monitoring<br>- Log and tracing <br>- Alerts</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Security<br>- EasyAuth support<br>- Authentication/Authorization</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>BCDR <br>- Backup<br>- Disaster recovery</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

