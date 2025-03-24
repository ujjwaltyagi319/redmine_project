# IMPLEMENTATION JOURNAL - Redmine Installation with Podman and PHP Scripts Integration

**Submitted By:** Ujjwal Tyagi  
**Submitted To:** Vipin Tripathi  
**Test Case Version:** 1.1  
**Reviewer Name:** Vipin Tripathi  

## Goal
The goal of this project is to install and run Redmine using Podman, ensuring it is accessible on port 8080. Additionally, PHP scripts running on port 3000 will enable modifications to Redmine's data. Any changes made via the PHP scripts should be reflected immediately in the Redmine installation.

---

## Table of Contents
1. [PREREQUISITES](#prerequisites)
    1.1 [Hardware Requirements](#hardware-requirements)  
    1.2 [Software Requirements](#software-requirements)  
    1.3 [Network Requirements](#network-requirements)
2. [STEPS](#steps)
    2.1 [Install Redmine with Podman](#install-redmine-with-podman)  
    2.2 [Verify Redmine Installation](#verify-redmine-installation)  
    2.3 [Set Up PHP Scripts Environment](#set-up-php-scripts-environment)  
    2.4 [Establish PHP and Redmine Communication](#establish-php-and-redmine-communication)  
    2.5 [Test Changes Reflecting in Redmine](#test-changes-reflecting-in-redmine)

---

## 1. PREREQUISITES

### 1.1 Hardware Requirements
- **CPU:** Minimum 2 Cores  
- **RAM:** Minimum 4 GB  
- **Storage:** Minimum 10 GB Free Space  

### 1.2 Software Requirements
- **OS:** Ubuntu 20.04 or later  
- **Podman:** Version 4.4 or later  
- **PHP:** Version 8.1 or later  
- **Redmine:** Latest stable version  
- **MySQL:** Version 8.0  
- **VS Code:** For editing scripts  

### 1.3 Network Requirements
- **Open Ports:**
    - Port 8080 for Redmine  
    - Port 3000 for PHP Scripts  
- **Internal Network Communication:** Between PHP scripts and Redmine  
- **External Internet Access:** For downloading dependencies  

---

## 2. STEPS

### 2.1 Install Redmine with Podman
**Command Executed:**
```bash
podman run -d --name redmine -p 8080:3000 redmine:latest

## create project
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Create Redmine Project</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }
        h2 {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
        }
        input, textarea {
            width: 100%;
            padding: 8px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background: #28a745;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }
        button:hover {
            background: #218838;
        }
    </style>
</head>
<body>
    <div class="container">
        <?php
        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            error_reporting(E_ALL); 
            ini_set('display_errors', '1');
            require_once 'vendor/autoload.php';
            
            $client = new \Redmine\Client\NativeCurlClient('http://localhost:8080/', 'aeb3cb5fdf236df131fd65afc5e65560be91415a');
            
            $client->getApi('project')->create([
                'name' => $_POST['name'],
                'identifier' => $_POST['identifier'],
                'description' => $_POST['description'],
            ]);
            
            echo "<p style='color: green;'>Project created successfully!</p>";
        }
        ?>
        <h2>Create Redmine Project</h2>
        <form method="post" action="">
            <label for="name">Project Name:</label>
            <input type="text" id="name" name="name" required>
            <label for="identifier">Identifier:</label>
            <input type="text" id="identifier" name="identifier" required>
            <label for="description">Description:</label>
            <textarea id="description" name="description" required></textarea>
            <button type="submit">Create Project</button>
        </form>
    </div>
</body>
</html>
