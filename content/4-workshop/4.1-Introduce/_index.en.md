---
title : "Introduction"
date :  "2024-01-01" 
weight : 1 
chapter : false
pre : " <b> 4.1. </b> "
---

### Introduction

#### Introduction to Multi-Tier Architecture

- Multi-Tier Architecture is an application design pattern that separates components into multiple independent tiers. Each tier has distinct responsibilities and communicates with others through well-defined interfaces.
- This architecture provides benefits such as easy scalability and maintenance, and separation of concerns between tiers.

#### Workshop Overview

In this workshop, we will deploy a complete e-commerce website on AWS.

- **"Customer Service"** runs in the public subnet to serve customers accessing from the internet. This service handles functions like viewing car lists, product details, and scheduling test drives.
- **"Admin/Employee Service"** runs in the private subnet for internal management. This service is accessible only through Application Load Balancer with path-based routing, handling administrative functions like product management, orders, users, and other items.
- **"Lambda Email Service"** is a serverless function that handles sending notification emails to customers when booking test drives or when employees need password resets.

![Architecture Overview](/images/arc-log.png)