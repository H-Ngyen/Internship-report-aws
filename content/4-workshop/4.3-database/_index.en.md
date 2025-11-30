---
title : "Create DynamoDB Database"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.3. </b> "
---

### Create DynamoDB Database

In this section, we will create the necessary DynamoDB tables for the CarBuyer application and import sample data.

#### Introduction to Amazon DynamoDB

Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability.

**Key Advantages:**

- **High Performance** - Low latency at single-digit milliseconds for both read and write operations
- **Serverless** - No need to manage servers, automatically scales based on demand
- **Flexible Billing** - On-demand pricing mode charges only for what you use, no minimum capacity
- **High Availability** - Automatically replicates data across multiple Availability Zones
- **Good Integration** - Native integration with other AWS services like Lambda, API Gateway, S3

#### Database Structure

The CarBuyer application uses 12 DynamoDB tables to store data:

| Table | Description | Partition Key |
|-------|-------------|---------------|
| User | User information (admin, employee, customer) | id (String) |
| XeOto | Car information (model, price, specs) | id (String) |
| ThuongHieu | Car and accessory brands | id (String) |
| MauXe | Car colors | id (String) |
| KieuDang | Car types (Sedan, SUV, Hatchback...) | id (String) |
| NguyenLieuXe | Fuel types (Petrol, Diesel, Hybrid, Electric) | id (String) |
| PhuKien | Car accessory information | id (String) |
| LoaiPhuKien | Accessory types (interior, exterior...) | id (String) |
| TinTuc | News and articles | id (String) |
| DanhGia | Customer reviews | id (String) |
| Slider | Homepage slider images | id (String) |
| DatLichKH | Customer test drive scheduling | id (String) |

![DynamoDB Architecture](/images/arc-database.png)

#### Content

1. [Create DynamoDB Tables](4.3.1-create-tables/)
2. [Import Sample Data](4.3.2-import-data/)
