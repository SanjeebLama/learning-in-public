### Microsoft Azure

A cloud computing platform with an ever-expanding set of services to help you build solutions to meet your business goals.

**Azure services support everything from simple to complex.**

- simple web services for hosting your business presence in the cloud.
- supports running fully virtualized computers managing your custom software solutions.
- a wealth of cloud-based services like remote storage, database hosting, and centralized account management.
- offers new capabilities like artificial intelligence (AI) and Internet of Things (IoT) focused services.

### Fundamentals:

- A. Introduction Cloud Computing
- B. Azure architecture and services
- C. Azure management and governance

# A. Introduction Cloud Computing

### What is cloud computing?

The delivery of virtualized computing services over the internet.

- Computing services include _common IT infrastructure such as virtual machines, storage, databases, and networking_.
- Cloud services also expand the traditional IT offerings to include things like _Internet of Things (IoT), machine learning (ML), and artificial intelligence (AI)_.

<br/>

### The shared responsibility model

A concept where both the cloud service provider and the customer share the responsibility for securing and managing different parts of the cloud infrastructure.

<br/>
<details>
<summary>History</summary>

Start with a traditional corporate datacenter. The company is responsible for maintaining the physical space, ensuring security, and maintaining or replacing the servers if anything happens. The IT department is responsible for maintaining all the infrastructure and software needed to keep the datacenter up and running. They’re also likely to be responsible for keeping all systems patched and on the correct version.

With the shared responsibility model, these responsibilities get shared between the cloud provider and the consumer. Physical security, power, cooling, and network connectivity are the responsibility of the cloud provider. The consumer isn’t collocated with the datacenter, so it wouldn’t make sense for the consumer to have any of those responsibilities.

At the same time, the consumer is responsible for the data and information stored in the cloud. (You wouldn’t want the cloud provider to be able to read your information.) The consumer is also responsible for access security, meaning you only give access to those who need it.

</details>
<br/>

![image](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/shared-responsibility-b3829bfe.svg)

**When using a cloud provider, you’ll always be responsible for:**

- The information and data stored in the cloud
- Devices that are allowed to connect to your cloud (cell phones, computers, and so on)
- The accounts and identities of the people, services, and devices within your organization

**The cloud provider is always responsible for:**

- The physical datacenter
- The physical network
- The physical hosts

**Your service model will determine responsibility for things like:**

- Operating systems
- Network controls
- Applications
- Identity and infrastructure

<br/>

### Cloud Models

1. **Public Cloud:**

   - services are delivered over the internet by a third-party provider, making them available to anyone who wants to use or purchase them. These services are typically offered on a pay-as-you-go basis, where users only pay for the resources they consume.
   - Example: Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP).

2. **Private Cloud:**

   - similar advantages to a public cloud but is _dedicated solely to one organization_.
   - It is typically hosted on-premises or in a data center operated by a third-party provider, offering greater control, security, and customization options.
   - Example: VMware Cloud Foundation, OpenStack.

3. **Hybrid Cloud:**

   - combines elements of both public and private clouds.
   - It allows data and applications to be shared between them, providing flexibility, scalability, and the ability to leverage the benefits of both cloud models.
   - Example: A company might use a private cloud for sensitive data and applications while utilizing a public cloud for less sensitive workloads or to handle spikes in demand.

4. **Multi-cloud:**

   - you use multiple public cloud providers. Maybe you use different features from different cloud providers.
   - Or maybe you started your cloud journey with one provider and are in the process of migrating to a different provider.
   - Regardless, in a multi-cloud environment you deal with two (or more) public cloud providers and manage resources and security in both environments.

5. **Azure Arc:**

   - Azure Arc is a set of technologies that helps manage your cloud environment. Azure Arc can help manage your cloud environment, whether it's a public cloud solely on Azure, a private cloud in your datacenter, a hybrid configuration, or even a multi-cloud environment running on multiple cloud providers at once.

6. **Azure VMware Solution:**
   - What if you’re already established with VMware in a private cloud environment but want to migrate to a public or hybrid cloud? Azure VMware Solution lets you run your VMware workloads in Azure with seamless integration and scalability.

<br/>

### Consumption-based model

- a pricing and billing approach in which customers only pay for the resources or services they actually use, rather than making fixed payments regardless of usage.

- It allows for flexible scaling and cost control, as charges are based on usage metrics such as data storage, computing power, network bandwidth, or the number of transactions processed.

- This model is commonly used in cloud computing, where users can adjust their resource allocation according to their needs, resulting in more efficient resource utilization and cost management.

<br/>

# The benefits of using cloud services

When building or deploying a cloud application, two of the biggest considerations are uptime (or availability) and the ability to handle demand (or scale).

<br/>

1. **High Availability**:

- ensuring that your applications or services are consistently accessible whenever they're needed, even in the face of disruptions. - In Azure, high availability is guaranteed through _service-level agreements (SLAs)_, providing uptime assurances for different services.

<details>
<summary> SLAs in details</summary>

