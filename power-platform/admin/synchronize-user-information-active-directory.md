---
redirect_url: https://docs.microsoft.com/dynamics365/customerengagement/on-premises/admin/synchronize-user-information-active-directory
title: "Synchronize user information with Active Directory  | MicrosoftDocs"
description: Synchronize user information with Active Directory
author: jimholtz
manager: kvivek
ms.service: power-platform
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: jimholtz
search.audienceType: 
  - admin
search.app: 
  - D365CE
  - PowerApps
  - Powerplatform
---
# Synchronize user information with Active Directory

[!INCLUDE [cc-settings-moving](../includes/cc-settings-moving.md)] 

Model-driven apps in Dynamics 365, such as Dynamics 365 Sales and Customer Service, supports two methods for authenticating users:  
  
- Integrated [!INCLUDE[pn_Windows_Authentication](../includes/pn-windows-authentication.md)]  
  
- Claims-based authentication  
  
By default, customers who purchase model-driven apps in Dynamics 365 and deploy it on-premises use [!INCLUDE[pn_Windows_Authentication](../includes/pn-windows-authentication.md)]. These customers also can set up claims-based authentication for Internet-facing deployments (IFDs) of the product.  
  
With integrated [!INCLUDE[pn_Windows_Authentication](../includes/pn-windows-authentication.md)], each user record must be associated with a user account in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] to enable log on to model-driven apps in Dynamics 365. When the user records are associated, model-driven apps in Dynamics 365 automatically reads and stores other information about the user record (including the first and last name, the email address, and the globally unique identifier, or GUID) from the [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] directory service.  
  
However, changes to the [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] information associated with a specific user can create discrepancies with the information maintained in model-driven apps in Dynamics 365, thereby preventing the user from accessing model-driven apps in Dynamics 365. Specifically, if value of the **User SamAccountName logon** attribute in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] changes for a user, the corresponding user information in model-driven apps in Dynamics 365 won’t match and the user won’t be able log on.  
  
To ensure that the user can successfully log on to model-driven apps in Dynamics 365, you must update the information in the user record so that it matches the detail in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)].  
  
Before you start, be sure to record the value of the **User SamAccountName logon** attribute for the affected user before updating the corresponding user record.  
  
> [!NOTE]
>  For information about synchronizing model-driven apps in Dynamics 365 with [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)], see the blog post [How to Synchronize CRM Online with your Active Directory](https://blogs.msdn.com/b/crm/archive/2013/07/18/how-to-synchronize-crm-online-with-your-active-directory.aspx).  
  
1. [!INCLUDE[proc_settings_security](../includes/proc-settings-security.md)]  
  
2. Choose **Users**.  
  
3. In the list of users, choose to select the user record you want to update, and then choose **Edit**.  
  
4. In the **User Name** text box, type an [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] user name that isn’t used by any user record.  
  
   > [!IMPORTANT]
   >  If you specify a user name that already exists in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)], model-driven apps in Dynamics 365 will try to map the user to the updated user in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)], and when it locates an existing record with the same GUID, the mapping will fail.  
  
    If all the user accounts in [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] are used by user records, create a temporary [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)] user account.  
  
5. Save the user record, and then in the **User Name** text box, type in the **User SamAccountName logon** value that appears for the user [!INCLUDE[pn_Active_Directory](../includes/pn-active-directory.md)], which you recorded prior to starting this procedure.  
  
6. Choose **Save and Close**.  
  
### See also  
 [Add or remove territory members](../admin/add-remove-territory-members.md)
