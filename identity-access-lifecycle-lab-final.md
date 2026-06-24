# Project 2: Identity & Access Lifecycle Lab

## Microsoft Entra ID + Azure RBAC

## Project Purpose

Build a hands-on identity and access management lab that demonstrates user provisioning, access modification, deprovisioning, group-based permissions, least-privilege access, Azure RBAC, MFA/security defaults awareness, manual access request tracking, manual access review tracking, and GitHub documentation.

## Career Goal

This project bridges my DoD identity credentialing and access-management experience with commercial IAM tools and concepts used in enterprise environments.

My goal is to show that I understand identity lifecycle management, access control, documentation, least privilege, and basic Azure access management in a way that applies to cloud support, IT support, systems administration, and junior IAM roles.

## Tools Used

* Microsoft Entra ID
* Azure Portal
* Azure RBAC
* Microsoft Entra security groups
* Azure resource group
* Manual access request tracker
* Manual access review tracker
* GitHub documentation
* Screenshots for proof of work

## Scenario

A fictional company, **DeLeon Energy Services**, needs a basic IAM workflow for employees joining the company, changing departments, and leaving the organization.

The company wants access assigned through security groups instead of direct user assignments whenever possible. Access should follow least-privilege principles, and all access requests, changes, and removals should be documented.

## Lab Objectives

1. Create test users in Microsoft Entra ID.
2. Create security groups based on job roles.
3. Assign users to groups using least-privilege principles.
4. Simulate a joiner workflow by provisioning a new user.
5. Simulate a mover workflow by changing group access.
6. Simulate a leaver workflow by disabling sign-in and removing access.
7. Assign Azure RBAC Reader access to a resource group.
8. Document MFA and security defaults awareness.
9. Create a manual access request tracker.
10. Create a manual access review tracker.
11. Capture screenshots for proof.
12. Publish documentation to GitHub.

## Cost Control Note

This lab is designed to be completed for free.

To avoid charges:

* Do not deploy virtual machines.
* Do not deploy storage accounts.
* Do not deploy databases.
* Do not enable Microsoft Sentinel.
* Do not create Log Analytics workspaces.
* Do not use paid Microsoft Entra ID Governance access reviews.
* Use manual documentation for access requests and access reviews.

The Azure resource group is used only as a scope for Azure RBAC Reader assignment.

## Fictional Company

**Company Name:** DeLeon Energy Services
**Environment:** Small energy services company
**IAM Need:** Basic joiner, mover, leaver workflow
**Security Goal:** Assign only the access users need to perform their job duties

## Test Users

| User | Department | Scenario | Name Meaning |
|---|---|---|---|
| Arya Keyholder | IT Support | Joiner | New IT support user who receives access through role-based group membership |
| Tyrion Ledger | Operations to Finance | Mover | Department transfer into finance; “Ledger” ties to finance access |
| Penny Wise | Finance | Leaver | Finance user being deprovisioned; name ties to money and access cleanup |
| Roland Reader | Field Support | Standard user / Azure Reader | Field user with read-only Azure visibility through the RBAC Reader role |

## Security Groups

| Group Name           | Purpose                               |
| -------------------- | ------------------------------------- |
| DES-IT-Support       | Access for IT support users           |
| DES-Operations       | Access for operations users           |
| DES-Finance          | Access for finance users              |
| DES-Field-Support    | Access for field support users        |
| DES-Azure-RG-Readers | Read-only Azure resource group access |

## Azure Resource Group

**Resource Group Name:** `RG-DES-IAM-LAB`

The resource group is used only to demonstrate Azure RBAC role assignment.

No paid Azure resources should be deployed inside the resource group.

## Azure RBAC Assignment

Assign the **Reader** role to the security group:

**Group:** `DES-Azure-RG-Readers`
**Role:** `Reader`
**Scope:** `RG-DES-IAM-LAB`

This demonstrates read-only access to Azure resources without giving users permission to create, modify, or delete resources.

## Workflow 1: Joiner

**Scenario:** Arya Keyholder joins DeLeon Energy Services as an IT Support Technician.

**Steps:**

1. Create Arya Keyholder as a new Microsoft Entra ID user.
2. Add Arya to `DES-IT-Support`.
3. Add Arya to `DES-Azure-RG-Readers`.
4. Confirm group membership.
5. Document the access request in the manual access request tracker.
6. Capture screenshots.

**Result:**
Arya was provisioned with access based on her role. Access was assigned through groups using least-privilege principles.

## Workflow 2: Mover

**Scenario:** Tyrion Ledger moves from Operations to Finance.

**Steps:**

1. Review Tyrion’s current group membership.
2. Remove Tyrion from `DES-Operations`.
3. Add Tyrion to `DES-Finance`.
4. Confirm updated group membership.
5. Document the change in the manual access request tracker.
6. Document the review in the manual access review tracker.
7. Capture screenshots.

**Result:**
Tyrion’s access was updated to match his new department, and access he no longer needed was removed.

## Workflow 3: Leaver

**Scenario:** Penny Wise leaves DeLeon Energy Services.

**Steps:**

1. Locate Penny Wise’s Microsoft Entra ID account.
2. Block sign-in for the user account.
3. Remove Penny from assigned security groups.
4. Confirm group access removal.
5. Document the deprovisioning action.
6. Capture screenshots.

**Result:**
Penny was deprovisioned, sign-in was blocked, and group access was removed to reduce security risk.

