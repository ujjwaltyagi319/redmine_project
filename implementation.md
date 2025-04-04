# IMPLEMENTATION JOURNAL - Redmine Installation with Podman and Laravel Integration

**Submitted By:** Ujjwal Tyagi  
**Submitted To:** Vipin Tripathi  
**Test Case Version:** 1.1  
**Reviewer Name:** Vipin Tripathi  

## Goal
The goal of this project is to install and run Redmine using Podman, ensuring it is accessible on port 8080. Additionally, a Laravel-based application running on port 8001 will enable modifications to Redmine's data. Any changes made via the Laravel application should be reflected immediately in the Redmine installation.

## Table of Contents
1. PREREQUISITES  
   1.1 Hardware Requirements  
   1.2 Software Requirements  
   1.3 Network Requirements  
2. STEPS  
   2.1 Install Redmine with Podman  
   2.2 Verify Redmine Installation  
   2.3 Set Up Laravel Environment  
   2.4 Establish Laravel and Redmine Communication  
   2.5 Test Changes Reflecting in Redmine  

## 1. PREREQUISITES
### 1.1 Hardware Requirements
- CPU: Minimum 2 Cores  
- RAM: Minimum 4 GB  
- Storage: Minimum 10 GB Free Space  

### 1.2 Software Requirements
- OS: Ubuntu 20.04 or later  
- Podman: Version 4.4 or later  
- PHP: Version 8.1 or later  
- Laravel: Latest stable version  
- Redmine: Latest stable version  
- MySQL: Version 8.0  
- VS Code: For editing scripts  

### 1.3 Network Requirements
- **Open Ports:**  
  - Port 8080 for Redmine  
  - Port 3000 for Laravel Application  
- **Internal Network Communication:** Between Laravel and Redmine  
- **External Internet Access:** For downloading dependencies  

## 2. STEPS
### 2.1 Install Redmine with Podman
Command Executed:
```sh
podman run -d --name redmine -p 8080:3000 redmine:latest
```

### 2.2 Verify Redmine Installation
- Open `http://localhost:8080/` in a browser to verify Redmine is running.

### 2.3 Set Up Laravel Environment
1. **Install Laravel:**
   ```sh
   composer create-project laravel/laravel redmine-app
   cd redmine-app
   ```
2. **Install Redmine API Package:**
   ```sh
   composer require kbsali/redmine-api
   ```

### 2.4 Establish Laravel and Redmine Communication
#### **Routes (routes/web.php):**
```php
use App\Http\Controllers\RedmineController;

Route::get('/projects/create', [RedmineController::class, 'create'])->name('projects.create');
Route::post('/projects/store', [RedmineController::class, 'store'])->name('projects.store');
```

#### **Controller (app/Http/Controllers/RedmineController.php):**
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Redmine\Client\NativeCurlClient;

class RedmineController extends Controller
{
    private $client;

    public function __construct()
    {
        $this->client = new NativeCurlClient('http://localhost:8080/', 'aeb3cb5fdf236df131fd65afc5e65560be91415a');
    }

    public function create()
    {
        return view('projects.create');
    }

    public function store(Request $request)
    {
        $request->validate([
            'name' => 'required|string',
            'identifier' => 'required|string|unique:projects',
            'description' => 'required|string',
        ]);

        $this->client->getApi('project')->create([
            'name' => $request->input('name'),
            'identifier' => $request->input('identifier'),
            'description' => $request->input('description'),
        ]);

        return redirect()->route('projects.create')->with('success', 'Project created successfully!');
    }
}
```

#### **Blade Template (resources/views/projects/create.blade.php):**
```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Create Redmine Project</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
</head>
<body class="bg-light d-flex justify-content-center align-items-center vh-100">
    <div class="container">
        <div class="card p-4 shadow-sm">
            <h2 class="mb-4 text-center">Create Redmine Project</h2>

            @if(session('success'))
                <div class="alert alert-success">{{ session('success') }}</div>
            @endif

            <form method="POST" action="{{ route('projects.store') }}">
                @csrf
                <div class="mb-3">
                    <label for="name" class="form-label">Project Name:</label>
                    <input type="text" id="name" name="name" class="form-control" required>
                </div>
                <div class="mb-3">
                    <label for="identifier" class="form-label">Identifier:</label>
                    <input type="text" id="identifier" name="identifier" class="form-control" required>
                </div>
                <div class="mb-3">
                    <label for="description" class="form-label">Description:</label>
                    <textarea id="description" name="description" class="form-control" required></textarea>
                </div>
                <button type="submit" class="btn btn-success w-100">Create Project</button>
            </form>
        </div>
    </div>
</body>
</html>
```



### 2.5 Test Changes Reflecting in Redmine
1. **Run Laravel Server:**
   ```sh
   php artisan serve
   ```
2. **Open in Browser:**
   - Navigate to `http://127.0.0.1:8000/projects/create`.
   - Fill in the form and submit.
   - The new project should be created in Redmine and appear under `http://localhost:8080/projects`.

---
This Laravel-based approach provides a structured and scalable way to integrate Redmine with Laravel, ensuring that project modifications via Laravel are instantly reflected in Redmine. 🚀

