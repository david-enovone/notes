## SBA - Service Based Architecture
### Technical Summary
My blog post on this pattern, written for a developer I was mentoring at the time: https://bluetoaster.io/posts/service-based-architecture/

We need to stay flexible, but we need to break out and break down coupling. Moving to more domain centric software design, with services, we can make our dev day-to-day lives easier*.



### Executive Summary

Service-based architecture, enhances software development by breaking down applications into smaller, independent services. Each service focuses on a specific business function and can be developed, deployed, and scaled independently. 

This approach improves flexibility, scalability, and resilience, allowing organizations to respond more quickly to changing requirements. Utilizing technologies like Docker and Kubernetes, along with API gateways, service-based architecture streamlines development processes and optimizes resource use, making it a powerful strategy for modern application development.


## Automated Testing

### Technical Summary
Ideally choosing between one of these two, depending upon where this gets slotted:
	1. Begin adding tests in bulk to the monolith with Django testing library
	2. As the monolith is broken up into services, tests are added

Tests should be ran automatically, regardless of CI/CD Pipeline, whenever a PR is opened or committed to.


### Executive Summary

Automated testing improves software development efficiency by using tools to test applications automatically, reducing manual effort and errors. It supports continuous integration and delivery, enabling faster release cycles and higher product quality. 

By catching issues early, automated testing saves time and resources, leading to more reliable software and a better user experiences.

## CI/CD Pipeline

### Technical Summary
We should aim to grab an off-the-shelf CI/CD tool for the interim until we can build out and support our own. This could be as simple as GitHub Actions, or, something like CircleCI.

Note that this is a known additional attack surface: https://github.com/rung/threat-matrix-cicd

### Executive Summary

A CI/CD pipeline enhances software development by automating the integration and deployment of code changes. 

This process reduces manual effort, speeds up release cycles, and ensures higher software quality. By continuously merging, testing, and deploying code, CI/CD pipelines help teams catch and fix issues early, resulting in more reliable software and a smoother development process.



## GraphQL 

### Technical Summary
This could be an optional stopgap while services are split up, and databases are enhanced.

Adding a GraphQL layer lets us update the resolvers as the data and services move around, minimizing the amount of updates we need to make to the business layers (Controllers + Views) and instead allow us to focus on the service layers.

Note that GraphQL is known to be tedious when managing ACL/Permissions. This would need to be addressed. Ideally overtime the GraphQL will stop serving sensitive data requests; offloading HIPAA and tenant only requests to a different API layer. 

### Executive Summary

GraphQL is an advanced technology for API management that offers efficient data retrieval and manipulation. 

Unlike traditional REST APIs, GraphQL allows clients to specify exactly what data they need, minimizing over-fetching and under-fetching of data. This results in improved performance and a more streamlined interaction between clients and servers. 

GraphQL's flexibility and efficiency make it a valuable tool for modern application development, enhancing the overall developer experience and optimizing API usage.

## Infrastructure

### Technical Summary
Since we're not really staffing devops / SRE at the moment, nor would it be practical, we should lean into what we can do while meeting practical infrastructure best practices.

We can build out better queue workers, logging, and access control -- all while just committing some markup or scripts to GitHub repos.

### Executive Summary
Infrastructure as Code (IaC) revolutionizes how IT infrastructure is managed by using code to automate provisioning and deployment.

This method enhances efficiency, consistency, and scalability, eliminating the need for manual configurations. By treating infrastructure setup as code, teams can version, track, and collaborate on infrastructure changes just like they do with software development. 

IaC tools such as Terraform, Ansible, and AWS CloudFormation streamline operations, reduce errors, and enable rapid scaling, making them essential for modern, agile IT environments.