## Standard User / Reader Access

**Scenario:** Roland Reader works in Field Support and only needs read-only visibility into the Azure resource group.

**Steps:**

1. Create Roland Reader as a Microsoft Entra ID user.
2. Add Roland to `DES-Field-Support`.
3. Add Roland to `DES-Azure-RG-Readers`.
4. Assign the `Reader` role to `DES-Azure-RG-Readers` at the resource group scope.
5. Confirm the RBAC assignment.
6. Capture screenshots.

**Result:**
Roland received read-only access through group-based Azure RBAC without direct user assignment.

## MFA and Security Defaults Awareness

This lab includes documentation of Microsoft Entra security defaults and MFA awareness.

The purpose is to show awareness of identity security controls, not to configure paid Conditional Access policies.

Document:

* Where security defaults are reviewed in Microsoft Entra ID
* Why MFA helps protect user accounts
* Why administrators and privileged users need stronger sign-in protection
* Why identity security settings should be reviewed regularly

## Manual Access Request Tracker

| Request ID | User | Request Type | Access Requested | Business Reason | Approval Status | Action Taken | Date |
|---|---|---|---|---|---|---|---|
| REQ-001 | Arya Keyholder | Joiner | DES-IT-Support, DES-Azure-RG-Readers | New IT Support Technician | Approved | User created and groups assigned | TBD |
| REQ-002 | Tyrion Ledger | Mover | Remove DES-Operations, Add DES-Finance | Department transfer | Approved | Group membership updated | TBD |
| REQ-003 | Penny Wise | Leaver | Remove all access | Employee separation | Approved | Sign-in blocked and groups removed | TBD |
| REQ-004 | Roland Reader | Standard Access | DES-Field-Support, DES-Azure-RG-Readers | Field Support user needs read-only Azure visibility | Approved | User added to field support and reader groups | TBD |

## Manual Access Review Tracker

| Review ID | User | Current Access | Access Still Needed? | Reviewer Decision | Action Taken | Review Date |
|---|---|---|---|---|---|---|
| REV-001 | Arya Keyholder | DES-IT-Support, DES-Azure-RG-Readers | Yes | Keep access | No change | TBD |
| REV-002 | Tyrion Ledger | DES-Finance | Yes | Keep updated access | Previous Operations access removed | TBD |
| REV-003 | Penny Wise | No active groups | No | Remove access | Sign-in blocked and access removed | TBD |
| REV-004 | Roland Reader | DES-Field-Support, DES-Azure-RG-Readers | Yes | Keep read-only access | No change | TBD |

## Screenshots to Capture

Save screenshots in a `/screenshots` folder.

Recommended screenshots:

1. Microsoft Entra ID test users
2. Security groups created
3. Joiner user created
4. Joiner group membership
5. Mover before group change
6. Mover after group change
7. Leaver sign-in blocked
8. Leaver group access removed
9. Azure resource group
10. Azure RBAC Reader role assignment
11. Security defaults / MFA awareness screen
12. Manual access request tracker
13. Manual access review tracker

## Recommended GitHub Repository Structure

```text
identity-access-lifecycle-lab/
│
├── README.md
├── docs/
│   ├── access-request-tracker.md
│   ├── access-review-tracker.md
│   ├── joiner-workflow.md
│   ├── mover-workflow.md
│   ├── leaver-workflow.md
│   └── lessons-learned.md
│
└── screenshots/
    ├── 01-entra-users.png
    ├── 02-security-groups.png
    ├── 03-joiner-user-created.png
    ├── 04-joiner-group-membership.png
    ├── 05-mover-before.png
    ├── 06-mover-after.png
    ├── 07-leaver-signin-blocked.png
    ├── 08-leaver-groups-removed.png
    ├── 09-resource-group.png
    ├── 10-rbac-reader-assignment.png
    ├── 11-security-defaults-awareness.png
    ├── 12-access-request-tracker.png
    └── 13-access-review-tracker.png
```

## Skills Demonstrated

* Microsoft Entra ID administration
* User provisioning
* Security group management
* Group-based access control
* Azure RBAC
* Azure resource group scope assignment
* Least-privilege access
* Joiner, mover, and leaver workflows
* Account deprovisioning
* Access request documentation
* Access review documentation
* MFA and security defaults awareness
* Technical documentation
* GitHub portfolio publishing

## Resume Bullet

Built a Microsoft Entra ID and Azure RBAC lab simulating enterprise IAM operations, including user provisioning, group-based access control, joiner/mover/leaver workflows, least-privilege permissions, MFA/security defaults awareness, manual access reviews, and deprovisioning documentation.

## Interview Summary

I built this lab to connect my DoD identity credentialing and access-management experience with commercial IAM tools.

The project demonstrates how I understand identity lifecycle management, access requests, Azure RBAC, least privilege, documentation, and deprovisioning using Microsoft Entra ID and Azure.

In the lab, I created test users, assigned access through security groups, simulated joiner, mover, and leaver workflows, assigned Azure RBAC Reader access to a resource group, documented security defaults awareness, and created manual access request and access review trackers.

This helped me practice the type of identity and access work used in IT support, cloud support, systems administration, and junior IAM roles.

## Lessons Learned

This lab reinforced that access should be assigned based on job role and removed when no longer needed. It also showed why group-based access is easier to manage than assigning permissions directly to individual users.

The project helped me understand how identity lifecycle management connects technical administration, documentation, security, and accountability.
