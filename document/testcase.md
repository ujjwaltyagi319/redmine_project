# Test Case: Redmine Tool Installation & PHP Script Interaction

**Submitted By**: [Ujjwal Tyagi]  
**Submitted To**: [Vipin Sir] 

**Test Case Version**: <Version>  
**Reviewer Name**: [Pooja Ma'am]

## Goal
The goal of this project is to install the Redmine tool using Podman, run it on port 8080, create a PHP script running on port 3000, and ensure that changes made in the PHP script are reflected in Redmine.

## Table of Contents
- [Test Case: Redmine Tool Installation \& PHP Script Interaction](#test-case-redmine-tool-installation--php-script-interaction)
  - [Goal](#goal)
  - [Table of Contents](#table-of-contents)
    - [Test Environment](#test-environment)
    - [TC1: Verify Redmine Installation with Podman](#tc1-verify-redmine-installation-with-podman)
    - [TC2: Verify Redmine Running on Port 8080](#tc2-verify-redmine-running-on-port-8080)
    - [TC3: Verify PHP Script Setup on Port 3000](#tc3-verify-php-script-setup-on-port-3000)
    - [TC4: Verify Redmine and PHP Script Accessibility](#tc4-verify-redmine-and-php-script-accessibility)
    - [TC5: Verify Database Connectivity Between Redmine and PHP Script](#tc5-verify-database-connectivity-between-redmine-and-php-script)
    - [TC6: Verify PHP Script Can Update Redmine Data](#tc6-verify-php-script-can-update-redmine-data)
    - [TC7: Verify Redmine Reflects PHP Script Changes](#tc7-verify-redmine-reflects-php-script-changes)
    - [TC8: Verify Data Consistency Between Redmine and PHP Script](#tc8-verify-data-consistency-between-redmine-and-php-script)
    - [TC9: Verify Error Handling in PHP Script for Redmine Changes](#tc9-verify-error-handling-in-php-script-for-redmine-changes)
    - [TC10: Verify Redmine and PHP Script Maintain Data Consistency After Restart](#tc10-verify-redmine-and-php-script-maintain-data-consistency-after-restart)
    - [TC11: Verify PHP Script Works After Redmine Restart](#tc11-verify-php-script-works-after-redmine-restart)
    - [TC12: Verify Log Files for Errors or Issues](#tc12-verify-log-files-for-errors-or-issues)

---

### Test Environment
Description of testing interfaces or URLs available to the tester.

---

### TC1: Verify Redmine Installation with Podman

**Scenario**: Verify that Redmine is installed correctly using Podman.  
**Remarks**: Ensure that Redmine is running successfully as a container in Podman.  
**Given**: Run the `podman run` command to install Redmine.  
**When**: Verify the container status using `podman ps`.  
**Then**: The Redmine container should be running successfully.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC2: Verify Redmine Running on Port 8080

**Scenario**: Ensure Redmine is accessible via port 8080.  
**Remarks**: Verify that Redmine can be accessed through the specified port.  
**Given**: Redmine is running in Podman.  
**When**: Open a browser and go to `http://localhost:8080`.  
**Then**: The Redmine login page should appear.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC3: Verify PHP Script Setup on Port 3000

**Scenario**: Verify the PHP script is set up to run on port 3000.  
**Remarks**: Ensure the PHP script is working on a different port.  
**Given**: The PHP script is running on port 3000.  
**When**: Access the PHP script using `http://localhost:3000`.  
**Then**: The PHP script's interface should load.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC4: Verify Redmine and PHP Script Accessibility

**Scenario**: Verify that both Redmine and the PHP script can be accessed.  
**Remarks**: Ensure both tools are working independently without errors.  
**Given**: Redmine is running on port 8080 and PHP script is on port 3000.  
**When**: Open the respective URLs in a browser (`http://localhost:8080` for Redmine and `http://localhost:3000` for the PHP script).  
**Then**: Both Redmine and the PHP script should load correctly.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC5: Verify Database Connectivity Between Redmine and PHP Script

**Scenario**: Ensure that the PHP script can communicate with the Redmine database.  
**Remarks**: Verify that the PHP script can access and modify Redmine’s database.  
**Given**: Database connectivity is set up between PHP script and Redmine.  
**When**: Execute a query from the PHP script to fetch Redmine data.  
**Then**: The PHP script should successfully fetch and return data from Redmine.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC6: Verify PHP Script Can Update Redmine Data

**Scenario**: Verify that the PHP script can update Redmine data.  
**Remarks**: Ensure the PHP script modifies the Redmine database as expected.  
**Given**: The PHP script is connected to the Redmine database.  
**When**: Use the PHP script to make changes to Redmine (e.g., create or update an issue).  
**Then**: The changes should be successfully reflected in the Redmine database.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC7: Verify Redmine Reflects PHP Script Changes

**Scenario**: Verify that Redmine reflects changes made by the PHP script.  
**Remarks**: Ensure Redmine updates after changes are made via the PHP script.  
**Given**: The PHP script has modified data in Redmine.  
**When**: Access Redmine through `http://localhost:8080`.  
**Then**: The changes made by the PHP script should be visible in Redmine (e.g., updated issue or project).

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC8: Verify Data Consistency Between Redmine and PHP Script

**Scenario**: Ensure that data remains consistent between Redmine and the PHP script.  
**Remarks**: Verify data changes are reflected both in Redmine and the PHP script.  
**Given**: Redmine data is modified by the PHP script.  
**When**: Check the database to confirm data consistency.  
**Then**: Data should be the same in both Redmine and the PHP script.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC9: Verify Error Handling in PHP Script for Redmine Changes

**Scenario**: Verify the error handling when there are issues updating Redmine via the PHP script.  
**Remarks**: Ensure that errors are caught and properly handled when trying to update Redmine.  
**Given**: The PHP script is trying to update Redmine.  
**When**: Introduce an error (e.g., database connection failure or invalid data).  
**Then**: The PHP script should display a relevant error message or log the issue.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC10: Verify Redmine and PHP Script Maintain Data Consistency After Restart

**Scenario**: Ensure Redmine and the PHP script maintain data consistency after a system restart.  
**Remarks**: Verify that data is not lost after a restart.  
**Given**: Redmine and the PHP script are both running.  
**When**: Restart the system or containers.  
**Then**: Redmine and the PHP script should retain data consistency after the restart.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC11: Verify PHP Script Works After Redmine Restart

**Scenario**: Verify that the PHP script continues to work after restarting Redmine.  
**Remarks**: Ensure the PHP script can still interact with Redmine after Redmine has been restarted.  
**Given**: Redmine is running and the PHP script is set up.  
**When**: Restart the Redmine container.  
**Then**: The PHP script should still be able to make changes to Redmine and fetch data.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---

### TC12: Verify Log Files for Errors or Issues

**Scenario**: Verify that log files are correctly generated for errors or issues.  
**Remarks**: Ensure logs are generated for PHP script or Redmine errors.  
**Given**: Redmine and PHP script are running.  
**When**: Check the logs for both systems (Redmine and PHP script).  
**Then**: Logs should capture any errors or issues that occur during execution.

**Test Run Date**:  
**Result**:  
Pending/Pass/Fail  
**Testing Outputs**: (paste your output/snapshots here)

---
