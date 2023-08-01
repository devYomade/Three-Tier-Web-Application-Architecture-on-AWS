# Three-Tier Web Application Architecture on AWS

## Overview

This document outlines the design of a scalable and resilient three-tier architecture on Amazon Web Services (AWS) for a web application that accepts requests from the internet and queries a MySQL database to return data to clients. The architecture leverages various AWS services, including Amazon Virtual Private Cloud (Amazon VPC), Amazon Elastic Compute Cloud (Amazon EC2), Amazon Relational Database Service (Amazon RDS) with high availability, and Elastic Load Balancing (ELB) to ensure efficient traffic flow and reliable performance.

## Architecture Diagram
## Work in Progress 😊😁
![1st picture](https://github.com/devYomade/Three-Tier-Web-Application-Architecture-on-AWS/assets/105651785/37500e71-8695-4504-bc35-417893cb6181)




## Architecture Components

### Networking Layer (Amazon VPC and ELB)

Amazon VPC provides a secure and isolated network environment for the application. The web application instances are placed within private subnets, ensuring that they are shielded from direct internet access. The Elastic Load Balancer (ELB) is deployed in a public subnet and serves as the entry point for incoming client requests. It distributes the incoming traffic across multiple EC2 instances in the compute layer, ensuring high availability and scalability.

### Compute Layer (Amazon EC2)

Amazon EC2 instances host the web application. To handle varying levels of traffic, the architecture employs Auto Scaling, which automatically adjusts the number of instances based on demand. As the number of incoming requests increases, Auto Scaling adds more instances to handle the load, and during periods of low traffic, it reduces the number of instances to optimize costs.

### Database Layer (Amazon RDS)

The MySQL database is hosted on Amazon RDS, providing a fully managed and highly available database service. RDS Multi-AZ deployment ensures redundancy and failover capability, ensuring minimal downtime and data loss in case of a primary instance failure. The database layer resides in private subnets to ensure secure access from the compute layer only.

## Traffic Flow

1. **Client Request**: Clients send requests to the web application through the public-facing Elastic Load Balancer (ELB). The ELB listens for incoming requests on port 80 (HTTP) or 443 (HTTPS).

2. **Load Balancing**: The ELB distributes incoming client requests across multiple EC2 instances in the compute layer. This load balancing mechanism ensures that no single instance is overwhelmed by traffic.

3. **Compute Layer Processing**: EC2 instances in the compute layer process the client requests. The web application queries the MySQL database in the backend to retrieve the requested data.

4. **Database Query**: The web application queries the highly available MySQL database hosted on Amazon RDS. The database layer stores and manages the application's data securely.

5. **Data Retrieval**: The MySQL database returns the requested data to the web application, which then prepares the response.

6. **Response to Client**: The web application sends the response back to the client through the ELB. The client receives the data they requested.

## Conclusion

The proposed three-tier architecture on AWS offers a robust and scalable solution for the web application scenario. By leveraging Amazon VPC, EC2, RDS, and ELB, the architecture ensures high availability, fault tolerance, and efficient traffic handling. Auto Scaling allows the system to dynamically adjust its compute capacity based on traffic demands, optimizing performance and cost-effectiveness. The use of Amazon RDS with Multi-AZ deployment guarantees data redundancy and automated failover for the database layer. Additionally, the separation of public and private subnets within the VPC enhances security by limiting direct internet access to the instances.

Overall, this AWS-based architecture provides a reliable and scalable foundation for the web application, enabling it to handle incoming client requests and efficiently retrieve data from the backend database, while ensuring the highest levels of availability and performance.
