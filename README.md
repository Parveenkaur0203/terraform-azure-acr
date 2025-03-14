# Terraform Module: Azure Container Registry (ACR)

This Terraform module provisions an **Azure Container Registry (ACR)**, a managed Docker registry service used to store and manage container images in Azure.

---

## Table of Contents

- [Usage](#usage)
- [Example Outputs](#example-outputs)
- [Inputs](#inputs)
- [Outputs](#outputs)
- [Providers](#providers)
- [Requirements](#requirements)
- [Notes](#notes)
- [License](#license)

---

## Usage

You can use this module to create an Azure Container Registry (ACR) with a **Basic SKU**. Below is an example:

```hcl
module "acr" {
  source              = "./path-to-module" # Replace this with the path or GitHub URL
  acr_name            = "myACR"
  resource_group_name = "myResourceGroup"
  location            = "eastus"
}

output "acr_id" {
  value = module.acr.acr_id
}

output "acr_login_server" {
  value = module.acr.login_server
}
```

## Inputs

The following variables must be set to use this module:

| Name | Description | Type | Default | Required |
| :-- | :-- | :-- | :-- | :-- |
| acr_name | The globally unique name of the Azure Container Registry. | string | n/a | Yes |
| resource_group_name | The name of the resource group for the registry. | string | n/a | Yes |
| location | The Azure region where the ACR will be provisioned. | string | n/a | Yes |


## Outputs

| Name | Description |
| :-- | :-- |
| acr_id | The ID of the created Azure Container Registry. |
| login_server | The DNS name for accessing the registry. |

### Example Outputs

Once provisioned, the module provides the following outputs:

- **ACR Resource ID**: The fully qualified ID of the created Azure Container Registry.
- **Login Server**: The DNS name for accessing the registry where container images are stored.


## Providers

This module requires the following Terraform provider:

- **[azurerm](https://registry.terraform.io/providers/hashicorp/azurerm/latest)** (Azure Resource Manager): Ensure you are using the latest version compatible with the module.


## Requirements

- **Terraform CLI version** `>= 1.0`
  
- **Azure CLI installed**
  - Required for local authentication (if using Service Principal credentials).
  
- **Active Azure Subscription**
  - Ensure that you have an active subscription in **Microsoft Azure**.


## Notes

- **SKU**: 
  The SKU for the registry is predefined as Basic for this module, which is suitable for development and small workloads. If you need a higher SKU (e.g., Premium), modify the main.tf file.

