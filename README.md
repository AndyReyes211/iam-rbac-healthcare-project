# iam-rbac-healthcare-project
self-directed IAM project: RBAC policy design for a fictional healthcare org
# IAM RBAC Project: Healthcare Access Control Design

## Overview
As part of my transition into cybersecurity, I built a self-directed IAM project: a role-based access control (RBAC) policy for a fictional healthcare organization ("Regional Health Clinic"). This was a chance to apply least-privilege principles and think through real access-control tradeoffs beyond what a certificate alone covers.

## Scenario
Regional Health Clinic is a fictional healthcare organization with five departments:
- Clinical Staff
- Front Desk / Admin
- Finance
- HR
- IT

## Approach
The project applies two core principles across all roles:
- **Least privilege** — each role gets only the access needed to do its job, nothing more
- **PHI isolation** — protected health information is restricted to roles that clinically or legally require it

## What's in this repo
- [`docs/role-matrix.md`](docs/role-matrix.md) — role definitions, access levels, and justifications per department
- [`docs/access-review-procedures.md`](docs/access-review-procedures.md) — how access would be periodically reviewed and revalidated

## Note
This is a self-directed practice project built after completing the Google Cybersecurity Certificate (June 2026), created to apply IAM concepts hands-on rather than just study them.

## Part 2: AWS Implementation\nI extended this project by implementing the RBAC model in AWS IAM, testing access boundaries with the Policy Simulator, and enabling MFA. See the [full case study](docs/aws-iam-case-study.md)
