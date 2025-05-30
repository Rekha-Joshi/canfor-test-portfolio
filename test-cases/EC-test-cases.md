### Scenario 1: Verify new employee creation in EC with all mandatory fields  
**Expected Result**:  
- New hire is created successfully in EC  
- All mandatory fields (e.g., name, ID, role) are saved correctly  
- Employee appears in the employee directory  

---

### Scenario 2: Update employee personal details via EC ESS portal  
**Expected Result**:  
- Employee can log in to ESS and update personal details such as address and contact number  
- Changes are saved without error  
- Updated information is reflected in the employee profile and audit log  

---

### Scenario 3: Confirm job change (e.g., promotion or transfer) updates employee profile  
**Expected Result**:  
- Job title, department, and position details are updated accurately  
- Effective date is reflected correctly  
- Historical job data is retained in profile  

---

### Scenario 4: Validate pay code change (e.g., hourly to salaried) updates compensation details  
**Expected Result**:  
- Compensation info is updated with new pay code  
- Pay group, pay frequency, or salary type reflects the change  
- Employee compensation history shows the update  

---

### Scenario 5: Submit leave request (e.g., vacation, sick) via EC ESS portal  
**Expected Result**:  
- Employee selects leave type and date range  
- Leave request is submitted successfully  
- Confirmation message is shown to employee  
- Request appears in pending approvals for the manager  

---

### Scenario 6: Verify supervisor approval of leave request in EC updates request status
**Expected Result**:

- Supervisor logs in and approves the employee’s leave request
- Leave request status changes to “Approved” in EC
- Leave balance is updated accordingly
- Employee sees updated status in ESS portal

---

### Scenario 7: Confirm rejection of leave request in EC triggers employee notification
**Expected Result**:

- Supervisor rejects the leave request via EC MSS portal
- Leave request status changes to “Rejected”
- Employee receives notification (email or system alert) about rejection
- Leave balance remains unchanged

---

### Scenario 8: Test leave balance validation prevents submission exceeding available days
**Expected Result**:

- Employee attempts to submit leave request exceeding available leave balance
- System displays an error message preventing submission
- Leave request is not created until balance is sufficient
- Leave balance remains unchanged

---

### Scenario 9: Verify employee termination in EC updates employment status correctly
**Expected Result**:

- Employee termination is processed with correct effective date
- Employment status changes to “Terminated” or equivalent in EC
- Employee profile no longer appears in active employee lists
- Payroll and benefits termination workflows are triggered

---

### Scenario 10: Test role-based access restricts managers from editing employee-only fields
**Expected Result**:

- Manager logs into EC MSS portal
- Manager attempts to edit fields designated as employee-only (e.g., personal banking info)
- System restricts access and does not allow changes
- Appropriate error message or access denial is shown