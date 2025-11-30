---
title: "Week 8 Worklog"
date: "2025-02-24"
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:
- Deploy VPC networking and IAM setup.
- Create DynamoDB tables and migrate data model from MongoDB.
- Complete CarBuyer application with DynamoDB and split into 2 independent services.
- Start writing workshop documentation.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference |
|-----|------|------------|----------------|-----------|
| 2 | - Start writing workshop <br> - Deploy VPC networking <br>&emsp; + Create VPC with 2 public + 2 private subnets <br>&emsp; + Configure Internet Gateway and NAT Gateway <br>&emsp; + Set up Route Tables <br> - Set up IAM roles/policies <br>&emsp; + Create IAM Role for EC2 <br>&emsp; + Create IAM Role for Lambda | 03/11/2025 | 03/11/2025 |  |
| 3 | - Continue writing workshop <br> - Create DynamoDB tables <br>&emsp; + Design schema for 12 tables <br> - Migrate data model <br>&emsp; + Analyze MongoDB schema <br>&emsp; + Design DynamoDB schema | 04/11/2025 | 04/11/2025 |  |
| 4 | Watch videos and complete quizzes for Week 1 and Week 2 | 05/11/2025 | 05/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/baf0a945-afdb-428d-ad81-a146139a7817> <https://specialforce.awsstudygroup.com/#/certPublic/2b93f7b5-3693-4326-9939-f5cd55400805> |
| 5 | Watch videos and complete quizzes for Week 3 and Week 4 | 06/11/2025 | 06/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/561fffd5-cf83-4f17-af70-cc1f8ac91862> <https://specialforce.awsstudygroup.com/#/certPublic/afe70851-24a1-4935-8806-4c4cc4d10b3a> |
| 6 | - Continue writing workshop <br> - Complete CarBuyer website <br>&emsp; + Modify code to switch from MongoDB to DynamoDB <br>&emsp; + Test CRUD operations <br>&emsp; + Fix bugs and optimize code | 07/11/2025 | 07/11/2025 |  |
| 7 | - Continue writing workshop <br> - Watch videos and complete quizzes for Week 5 and Week 6 <br> - Continue completing CarBuyer website <br> - Split services into 2 independent services (Customer and Admin/Employee) | 07/11/2025 | 07/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/3117bd18-58fb-419b-847c-5d0a7c9f8477> <https://specialforce.awsstudygroup.com/#/certPublic/859dc734-c718-42f4-ad08-00d91d71c7eb> |

### Week 8 Achievements:
- Completed videos and quizzes for weeks 1, 2, 3, 4, 5, and 6.
- Successfully deployed VPC with 2 public + 2 private subnets, Internet Gateway, NAT Gateway, and Route Tables.
- Set up IAM roles for EC2 and Lambda.
- Created 12 DynamoDB tables and designed appropriate schemas.
- Successfully migrated data model from MongoDB to DynamoDB.
- Completed CarBuyer application with DynamoDB and split into 2 services (Customer and Admin/Employee).

### Challenges:
- Needed time to understand the difference between MongoDB (document-based) and DynamoDB (key-value).
- Splitting the application into 2 independent services required restructuring code and routing.

### Plan for Next Week:
- Set up S3, CloudFront, and VPC Gateway Endpoint.
- Develop Lambda email service with Nodemailer and API Gateway.
- Deploy 2 services to EC2 and configure Application Load Balancer.
- Continue writing workshop documentation.