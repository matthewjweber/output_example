# GCP Infrastructure Documentation
Generated on: 2024-01-24

## Overview
This document provides a comprehensive overview of the Google Cloud Platform (GCP) infrastructure currently in use.

## Project Information
Current project: wp-serverless-demo

### Available Projects
| Project ID | Name | Project Number | State |
|------------|------|----------------|-------|
| matts-ga-sandbox | Matt's GA Sandbox | 929276460361 | ACTIVE |
| matts-search-eng-1612273907005 | Matt's Search Engine | 457093336574 | ACTIVE |
| my-project-1526479890245 | My Project | 829656162028 | ACTIVE |
| shopify-pm-demo-1554146966007 | Shopify PM Demo | 587014820973 | ACTIVE |
| wp-serverless-demo | wp-serverless-demo | 683450197111 | ACTIVE |

## Infrastructure Components
The following sections detail the various GCP resources and their configurations.

### Compute Resources

#### Compute Engine
No Compute Engine instances found in the current project.

#### Cloud Functions
Cloud Functions API is not enabled for this project.

#### Cloud Run Services
| Service Name | Region | Last Modified By | Last Deployed |
|--------------|--------|------------------|---------------|
| wp-cr-wordpress | us-central1 | matthewjweber@gmail.com | 2024-10-24T06:42:53.140609Z |

### Storage Resources

#### Cloud Storage
No Cloud Storage buckets found in the current project.

#### Cloud SQL
| Instance Name | Database Version | Status | 
|--------------|------------------|--------|
| wp-mysql | MySQL 8.4 | RUNNABLE |

### Network Configuration

#### VPC Networks
1. default
   - Default VPC network with auto-created subnets in multiple regions
   - Private Google Access: Disabled
2. wp-sql-vpc
   - Custom VPC network
   - Contains subnet 'subnet' in us-central1 with Private Google Access enabled

#### Firewall Rules
| Rule Name | Network | Direction | Priority | Source Ranges | Allow |
|-----------|---------|-----------|-----------|---------------|-------|
| default-allow-icmp | default | INGRESS | 65534 | 0.0.0.0/0 | icmp |
| default-allow-internal | default | INGRESS | 65534 | 10.128.0.0/9 | tcp:0-65535, udp:0-65535, icmp |
| default-allow-rdp | default | INGRESS | 65534 | 0.0.0.0/0 | tcp:3389 |
| default-allow-ssh | default | INGRESS | 65534 | 0.0.0.0/0 | tcp:22 |

### Architecture Summary
The infrastructure appears to be a WordPress deployment using Cloud Run and Cloud SQL:
1. WordPress application running on Cloud Run (wp-cr-wordpress) in us-central1
2. MySQL database (wp-mysql) running on Cloud SQL
3. Custom VPC network (wp-sql-vpc) likely used for secure database connectivity
4. Default networking rules allowing standard access patterns (SSH, RDP, ICMP, internal communication)

### Identity and Access Management (IAM)

#### Service Accounts
| Email | Display Name | Status |
|-------|--------------|--------|
| 683450197111-compute@developer.gserviceaccount.com | Compute Engine default service account | Active |

The infrastructure uses the default Compute Engine service account, which typically has the following characteristics:
- Automatically created for Compute Engine resources
- Used by default for Cloud Run services unless otherwise specified
- Has the default Compute Engine service account role
