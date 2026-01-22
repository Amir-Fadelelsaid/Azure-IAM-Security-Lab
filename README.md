# Azure-IAM-Security-Lab

Hands-on Azure IAM lab demonstrating identity-first security, MFA enforcement,
RBAC at resource and subscription scope, and Sentinel onboarding.

## Overview
This lab demonstrates identity-first cloud security in Microsoft Azure, focusing on
authentication, least privilege access, RBAC enforcement, and secure monitoring foundations.

The lab intentionally validates **deny-by-default behavior** before allowing access,
aligning with Zero Trust principles.

---

## What This Lab Proves

- Identity-first cloud security
- MFA enforcement using Microsoft Authenticator
- Azure RBAC at subscription and resource-group scope
- Least privilege access validation (deny → allow)
- Secure onboarding of Log Analytics and Microsoft Sentinel
- Zero Trust thinking applied to cloud resources

---

## Environment

- Cloud Provider: Microsoft Azure
- Subscription: Azure subscription 1
- Resource Group: `rg-security-lab`
- Region: East US 2
- Directory: Default Entra ID tenant

---

## Key Actions Performed

### Identity & Authentication
- Forced password reset on first login
- Configured Microsoft Authenticator (MFA)
- Verified secure sign-in with cloud user

### Authorization & RBAC
- Observed access denial when permissions were missing
- Reviewed role assignments at subscription scope
- Validated IAM boundaries at resource group level

### Monitoring Foundation
- Deployed Log Analytics Workspace (`IAM-security-lab`)
- Onboarded workspace to Microsoft Sentinel
- Verified Sentinel connection in Microsoft Defender

---

## Evidence

All screenshots are provided in the `/screenshots` directory in chronological order,
showing authentication setup, RBAC behavior, and secure service onboarding.

---

## Next Steps (Planned)

- RBAC role switching (Reader → Contributor)
- Explicit Zero Trust deny/allow testing
- Activity Log and Sign-In Log validation

![IAM Password Reset Enforcement](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/bd61411a8aa5f5559b259e971b78af3b41aeaf22/Iam%20Password%20reset.png)
This lab intentionally started with restricted access to validate
Azure’s deny-by-default security model.

Access failures were observed before RBAC permissions were reviewed,
confirming correct enforcement of least privilege.

Only after validation were monitoring services onboarded,
ensuring identity and authorization were established first.

### IAM Authentication – MFA Enforcement

![IAM authenticate](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/2a30d1406ce2b625f53bb8aa33c97ba26f3c6f35/IAM%20authenticate.png)

Azure enforced multi-factor authentication during first-time sign-in, requiring Microsoft Authenticator enrollment before access was granted.

![MFA Enforcement - Microsoft Authenticator Added](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/32a8b40f827183a454083fdbb48022cb9b3f3224/Iam%20Authenticator%20added.png)
This screenshot confirms successful multi-factor authentication (MFA) enrollment for a cloud user using Microsoft Authenticator.  
It validates strong authentication enforcement as part of an identity-first, Zero Trust security model in Azure.

![Cloud User Login After MFA](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/30d5ac862081b8c0aabf78b8bd9f4c711ba508a3/IAM%20logged%20in%20Azure%20with%20Cloud%20user.png?raw=true)

This screenshot shows a successful Azure portal login using a cloud user account after multi-factor authentication was enforced. It confirms identity verification was completed prior to authorization decisions, validating the authentication portion of the IAM process.

![RBAC Access Denied](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/1f9448b30cb2cd33987c5c325f911e593a49221f/IAM%20Logs%20dont%20have%20permission.png)
This screenshot demonstrates Azure Role-Based Access Control (RBAC) enforcement. Although the cloud user was authenticated via MFA, they were denied access to the storage logs container due to insufficient permissions. This confirms that authentication (identity) does not imply authorization (access), enforcing least privilege.

![Log Analytics Workspace Deployment Complete](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/d092ca2104f7f4614257b7f48b15feb705babb9f/IAM%20Log%20Analytics%20work%20space%20completed.png)
Shows successful deployment of the Log Analytics Workspace used for centralized logging and monitoring in the IAM security lab.

![Subscription IAM Role Assignments](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/6f5562aa9acaeab0f900fb75398528903d19f2ad/IAM%20Role%20Assignment%20Page%20.png)
This screenshot shows the Azure subscription’s Access control (IAM) page, listing role assignments. It confirms which identities and service principals have been granted roles (such as Owner and Microsoft Sentinel Contributor) at the subscription scope, validating RBAC and least-privilege access controls.

![Resource Group IAM Scope](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/65f6073369db877522b5bfa2b78d212e8aad799b/IAM%20RG%20Security%20Lab%20resource%20group.png)
This screenshot shows the `rg-security-lab` resource group, illustrating how Azure IAM can be scoped at the resource group level. This limits access to only the resources required, reducing blast radius and enforcing least-privilege access controls.

![Subscription Overview](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/b9d0642f921117247ab11a6394a8e1d8d6a06709/IAM%20Azure%20Subscription%20Overview.png)
This screenshot shows the Azure Subscription overview for the signed-in user. It confirms the subscription name, ID, and that the user is authenticated in the Default Directory with appropriate role context, providing baseline visibility into the environment before applying RBAC and resource-level controls.

![Containers View](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/098eb89c302b958ac3bdd3999e56e8cc8cacc7c0/Iam%20containers.png)
Displays the storage account container list accessible to the cloud user, demonstrating scoped visibility before attempting restricted actions like log access.

![Log Analytics in Resource Group](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/098eb89c302b958ac3bdd3999e56e8cc8cacc7c0/IAM%20Log%20Analytics%20IAM%20Security%20LAB.png)
Shows the Log Analytics workspace deployed within the `rg-security-lab` resource group, establishing a monitoring foundation under the scoped IAM model.

![Sentinel Workspace Connected](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/098eb89c302b958ac3bdd3999e56e8cc8cacc7c0/IAM%20Microsoft%20Defender%20Worspace%20connected.png)
Shows the Microsoft Sentinel workspace connected to Microsoft Defender for Cloud, indicating extended security integration within the scoped environment.



