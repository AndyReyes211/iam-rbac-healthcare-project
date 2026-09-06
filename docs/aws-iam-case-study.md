# Hands-On IAM Project: AWS Implementation

## Overview
As a follow-up to my [RBAC design project](https://github.com/AndyReyes211/iam-rbac-healthcare-project), I implemented the same role-based access control model using AWS IAM — moving from policy design on paper to a working, testable access control system.

## What I Built
Using a free AWS account, I recreated the five-department structure from my original healthcare org scenario (Regional Health Clinic):

| Group | Policy Assigned | Access Level |
|-------|-----------------|---------------|
| ClinicalStaff | AmazonS3FullAccess | Full read/write (patient records) |
| FrontDeskAdmin | AmazonS3ReadOnlyAccess | Read-only (no edit/delete) |
| Finance | Billing | Billing/invoice access only |
| HR | IAMReadOnlyAccess | View-only into account structure |
| IT | PowerUserAccess | Broad system access, excluding IAM management |

For each group, I created a test IAM user (e.g. `clinical-staff-test1`) to validate that permissions were applied correctly.

## Testing Least Privilege
Using AWS's IAM Policy Simulator, I verified that access differences actually worked as designed:

- **FrontDeskAdmin** was denied `s3:PutObject` (write) but allowed `s3:GetObject` (read) — confirming read-only access.
- **ClinicalStaff** was allowed `s3:PutObject`, contrasting directly with FrontDeskAdmin's denial on the same action.
- **IT** (PowerUserAccess) was allowed broad actions but denied `iam:CreateUser` — demonstrating that even the most privileged group can't grant itself additional access, a real-world separation-of-duties principle.
- **HR** (IAMReadOnlyAccess) was allowed `iam:ListUsers` but denied `iam:CreateUser` — confirming view-only access.

## Adding a Security Control: MFA
To go beyond access policy alone, I enabled multi-factor authentication (MFA) on the IT test user using an authenticator app, demonstrating the ability to configure — not just describe — a core security control.

## Key Takeaway
This project moved my understanding of least-privilege access control from theoretical to practical: I didn't just define what access each role *should* have, I implemented it, tested it, and confirmed the boundaries actually held — including an important nuance where broad system access still doesn't include the ability to self-escalate permissions.

## Note
This is a self-directed practice project, built to apply IAM concepts hands-on using AWS's free tier.