Service Level Agreements (SLAs) define the level of service that a customer can expect from a service provider, typically regarding uptime and availability. The numbers like 99% or 99.9% represent the percentage of time a service is guaranteed to be available within a given period, usually measured annually.

- **99% Uptime**: This means the service is guaranteed to be available for at least 99% of the time in a given period, which allows for approximately 3.65 days of downtime per year or around 7.2 hours per month.

- **99.9% Uptime (Three Nines)**: This implies a higher level of availability, with the service guaranteed to be available for at least 99.9% of the time. This allows for approximately 8.76 hours of downtime per year or around 43.2 minutes per month.

In practical terms, the difference between these SLAs can be significant for businesses, especially those with critical applications. Higher uptime guarantees provide greater assurance of continuous service availability, minimizing disruptions and ensuring better reliability for users. However, achieving higher uptime levels often requires additional redundancy, fault tolerance, and investment in infrastructure, which can impact costs.

When choosing a service provider or cloud platform, organizations should carefully consider their uptime requirements and select SLAs that align with their business needs and tolerance for downtime.

</details>
<br/>

2. **Scalability**

- the ability to easily and rapidly adjust resources, such as computing power and storage capacity, in response to changing demand.
- This allows businesses to efficiently handle fluctuations in workload without the need for significant upfront investment in infrastructure.
- Scalability in the cloud offers benefits such as improved performance, cost optimization, and the ability to accommodate growth and innovation seamlessly.
- It enables organizations to scale resources up or down as needed, ensuring optimal resource utilization and enhancing agility in adapting to evolving business requirements.

### Vertical Scaling (Scaling Up):

- Increasing the capacity of individual resources, such as upgrading CPU, memory, or storage.
- Involves adding more powerful hardware components to existing infrastructure.
- Provides a quick solution to meet increased demand or improve performance.
- May have limitations in scalability and cost-effectiveness due to hardware constraints.
- Typically requires downtime during upgrades and can be more complex to manage.

### Horizontal Scaling (Scaling Out):

- Adding more instances of resources, such as servers, to distribute workload across multiple machines.
- Focuses on adding more identical resources in parallel to handle increased demand.
- Offers better scalability and fault tolerance as workload is distributed across multiple machines.
- Common strategy in cloud computing, where virtual machines or containers can be provisioned or decommissioned dynamically.
- Enables more efficient resource utilization and provides better resilience against hardware failures or performance bottlenecks.

> In summary, vertical scaling adds more power to existing resources, while horizontal scaling adds more resources in parallel to handle increased demand.

<br/>

3. **Reliability**

- the ability of a system to recover from failures and continue to function
- It encompasses various aspects such as availability, consistency, fault tolerance, and resilience to ensure that users can rely on the system to deliver consistent performance and meet their expectations.

Certainly, here's a brief overview of the benefits of predictability, performance, and cost in computing:

4. **Predictability**:

   - Predictability ensures that systems behave consistently and reliably, allowing users to anticipate and plan for expected outcomes.
   - It reduces uncertainty and improves decision-making by providing reliable estimates of system behavior and performance.
   - Predictable systems facilitate smoother operations, enhance user experience, and foster trust and confidence in the technology.

5. **Performance**:

   - Performance refers to the speed, responsiveness, and efficiency of computing systems in executing tasks and delivering results.
   - Improved performance leads to faster processing, reduced latency, and enhanced user satisfaction.
   - High-performance systems enable organizations to handle larger workloads, process data more quickly, and achieve better outcomes in terms of productivity and competitiveness.

6. **Cost**:

   - Cost considerations include both the initial investment and ongoing expenses associated with deploying and maintaining computing infrastructure.
   - Optimizing costs involves balancing performance, scalability, and efficiency to achieve the best possible value for resources expended.
   - Cost-effective solutions maximize return on investment (ROI) by minimizing unnecessary expenditures, optimizing resource utilization, and aligning expenses with business needs and priorities.

7. **Enhanced Security**:

   - Cloud providers invest heavily in security measures, offering advanced encryption, access controls, and threat detection capabilities.
   - Centralized security management and monitoring help detect and respond to security threats more effectively.
   - Regular security updates and patches are applied automatically by the cloud provider, reducing the burden on organizations to maintain security measures.

8. **Improved Compliance and Governance**:

   - Cloud platforms offer compliance certifications and adherence to industry standards, helping organizations meet regulatory requirements more easily.
   - Governance tools enable organizations to enforce policies, track usage, and ensure compliance across their cloud environments.
   - Centralized governance provides visibility and control over cloud resources, reducing the risk of unauthorized access or data breaches.

9. **Scalability and Flexibility**:
   - Cloud security scales dynamically with resource usage, ensuring consistent protection regardless of workload fluctuations.
   - Flexible security configurations allow organizations to customize security policies and controls to meet specific needs and requirements.
   - Automated security processes streamline operations and reduce manual intervention, enabling organizations to focus on innovation and growth.

In summary, security and governance in the cloud offer enhanced protection against cyber threats, simplified compliance management, and greater flexibility to adapt to changing business needs. These benefits enable organizations to mitigate risks, improve operational efficiency, and maintain trust and confidence in their cloud environments.
