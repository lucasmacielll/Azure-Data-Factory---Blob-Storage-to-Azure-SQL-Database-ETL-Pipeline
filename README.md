# Azure-Data-Factory---Blob-Storage-to-Azure-SQL-Database-ETL-Pipeline
End-to-end Azure Data Factory ETL pipeline that transfers CSV data from Azure Blob Storage to Azure SQL Database using Managed Identity and Microsoft Entra ID authentication.

📖 Project Overview

This project demonstrates the implementation of an end-to-end ETL (Extract, Transform, and Load) pipeline using Azure Data Factory. The pipeline is responsible for extracting a CSV file stored in Azure Blob Storage, performing a Move & Transform operation, and loading the processed data into an Azure SQL Database.

The primary objective of this project is to demonstrate how Azure-native services can be integrated to build a secure, scalable, and production-ready data ingestion solution while following Microsoft best practices for authentication and access management.

🎯 Project Objectives
Build an end-to-end ETL pipeline using Azure services.
Load structured CSV data from Azure Blob Storage into Azure SQL Database.
Implement secure authentication using System Assigned Managed Identity.
Eliminate the use of hardcoded credentials by leveraging Microsoft Entra ID.
Demonstrate troubleshooting and resolution of common authentication and connectivity issues encountered in Azure environments.
🔄 Pipeline Type

Move & Transform

The pipeline performs the following workflow:

Reads a CSV file stored in Azure Blob Storage.
Validates and maps the dataset.
Transfers the data through Azure Data Factory.
Loads the data into an Azure SQL Database.
Executes the process using Managed Identity authentication.
🛠 Technologies & Services
Service	Purpose
Azure Data Factory	Data integration and pipeline orchestration
Azure Blob Storage	Source storage for CSV files
Azure SQL Database	Destination relational database
Azure SQL Server	SQL server hosting the database
Microsoft Entra ID	Identity and authentication management
System Assigned Managed Identity	Secure authentication between Azure services
🔐 Authentication

This project uses System Assigned Managed Identity for authentication between Azure Data Factory and Azure SQL Database.

Instead of storing usernames and passwords, Microsoft Entra ID securely authenticates the Data Factory, following Azure security best practices.

🔎 Troubleshooting

During the implementation, several real-world issues were identified and resolved.

Azure SQL Authentication Error

Issue

The Azure SQL Server was configured to accept only Microsoft Entra ID authentication while the Linked Service was configured to use SQL Authentication.

Resolution

Changed the Linked Service authentication method to System Assigned Managed Identity.
Removed SQL Authentication from the connection configuration.
Azure SQL Firewall Restriction

Issue

The Azure Integration Runtime was blocked by the Azure SQL Server firewall.

Resolution

Configured Azure SQL Server firewall rules.
Allowed Azure services to access the SQL Server.
Validated network connectivity.
Managed Identity Authentication Failure

Issue

Azure Data Factory successfully authenticated with Microsoft Entra ID but failed to access the Azure SQL Database.

Resolution

Created a database user mapped to the Managed Identity.
Granted the required database roles.
CREATE USER [ManagedIdentity] FROM EXTERNAL PROVIDER;

ALTER ROLE db_datareader ADD MEMBER [ManagedIdentity];

ALTER ROLE db_datawriter ADD MEMBER [ManagedIdentity];
Managed Identity Discovery

Issue

The Managed Identity name differed from the Azure Data Factory resource name, preventing the database user from being created.

Resolution

Located the Managed Identity in Microsoft Entra ID using its Object ID.
Identified the correct Enterprise Application name.
Successfully created the database principal.
📚 Skills Demonstrated
Azure Data Factory
Azure Blob Storage
Azure SQL Database
Azure SQL Server
Microsoft Entra ID
Managed Identity
ETL Pipeline Development
Move & Transform Pipelines
Linked Services
Datasets
Azure Integration Runtime
Azure SQL Firewall Configuration
Database Security
Identity-Based Authentication
Cloud Troubleshooting
Production-Ready Azure Architecture
🚀 Project Outcome
✅ Successfully built an end-to-end Azure ETL pipeline.
✅ Secure authentication implemented using System Assigned Managed Identity.
✅ CSV data successfully loaded into Azure SQL Database.
✅ Microsoft Entra ID authentication configured without storing credentials.
✅ Multiple Azure authentication and connectivity issues identified, analyzed, and resolved.
