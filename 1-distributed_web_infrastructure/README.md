# Distributed Web Infrastructure Design

This project demonstrates a three-server web infrastructure hosting www.foobar.com.

## Architecture Overview

- **Two Servers**:
  - **Server 1:** Hosts Nginx web server, application server, and application files.
  - **Server 2:** Hosts MySQL database configured in a Primary-Replica cluster.

- **Load Balancer (HAproxy):**  
  Receives incoming traffic and distributes it to the web/application server(s).

- **DNS:**  
  Resolves www.foobar.com to the Load Balancer’s IP address.

## Components Roles

- **Load Balancer:** Distributes user requests to prevent overload and improve availability.  
  Uses **Round Robin** distribution algorithm, sending requests evenly in sequence.

- **Active-Active vs Active-Passive:**  
  This design uses **Active-Active** load balancing: multiple servers handle requests simultaneously.  
  Active-Passive means one server handles traffic while the other is standby for failover.

- **Primary-Replica MySQL Cluster:**  
  The **Primary** node handles all write operations.  
  The **Replica** node replicates data from Primary and handles read operations to reduce load.

- **Web Server (Nginx):** Handles HTTP requests and forwards dynamic requests to the application server.

- **Application Server:** Runs backend application logic and interacts with the database.

## Known Issues

- **Single Points of Failure (SPOF):**  
  The load balancer and primary database are SPOFs.

- **Security:**  
  No firewalls or HTTPS implemented yet.

- **Monitoring:**  
  No monitoring tools are configured.

## Diagram

![Distributed Web Infrastructure Diagram](https://i.imgur.com/your-upload-link.png)
