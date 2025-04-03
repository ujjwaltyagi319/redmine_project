# Test Case: Redmine Installation & Laravel API Interaction

**Submitted By**: [Ujjwal Tyagi]  
**Submitted To**: [Vipin Sir]  
**Test Case Version**: 1.0  
**Reviewer Name**: [Pooja Ma'am]

## Goal
The goal of this project is to install Redmine using Podman, run it on port 8080, and connect it with a Laravel application through an API to perform various interactions.

## Table of Contents
- [Test Case: Redmine Installation & Laravel API Interaction](#test-case-redmine-installation--laravel-api-interaction)
  - [Goal](#goal)
  - [Test Environment](#test-environment)
  - [Test Cases](#test-cases)

---

## Test Environment
- **Redmine**: Running in a Podman container on port 8080.
- **Laravel Application**: Running separately and communicating with Redmine via API.
- **Database**: MySQL or PostgreSQL, used by both Redmine and Laravel.
- **Tools**: Postman, Browser, Laravel Artisan CLI.

---

## Test Cases

### TC1: Verify Podman Installation
**Scenario**: Ensure that Podman is installed correctly.  
**Given**: Podman is installed on the system.  
**When**: Run `podman --version` command.  
**Then**: Podman should return its installed version.  

---

### TC2: Verify Redmine Image Download
**Scenario**: Ensure the Redmine image is downloaded successfully.  
**Given**: Podman is installed.  
**When**: Run `podman pull redmine` command.  
**Then**: The Redmine image should be downloaded successfully.  

---

### TC3: Verify Redmine Container Runs on Port 8080
**Scenario**: Ensure Redmine is running on port 8080.  
**Given**: The Redmine container is started.  
**When**: Open `http://localhost:8080` in a browser.  
**Then**: The Redmine login page should be visible.  

---

### TC4: Verify Laravel Installation
**Scenario**: Ensure Laravel is installed and functional.  
**Given**: Laravel is installed.  
**When**: Run `php artisan --version`.  
**Then**: Laravel should return its installed version.  

---

### TC5: Verify Laravel API Can Connect to Redmine
**Scenario**: Ensure Laravel can communicate with Redmine via API.  
**Given**: Laravel is running.  
**When**: Call Redmine API from Laravel.  
**Then**: Redmine should return a valid response.  

---

### TC6: Verify Laravel Can Create an Issue in Redmine
**Scenario**: Ensure Laravel can create an issue in Redmine.  
**Given**: The Laravel API is connected to Redmine.  
**When**: Laravel sends a request to create an issue.  
**Then**: The issue should appear in Redmine.  

---

### TC7: Verify Laravel Can Fetch Issues from Redmine
**Scenario**: Ensure Laravel can fetch Redmine issues.  
**Given**: Redmine has issues.  
**When**: Laravel API requests issue data.  
**Then**: Laravel should retrieve Redmine issues.  

---

### TC8: Verify Laravel Can Update Issues in Redmine
**Scenario**: Ensure Laravel can update an issue in Redmine.  
**Given**: An issue exists in Redmine.  
**When**: Laravel sends an update request.  
**Then**: The issue should be updated in Redmine.  

---

### TC9: Verify Laravel Can Delete Issues in Redmine
**Scenario**: Ensure Laravel can delete an issue from Redmine.  
**Given**: An issue exists in Redmine.  
**When**: Laravel sends a delete request.  
**Then**: The issue should be removed from Redmine.  

---

### TC10: Verify API Authentication Between Laravel and Redmine
**Scenario**: Ensure Laravel uses correct API authentication.  
**Given**: Laravel is making API requests.  
**When**: The API token is invalid.  
**Then**: Redmine should return an authentication error.  

---

### TC11: Verify Error Handling in Laravel API
**Scenario**: Ensure Laravel API handles Redmine errors correctly.  
**Given**: Laravel API calls Redmine.  
**When**: Redmine returns an error.  
**Then**: Laravel should log the error and show an appropriate message.  

---

### TC12: Verify Data Consistency Between Redmine and Laravel
**Scenario**: Ensure data remains consistent between Laravel and Redmine.  
**Given**: Data is modified via Laravel.  
**When**: Fetch the same data from Redmine.  
**Then**: The data should match.  

---

### TC13: Verify Laravel Can Handle Network Failures
**Scenario**: Ensure Laravel API handles network issues.  
**Given**: Redmine is temporarily down.  
**When**: Laravel tries to access Redmine.  
**Then**: Laravel should handle the failure gracefully.  

---

### TC14: Verify Redmine and Laravel After a Restart
**Scenario**: Ensure Laravel and Redmine maintain consistency after a restart.  
**Given**: The system is restarted.  
**When**: Fetch data from both systems.  
**Then**: The data should remain unchanged.  

---

### TC15: Verify Log Files Capture Laravel-Redmine Errors
**Scenario**: Ensure log files capture API-related errors.  
**Given**: Laravel is making API calls to Redmine.  
**When**: An error occurs.  
**Then**: The Laravel logs should capture the details.  

---

**End of Test Cases**


