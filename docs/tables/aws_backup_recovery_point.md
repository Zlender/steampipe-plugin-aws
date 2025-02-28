---
title: "Steampipe Table: aws_backup_recovery_point - Query AWS Backup Recovery Points using SQL"
description: "Allows users to query AWS Backup Recovery Points to gather comprehensive information about each recovery point within an AWS Backup vault."
---

# Table: aws_backup_recovery_point - Query AWS Backup Recovery Points using SQL

The AWS Backup Recovery Point is a component of AWS Backup, a fully managed backup service that makes it easy to centralize and automate the backup of data across AWS services. This resource, the recovery point, is an entity that contains all the metadata that AWS Backup needs to recover a protected resource, such as an Amazon RDS database, an Amazon EBS volume, or an Amazon S3 bucket. The recovery point is created after a successful backup of a protected resource.

## Table Usage Guide

The `aws_backup_recovery_point` table in Steampipe provides you with information about each recovery point within an AWS Backup vault. This table allows you, as a DevOps engineer or system administrator, to query recovery point-specific details, including the backup vault where the recovery point is stored, the source of the backup, the state of the recovery point, and associated metadata. You can utilize this table to gather insights on recovery points, such as identifying unencrypted recovery points, verifying backup completion status, and more. The schema outlines the various attributes of the recovery point for you, including the recovery point ARN, creation date, backup size, and associated tags.

## Examples

### Basic Info
Discover the segments that are significant in your AWS backup recovery points. This can be beneficial for assessing the status and type of resources within your backup vaults, which can help in managing your backup strategy effectively.

```sql+postgres
select
  backup_vault_name,
  recovery_point_arn,
  resource_type,
  status
from
  aws_backup_recovery_point;
```

```sql+sqlite
select
  backup_vault_name,
  recovery_point_arn,
  resource_type,
  status
from
  aws_backup_recovery_point;
```

### List encrypted recovery points
Identify instances where your recovery points are encrypted to ensure data security and compliance. This query is useful to maintain a secure and compliant data backup system by pinpointing the specific locations where encryption is applied.

```sql+postgres
select
  backup_vault_name,
  recovery_point_arn,
  resource_type,
  status,
  is_encrypted
from
  aws_backup_recovery_point
where
  is_encrypted;
```

```sql+sqlite
select
  backup_vault_name,
  recovery_point_arn,
  resource_type,
  status,
  is_encrypted
from
  aws_backup_recovery_point
where
  is_encrypted = 1;
```