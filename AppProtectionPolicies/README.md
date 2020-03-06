
# App Protection Policy Data Protection Framework

As more organizations implement mobile device strategies for accessing work or school data, protecting against data leakage becomes paramount. Intune's mobile application management solution for protecting against data leakage is App Protection Policies (APP). APP are rules that ensure an organization's data remains safe or contained in a managed app, regardless of whether the device is enrolled. For more information, see [App protection policies overview](https://docs.microsoft.com/intune/apps/app-protection-policy).

When configuring App Protection Policies, the number of various settings and options enable organizations to tailor the protection to their specific needs. Due to this flexibility, it may not be obvious which permutation of policy settings are required to implement a complete scenario. To help organizations prioritize hardening endeavors, Microsoft has introduced a new taxonomy for its APP data protection framework for mobile app management.

The APP data protection configuration framework is organized into three distinct configuration scenarios:

- Level 1 enterprise basic data protection – Microsoft recommends this configuration as the minimum data protection configuration for an enterprise device.

- Level 2 enterprise enhanced data protection – Microsoft recommends this configuration for devices where users access sensitive or confidential information. This configuration is applicable to most mobile users accessing work or school data. Some of the controls may impact user experience.

- Level 3 enterprise high data protection – Microsoft recommends this configuration for devices run by an organization with a larger or more sophisticated security team, or for specific users or groups who are at uniquely high risk (as one example, one organization identified users who handle data whose theft would directly and seriously impact their stock price). An organization likely to be targeted by well-funded and sophisticated adversaries should aspire to this configuration.

For more information, see [Data protection framework using app protection policies ](https://docs.microsoft.com/intune/apps/app-protection-framework).

## Prerequisites

Importing the JSON templates into an Intune tenant requires the following:

- Install the AzureAD PowerShell module by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt
- An Intune tenant which supports the Azure Portal with a production or trial license (https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)
- Using the Microsoft Graph APIs to configure Intune controls and policies requires an Intune license.
- An account with permissions to administer the Intune Service
- PowerShell v5.0 on Windows 10 x64
- First time usage of these scripts requires a Global Administrator of the Tenant to accept the permissions of the application

## Steps

1. Download the [ManagedAppPolicy_Import_FromJSON.ps1](https://github.com/microsoftgraph/powershell-intune-samples/blob/master/AppProtectionPolicy/ManagedAppPolicy_Import_FromJSON.ps1) script.
2. Download the JSON templates in this directory.
3. Open Windows PowerShell.
4. Navigate to the directory containing the script and execute ManagedAppPolicy_Import_FromJSON.ps1.
5. The first time you run the script, you will be asked to authenticate with Azure Active Directory:
    ```
    Please specify your user principal name for Azure Authentication:
    ```
    Once you have provided a user principal name a popup will open prompting for your password. After a successful authentication with Azure Active Directory the user token will last for an hour, once the hour expires within the PowerShell session you will be asked to re-authenticate.

6. If you are running the script for the first time against your tenant a popup will be presented stating:

    ```
    Microsoft Intune PowerShell needs permission to:

    * Sign you in and read your profile
    * Read all groups
    * Read directory data
    * Read and write Microsoft Intune Device Configuration and Policies (preview)
    * Read and write Microsoft Intune RBAC settings (preview)
    * Perform user-impacting remote actions on Microsoft Intune devices (preview)
    * Sign in as you
    * Read and write Microsoft Intune devices (preview)
    * Read and write all groups
    * Read and write Microsoft Intune configuration (preview)
    * Read and write Microsoft Intune apps (preview)
    ```
    Note: If your user account is targeted for device based conditional access your device must be enrolled or compliant to pass authentication.

7. The script will prompt you to enter the full path to the JSON template file. Enter the full path escaping with quotation marks; for example "C:\Framework\JSON\level-1-enterprise-basic-data-protection-Android.json"

    ```
    Please specify a path to a JSON file to import data from e.g. C:\IntuneOutput\Policies\policy.json:
    ```
8. Verify that the script import is successful by reviewing the policy within Microsoft Endpoint Manager.


## Additional resources

- [Intune Graph Samples](https://github.com/microsoftgraph/powershell-intune-samples)
- [Data protection framework using app protection policies](https://docs.microsoft.com/intune/apps/app-protection-framework)

## Copyright

Copyright (c) 2020 Microsoft Corporation. ALl rights reserved.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.