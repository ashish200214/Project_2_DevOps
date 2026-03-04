# High Availability Strategy

## Overview

This project demonstrates how to build a **highly available and scalable web application** on AWS using **Auto Scaling and an Application Load Balancer**.
The goal was to ensure the application remains available even during traffic spikes or server failures.

---

## High Availability Strategy

### Multi–Availability Zone Deployment

Two public subnets were created in **different Availability Zones**.
This ensures that if one AZ fails, the application can still run from another AZ.

### Load Balancing

An **Application Load Balancer (ALB)** distributes incoming traffic across multiple EC2 instances.
This prevents a single server from being overloaded and improves response time.

### Auto Scaling

An **Auto Scaling Group (ASG)** automatically adjusts the number of EC2 instances based on CPU utilization.

* Minimum instances: 2
* Instances increase automatically when load increases
* Instances terminate when load decreases

This ensures the application can handle traffic spikes efficiently.

### Launch Template

A **Launch Template** was created from a configured EC2 instance running Nginx and the web application.
Auto Scaling uses this template to launch identical instances when scaling occurs.

### Health Checks

The Load Balancer continuously performs **health checks** on instances.
If an instance becomes unhealthy, traffic is automatically redirected to healthy instances.

---

## Result

* The application remained available during high CPU load.
* Auto Scaling automatically launched additional EC2 instances when stress was applied.
* The Load Balancer distributed traffic across all running instances.

This architecture removes single points of failure and ensures **high availability and scalability for web applications**.
