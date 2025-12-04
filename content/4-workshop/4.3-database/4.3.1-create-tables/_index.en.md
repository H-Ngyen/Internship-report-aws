---
title : "Create DynamoDB Tables"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.3.1 </b> "
---

1. Launch AWS CloudShell at [CloudShell Interface](https://console.aws.amazon.com/cloudshell/home?region=ap-southeast-1)

2. **Open ap-southeast-1 environment**

![](/Internship-report-aws/images/5-workshop/3.dynamodb/001-dynamoDB.png?width=90pc)

3. Type command **`aws configure`**

4. Enter details from the csv file in section [4.2.3 Create Access Keys](../../4.2-Prerequiste/4.2.3-create-access-keys/):

- **AWS Access Key ID**
- **AWS Secret Access Key**
- **Default region name**: `ap-southeast-1`
- **Default output format**

![](/Internship-report-aws/images/5-workshop/3.dynamodb/002-dynamoDB.png?width=90pc)

5. To create table, use **`create-table`** command. Type:

```bash
aws dynamodb create-table --table-name DanhGia --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name DatLichKH --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name KieuDang --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name LoaiPhuKien --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name MauXe --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name NguyenLieuXe --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name PhuKien --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name Slider --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name ThuongHieu --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name TinTuc --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name User --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name XeOto --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1
```

6. Results:

- Results on AWS CloudShell:

![](/Internship-report-aws/images/5-workshop/3.dynamodb/003-dynamoDB.png?width=90pc)

- Results on the interface:

![Create Tables](/Internship-report-aws/images/5-workshop/3.dynamodb/004-dynamoDB.png?width=90pc)

7. Verify created tables

After creation, check the list of tables:

```bash
aws dynamodb list-tables --region ap-southeast-1
```

The result will display 12 tables:

```json
{
    "TableNames": [
        "DanhGia",
        "DatLichKH",
        "KieuDang",
        "LoaiPhuKien",
        "MauXe",
        "NguyenLieuXe",
        "PhuKien",
        "Slider",
        "ThuongHieu",
        "TinTuc",
        "User",
        "XeOto"
    ]
}
```

You have completed creating DynamoDB tables! Next, we will import sample data.
