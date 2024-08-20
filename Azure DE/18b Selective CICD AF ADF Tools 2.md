### Summary of the Video: Setting Up CI/CD for Azure Data Factory Using ADF Tools

![[Setting Up CI_CD for Azure Data Factory Using ADF Tools.png]]

#### Introduction
The video demonstrates how to set up Continuous Integration and Continuous Deployment (CI/CD) pipelines for Azure Data Factory (ADF) using ADF Tools, which allow for selective deployment of ADF objects.

#### Key Concepts
1. **Benefits of ADF Tools**:
   - Enables selective deployment of ADF objects.
   - Avoids the limitations of ARM template-based deployments that deploy everything.
   - Provides better control and configurability over deployments.

#### Implementation Steps
1. **Environment Setup**:
   - Use two instances of ADF: one for development (Dev) and one for production (Prod).
   - Ensure the Dev instance has Git integration configured and the Prod instance does not.

2. **Creating the Repository and Initial Files**:
   - Create a GitHub repository to store ADF resources.
   - Add a `devops` directory and create an `ADF_selective_job_template.yaml` file inside it.

3. **Setting Up the YAML Template**:
   - The YAML template will include steps to get the code, install ADF Tools PowerShell modules, test ADF code integrity, and deploy ADF using a deployment script.
   - Reference the [ADF Tools GitHub repository](https://github.com/KamilNowinski/azure.datafactory.tools) for detailed commands and documentation.

4. **Creating Configuration Files**:
   - Use CSV configuration files for different environments (Dev and Prod).
   - Each CSV file includes columns for type, name, path, and value to parameterize ADF objects.

5. **Setting Up Service Connections**:
   - Create service connections in Azure DevOps to allow pipelines to deploy ADF resources.
   - Ensure service connections have appropriate permissions (e.g., Contributor role).

6. **Configuring the Pipeline for Everything Deployment**:
   - Create a deployment script (`deploy_script.ps1`) and a pipeline YAML file for the Dev environment.
   - The pipeline will trigger on changes in the main branch and deploy everything in the branch to the Dev environment.

7. **Setting Up Selective Deployment Pipelines**:
   - Create selective deployment scripts for each team or product.
   - Define which objects to include in the deployment using functions like `Get-ADFObjectsByFolderName`.
   - Create separate deployment pipelines for each team, specifying the scope and objects to be deployed.

#### Example Scenario
1. **Team-Based Development**:
   - Team 1 and Team 2 work on separate features.
   - Each team has a selective deployment pipeline that deploys only their respective objects to Dev and Prod environments.
   - The main deployment pipeline runs automatically, deploying all changes in the main branch to the Dev environment.

2. **Pipeline Execution**:
   - The deployment pipeline for Team 1 deploys only Team 1's objects, ignoring Team 2's objects.
   - Manual approval is required for deploying to the Prod environment to ensure proper verification.

#### Conclusion
ADF Tools offer a more flexible and efficient approach to deploying Azure Data Factory projects, especially in environments with multiple teams. By allowing selective deployment, ADF Tools resolve many issues inherent in ARM template-based CI/CD pipelines.

---
