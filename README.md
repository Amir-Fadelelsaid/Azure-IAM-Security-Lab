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

![Subscription IAM Role Assignments](https://github.com/Amir-Fadelelsaid/Azure-IAM-Security-Lab/blob/6f5562aa9acaeab0f900fb75398528903d19f2ad/IAM%20Role%20Assignment%20Page%20.png)
This screenshot shows the Azure subscription’s Access control (IAM) page, listing role assignments. It confirms which identities and service principals have been granted roles (such as Owner and Microsoft Sentinel Contributor) at the subscription scope, validating RBAC and least-privilege access controls.
