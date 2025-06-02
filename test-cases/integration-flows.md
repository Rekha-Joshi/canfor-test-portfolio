### Scenario 1: New Hire in EC is Replicated to Payroll System  
**Expected Result**:  
- New employee data (name, ID, position, pay group, etc.) is created in EC  
- Replication to Payroll is successful  
- Employee appears in Payroll with correct infotypes (0000, 0001, 0007, 0008) populated  

---

### Scenario 2: Time Entry in Kronos is Transferred to Payroll for Processing  
**Expected Result**:  
- Employee time punches or hours are recorded in Kronos  
- Time data is approved and passed to Payroll  
- Payroll run includes imported hours and calculates gross pay correctly  

---

### Scenario 3: Pay Code Change in EC is Reflected in Both Kronos and Payroll  
**Expected Result**:  
- EC job information is updated with a new pay code (e.g., hourly → salaried)  
- Replication updates Payroll with new basic pay info  
- Time tracking logic in Kronos adjusts based on new pay type  

---

### Scenario 4: Leave Request in Kronos is Accounted for in Payroll Calculation  
**Expected Result**:  
- Leave request submitted in Kronos reflects correct leave type and duration  
- Leave is approved and passed to Payroll  
- Payroll reflects correct deduction or paid leave amount based on policy  

---

### Scenario 5: Job Change in EC Updates Time Recording Profile and Schedule  
**Expected Result**:  
- Employee receives job change (e.g., role or department) in EC  
- New job triggers update to Time Recording Profile or Work Schedule Rule  
- Updated scheduling logic reflects in Kronos assignment  
- Payroll reflects new schedule where applicable  

---

### Scenario 6: Employee Termination in EC Triggers Final Payroll Processing  
**Expected Result**:  
- Termination action in EC updates status and end date  
- Payroll run includes final settlement (leave payout, last salary, etc.)  
- Access in Kronos is restricted or disabled post-termination  

---

### Scenario 7: Bank Information Update in EC Reflects in Payroll (Infotype 0009)  
**Expected Result**:  
- Employee updates or submits new bank info in EC ESS  
- Infotype 0009 is updated via replication  
- Payroll payment file reflects new bank account  

---

### Scenario 8: One-Time Payment Added in EC Replicates to Payroll (Infotype 0015)  
**Expected Result**:  
- Bonus or one-time payment is added in EC  
- Infotype 0015 in Payroll is updated with correct wage type and amount  
- Payroll run includes the payment in that cycle  

---

### Scenario 9: Work Schedule Rule in EC Drives Shift Assignment in Kronos  
**Expected Result**:  
- EC assignment includes or updates Work Schedule Rule  
- Rule maps to predefined Kronos shift pattern (e.g., day, night, rotating)  
- Kronos schedule reflects correct shift plan for employee  

---

### Scenario 10: Timesheet Approval in Kronos Locks Entries and Sends to Payroll  
**Expected Result**:  
- Employee submits and supervisor approves timesheet in Kronos  
- Approved time is locked and marked as ready for Payroll  
- Time data successfully transfers and appears in Payroll pre-processing log  

** note - 
EC holds things like:
Time Recording Profile (e.g., "Positive time" or "Negative time")
Work Schedule Rule (e.g., “M-F 9–5” vs. “Rotating 4x4”)
Employee Class (Salaried vs. Hourly)
This defines what kind of time logic applies.
BUT...

Kronos = Actual Scheduling Engine
Kronos is where you define actual shift templates:
e.g., "Warehouse Shift A – 6 AM–2 PM"
e.g., "Night Maintenance – Rotating Weekends"
You assign these schedules in Kronos so it can:
Generate the daily/weekly roster
Enable punch-in/punch-out tracking
Apply overtime/shift premiums
Trigger alerts for schedule violations
** EC sending over “this person is hourly, should work rotating night shift”:
- Kronos needs an actual shift pattern to execute
- We created these as templates or pattern groups
- These were then mapped based on EC logic — assigned manually