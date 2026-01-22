# Azure-IAM-Security-Lab

Hands-on Azure IAM lab demonstrating identity-first security, MFA enforcement,
RBAC at resource and subscription scope, and Sentinel onboarding.

# Azure IAM Security Lab

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
