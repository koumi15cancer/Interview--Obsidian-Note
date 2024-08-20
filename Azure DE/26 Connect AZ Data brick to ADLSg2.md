# Securely Connecting Azure Databricks to Azure Data Lake Storage Gen2
![[Securely Connecting Azure Databricks to Azure Data Lake Storage Gen2.png]]
## Introduction
This article discusses different methods to connect Azure Databricks to Azure Data Lake Storage (ADLS) Gen2 securely, avoiding insecure methods like using account keys.

## Architecture Overview
- **Azure Databricks Workspace**: Primarily used for data transformations.
- **Azure Data Lake Storage (ADLS) Gen2**: Stores raw and transformed data.
- **Connectivity Importance**: Ensures secure and proper data flow between Databricks and Data Lake.

## Methods to Connect to ADLS Gen2

### 1. Account Key
- Insecure and not recommended.
- Grants full access to the storage account.
- Should only be used for quick tests.

### 2. Service Principal
- A more secure and preferred method.
- Involves creating a service principal in Azure Active Directory.
- Assign appropriate roles (e.g., Storage Blob Data Contributor) to the service principal.

### 3. SAS Token
- Generates a Shared Access Signature (SAS) token for temporary access.
- Less secure than using service principals but can be useful in some scenarios.

### 4. Azure Key Vault Integration
- Store secrets in Azure Key Vault.
- Use Databricks secret scopes to securely access secrets in notebooks.

### 5. Unity Catalog
- Databricks' recommended method for data governance.
- Integrates with Databricks for secure data management and access control.

## Detailed Steps for Service Principal and SAS Token Methods

### Service Principal Method

#### 1. Create Service Principal
- Go to Azure Active Directory > App registrations > New registration.
- Create a new service principal with a client secret (password).

#### 2. Assign Roles
- Assign the service principal the necessary roles in the storage account (e.g., Storage Blob Data Contributor).

#### 3. Databricks Configuration
- Configure Databricks to use the service principal for accessing ADLS Gen2.

```python
# Configuration for Service Principal
service_credential = "your-client-secret"
storage_account_name = "your-storage-account"
application_id = "your-application-id"
tenant_id = "your-tenant-id"

spark.conf.set("fs.azure.account.auth.type." + storage_account_name + ".dfs.core.windows.net", "OAuth")
spark.conf.set("fs.azure.account.oauth.provider.type." + storage_account_name + ".dfs.core.windows.net", "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider")
spark.conf.set("fs.azure.account.oauth2.client.id." + storage_account_name + ".dfs.core.windows.net", application_id)
spark.conf.set("fs.azure.account.oauth2.client.secret." + storage_account_name + ".dfs.core.windows.net", service_credential)
spark.conf.set("fs.azure.account.oauth2.client.endpoint." + storage_account_name + ".dfs.core.windows.net", "https://login.microsoftonline.com/" + tenant_id + "/oauth2/token")
```

### SAS Token Method

#### 1. Generate SAS Token

- Go to the storage account > Shared access signature.
- Generate a SAS token with the necessary permissions and validity period.

#### 2. Databricks Configuration

- Configure Databricks to use the SAS token for accessing ADLS Gen2.
-

```
# Configuration for SAS Token
sas_token = "your-sas-token"
storage_account_name = "your-storage-account"

spark.conf.set("fs.azure.sas." + storage_account_name + ".dfs.core.windows.net", sas_token)

```


### Using Azure Key Vault

#### 1. Store Secrets in Key Vault

- Store the client secret or SAS token in Azure Key Vault.

#### 2. Create Secret Scope in Databricks

- Use the Databricks CLI or UI to create a secret scope that links to the Azure Key Vault.

#### 3. Access Secrets in Notebooks

- Retrieve and use secrets in your Databricks notebooks securely.

```
# Retrieve secrets from Azure Key Vault via Databricks Secret Scope
service_credential = dbutils.secrets.get(scope = "your-secret-scope", key = "your-secret-key")

spark.conf.set("fs.azure.account.oauth2.client.secret." + storage_account_name + ".dfs.core.windows.net", service_credential)

```

## Conclusion

Azure Databricks provides multiple methods to securely connect to ADLS Gen2. The preferred method is using service principals and integrating with Azure Key Vault for managing secrets. The Unity Catalog offers enhanced data governance features but may not be widely adopted yet.