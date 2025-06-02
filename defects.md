# Real Defects Encountered During SAP EC, Kronos, and Payroll Testing

This document captures real-world defects encountered during functional, integration, and end-to-end testing across SAP Employee Central (EC), Kronos Time & Attendance, and SAP Payroll. These examples demonstrate how deep domain understanding and cross-system validation can uncover critical issues before go-live.

---

## SAP Employee Central (EC)

### 1. Job Info Not Replicating to Payroll After Change
**Issue**: EC job change did not update Payroll  
**Cause**: Integration mapping for new job code missing  
**Impact**: Payroll processed outdated department and pay  
**Resolution**: Corrected integration mapping and reprocessed queue

---

### 2. Incorrect Time Recording Profile After Job Change
**Issue**: Job change didn’t update time recording profile  
**Cause**: Business rule did not trigger profile reassignment  
**Impact**: Kronos didn’t collect time; no hours sent to payroll  
**Resolution**: Updated rule to include new job families

---

### 3. Leave Request Exceeded Quota in EC ESS
**Issue**: Employee submitted more leave than allowed  
**Cause**: Leave balance validation failed in Time Off config  
**Impact**: Negative balance created; overpayment  
**Resolution**: Fixed validation rule, recalculated quota

---

### 4. New Hire Missing Mandatory Pay Group
**Issue**: New hire saved without Pay Group  
**Cause**: UI rule inactive on onboarding template  
**Impact**: Payroll replication failed  
**Resolution**: Made Pay Group mandatory and updated template

---

### 5. One-Time Payment in EC Not Reflected in Payroll
**Issue**: Bonus not visible in payroll  
**Cause**: Infotype 0015 wage type mapping broken  
**Impact**: Employee underpaid  
**Resolution**: Repaired mapping and retro-triggered

---

## Kronos (UKG)

### 6. Shift Premium Not Applied in Kronos
**Issue**: Night shift hours paid as regular  
**Cause**: Incorrect pay rule or work rule in Kronos  
**Impact**: Employee paid less than entitled  
**Resolution**: Corrected rule and re-exported hours

---

### 7. Kronos Export File Sent Wrong Hours to Payroll
**Issue**: Kronos UI showed correct pay, but file sent regular hours only  
**Cause**: Export logic ignored overtime split  
**Impact**: Payroll underpaid OT  
**Resolution**: Fixed interface mapping and pay code tags

---

### 8. Leave Approved in Kronos Not Reflected in Timesheet
**Issue**: Leave not applied in payroll  
**Cause**: Approved leave didn’t update timecard  
**Impact**: Payroll treated it as unpaid  
**Resolution**: Fixed the logic/rules in Kronos

---

### 9. Night Shift Hours Not Processed Correctly Across Midnight  
**Issue**: Night shift hours (e.g., 10:00 PM to 6:00 AM) were either split incorrectly or partially dropped in payroll  
**Cause**: Kronos configuration didn't handle cross-midnight shift valuation properly; hours after midnight were not mapped to the correct day  
**Impact**: Employees paid only for part of their shift or received incorrect shift premium  
**Resolution**: Updated work rule in Kronos to correctly span overnight shifts and applied cross-day pay rule logic; validated payroll entries against full shift duration  

---

### 10. On-Call Hours Sent as Regular Time
**Issue**: On-call not treated as premium  
**Cause**: Pay code not mapped to correct wage type  
**Impact**: Employee underpaid  
**Resolution**: Fixed Kronos-to-Payroll wage type mapping

---

## SAP Payroll

### 11. Bonus Payment Triggered Wrong Wage Type
**Issue**: Bonus appeared as base pay  
**Cause**: Wrong wage type used in IT0015  
**Impact**: Incorrect taxation and GL posting  
**Resolution**: Corrected infotype setup

---

### 12. Final Pay Missed Leave Payout
**Issue**: Accrued vacation not included in final pay  
**Cause**: Leave quotas not pulled during termination  
**Impact**: Legal and employee escalation  
**Resolution**: Updated schema and control record logic

---

### 13. Garnishment Deduction Exceeded Net Pay
**Issue**: Garnishment left employee with negative pay  
**Cause**: Missing validation of minimum net rule  
**Impact**: Payroll violation and employee grievance  
**Resolution**: Added net pay check in pre-processing

---

### 14. Retro Pay Skipped Job Change Adjustment
**Issue**: Backdated pay raise not included in retro run  
**Cause**: Infotype 0008 change didn’t split correctly  
**Impact**: Missed retro payment  
**Resolution**: Manually split infotype and re-ran payroll

---

## Cross-System Integration

### 15. Missing Pay Code Mapping Between Kronos and Payroll
**Issue**: Kronos sent valid entry, but Payroll dropped it  
**Cause**: New pay code lacked wage type mapping  
**Impact**: Missing hours in payroll  
**Resolution**: Added mapping in middleware and reprocessed

---

## Defect Logging, Tracking, and Retesting Process

- **Defect Management Tool**: Jira was used for logging, assigning, and tracking defects  
- **Triage Meetings**: Weekly triage meetings held with vendors and stakeholders  
- **UAT Defects**: Logged and prioritized by severity; retested after fixes  
- **Traceability**: All bugs linked to test cases using unique IDs in Excel  
- **Retesting Approach**:
  - Reproduced the issue in the same environment
  - Validated once fixed by vendors
  - Marked as "Closed/Fixed" once business users validated

---

✅ These real-world defects strengthened my ability to validate end-to-end flows across EC, Kronos, and Payroll — including edge cases, data mismatches, and configuration gaps.

