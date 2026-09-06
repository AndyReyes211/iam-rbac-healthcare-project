# Role Access Matrix — Regional Health Clinic

| Department       | Role                  | System Access                          | PHI Access        | Justification |
|-------------------|-----------------------|------------------------------------------|--------------------|----------------|
| Clinical Staff    | Physician / Nurse     | EHR (full read/write), scheduling       | Full (assigned patients only) | Requires complete patient records to deliver care |
| Front Desk / Admin| Receptionist          | Scheduling system, patient contact info | None (no clinical PHI) | Needs contact/scheduling data only, not clinical records |
| Finance           | Billing Specialist    | Billing system, insurance claims        | Limited (billing-relevant PHI only, e.g. diagnosis codes for claims) | Needs enough clinical data to process claims, not full records |
| HR                | HR Generalist         | HR/payroll system, employee records     | None | No clinical role; access limited to employee data |
| IT                | IT Support / SysAdmin | System-level access (infrastructure, backups) | None (technical access only, no direct PHI viewing) | Needs to maintain systems, not view patient data directly |

## Notes
- Access is role-based, not individual-based — access changes automatically when someone changes roles.
- PHI access follows a "need to treat/process" standard, not blanket department-wide access.
- IT access is scoped to system administration, with audit logging enabled — IT does not need standing access to PHI to do their job.
