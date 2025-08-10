# Secured and Monitored Web Infrastructure Design

This project demonstrates a secure and monitored three-server web infrastructure for www.foobar.com.

## Architecture Overview

- **Three Servers**, each protected by its own **firewall**.
- **Load Balancer** (HAproxy) configured to serve HTTPS using an **SSL certificate** for www.foobar.com.
- **Monitoring Clients** (e.g., Sumologic agents) installed on all servers to collect metrics and logs.

## Components Added

- **Firewalls:**  
  Control incoming/outgoing traffic, block unauthorized access, and protect servers from attacks.

- **SSL Certificate (HTTPS):**  
  Encrypts traffic between users and servers to protect data integrity and privacy.

- **Monitoring Clients:**  
  Collect server and application metrics (CPU, memory, web requests per second, errors) and send data to monitoring services.

## Why these are added

- Firewalls increase security by limiting network access.
- HTTPS protects sensitive user data during transmission.
- Monitoring helps detect issues early and maintain server health.

## Monitoring Details

- Monitoring clients collect logs and metrics continuously.
- To monitor web server QPS (Queries Per Second), enable web server metrics collection or parse access logs.

## Known Issues

- Terminating SSL at load balancer can expose unencrypted traffic internally.
- Having a single MySQL server that handles all writes is a bottleneck and SPOF.
- Servers running all components (database, web, app) may cause resource contention and reduce fault isolation.

## Diagram

![Secured and Monitored Web Infrastructure Diagram](https://i.imgur.com/your-upload-link.png)
