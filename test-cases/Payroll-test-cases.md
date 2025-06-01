## Glossary

* Info Type: Infotypes are the screens or tables where employee data is stored (e.g., address, pay)
* Wage Type: A specific component of pay (e.g., basic salary, bonus, deduction) used in payroll.
* Infotype 0008:	Basic Pay – stores salary, pay scale, and wage type data for employees.
* Infotype 0009:	Bank Details – stores bank account info for direct deposit.
* Infotype 0014: Recurring Payments/Deductions (like monthly deductions or allowances e.g loan)
* Infotype 0015:	Additional Payments – used to enter one-time payments like bonuses.

| Concept | Example	| What It Means |
| --------|------------|---------------|  
| Infotype	| 0008	| Basic Pay infotype — stores base salary info|
| Infotype	| 0015	| Additional Payments infotype — stores one-time payments|
| Wage Type	| 1000	| Basic Pay (a wage type stored in Infotype 0008)|
| Wage Type	| 2010	| Overtime Pay (a wage type, often in Infotype 0015)|
| Wage Type	| 3010	| Loan Deduction (recurring deduction in Infotype 0014)|
| Wage Type	| 9050	| Garnishment (deduction wage type in Infotype 0014 or 0015)|

* Retroactive Payroll:	A payroll run that reprocesses past periods due to data changes (e.g., backdated pay raise).
* Garnishment:	A court-ordered deduction from an employee's pay (e.g., child support).
* Off-Cycle Payroll:	A separate payroll run outside the regular schedule (e.g., bonus, missed payment).
* Payroll Area:	A group of employees processed together in a payroll run (e.g., monthly staff).


### Scenario 1: Add an Off-Cycle Payment for an Employee  
**Expected Result**:  
- Off-cycle run is created for the selected employee  
- One-time payment (e.g., bonus or missed pay) is added successfully  
- Payment is processed in the off-cycle payroll run  
- Pay slip reflects the correct additional payment amount  

---

### Scenario 2: Validate Core Infotypes Required for Payroll Run (0000, 0001, 0008, etc.)  
**Expected Result**:  
- Infotypes 0000 (Actions), 0001 (Org Assignment), and 0008 (Basic Pay) are present and complete  
- Data in each infotype is valid (e.g., pay scale group, cost center)  
- Payroll run does not return missing data or error messages  

---

### Scenario 3: Test Loan Deduction Processing for an Employee  
**Expected Result**:  
- Loan master data is entered correctly in the loan infotype  
- Payroll run deducts the loan installment as scheduled  
- Deduction amount appears correctly in pay slip  
- Loan balance is updated after each payroll run  

---

### Scenario 4: Verify One-Time Payment Integration from EC to Payroll  
**Expected Result**:  
- One-time payment entered in EC is replicated to Payroll successfully  
- Infotype 0015 (Additional Payments) is updated  
- Payroll run includes the additional amount in gross pay  
- Pay slip reflects correct one-time payment details  

---

### Scenario 5: Change Employee Bank Info (Infotype 0009) and Validate in Payroll  
**Expected Result**:  
- Updated bank account details are saved successfully in Infotype 0009  
- Payroll run reflects the updated payment method and bank account  
- Pay slip shows new account number (masked)  
- EFT file is generated with updated bank info for the employee  
### Scenario 6: Simulate Regular Payroll Run and Verify Gross to Net Calculation  
**Expected Result**:  
- Payroll simulation completes without errors  
- Gross salary, deductions, and net pay are calculated correctly  
- Results match expected values based on employee data  
- Pay slip reflects all relevant components (earnings, taxes, deductions)

---

### Scenario 7: Check Retroactive Payroll Calculation After Pay Code Update  
**Expected Result**:  
- Historical pay code change triggers retro calculation  
- Retro differences are included in the next payroll run  
- Retro amounts are shown on pay slip with reference period  
- Payroll log shows correct retro processing steps  

---

### Scenario 8: Validate Tax Calculation for Different Provinces (e.g., BC vs. AB)  
**Expected Result**:  
- Employee tax withholding reflects correct provincial tax rules  
- Payroll calculates accurate federal and provincial deductions  
- Pay slip includes proper tax codes and amounts based on location  
- Tax reporting fields (e.g., T4) are updated accordingly  

---

### Scenario 9: Test Garnishment Deduction Setup and Execution  
**Expected Result**:  
- Garnishment details (amount, type, court order) are set up correctly  
- Payroll deducts garnishment in specified sequence  
- Net pay is adjusted after garnishment  
- Garnishment details appear in pay slip and are audit-traceable  

---

### Scenario 10: Confirm Final Settlement on Employee Termination  
**Expected Result**:  
- Final pay run includes all earned salary, bonuses, and leave payout  
- Statutory deductions and tax adjustments are calculated correctly  
- Termination infotypes (e.g., 0000) are completed  
- Pay slip shows full final settlement breakdown  
