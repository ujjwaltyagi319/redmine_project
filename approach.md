# Approach Paper

## Laravel Installation using Podman

---

### Table of Contents (TOC)
1. [Objective](#objective)
2. [Proposed Solutions](#proposed-solutions)
   - [Approach 1: Laravel Installation using Podman](#approach-1-laravel-installation-using-podman)
   - [Approach 2: Laravel Installation using Docker (Alternative)](#approach-2-laravel-installation-using-docker-alternative)
3. [Comparison & Chosen Approach](#comparison--chosen-approach)

---

## 1. Objective
The objective of this project is to install Laravel using Podman, a container management tool, configure the system, and ensure functionality through customization and testing. The Laravel application will be installed on port 8080 and accessed through a web browser.

## 2. Proposed Solutions
We propose two approaches for installing Laravel:
- **Approach 1**: Podman for Laravel installation (Primary Approach)
- **Approach 2**: Docker for Laravel installation (Alternative Approach)

Both approaches will be explored, with the advantages and disadvantages of each evaluated to determine the best solution for the project.

---

## 3. Approach 1: Laravel Installation using Podman

### 3.1 Architecture Diagram

### 3.2 Description
In **Approach 1**, we will install Laravel in a containerized environment using Podman. Podman offers similar functionality to Docker but does not require a daemon, making it a more secure and flexible solution. The Laravel source code will be pulled from GitHub, and any required modifications will be made using VS Code.

**Advantages** of this approach:
- **Security**: Podman does not require root privileges and does not need a daemon, making it more secure.
- **Flexibility**: Podman can easily integrate with CI/CD pipelines.
- **Lightweight**: Podman’s architecture is less resource-intensive.

**Disadvantages** of this approach:
- **Learning Curve**: Fewer resources and examples are available compared to Docker.
- **Limited GUI**: Podman does not provide a graphical interface like Docker Desktop.

### 3.3 Pre-requisites

#### 3.3.1 Hardware Requirements
- **RAM**: Minimum 2 GB RAM for basic operations.
- **Disk Space**: Minimum 10 GB of disk space for the Laravel application, database, and containers.

#### 3.3.2 Software Requirements
- **Podman** (Version 3.x or higher) for managing containers.
- **Laravel** (Latest stable version).
- **Git** for pulling Laravel’s code from GitHub.
- **VS Code** for editing and testing the code.
- **Linux OS** (Ubuntu 20.04 recommended).

#### 3.3.3 Networking Requirements
- **Port 8080**: Must be open to allow Laravel access through a browser.
- **Internet**: Needed to fetch container images and dependencies.

---

## 4. Approach 2: Laravel Installation using Docker (Alternative)

### 4.1 Architecture Diagram

### 4.2 Description
**Approach 2** utilizes Docker, which is the most widely used container management tool. Docker allows us to run Laravel in isolated containers, managing both the application and its dependencies (such as the database). The setup is simplified with Docker Compose, allowing us to easily configure and manage multiple containers.

**Advantages** of this approach:
- **Widespread Adoption**: Docker is well-documented and widely used in industry.
- **Easy Setup**: Docker provides a straightforward installation and setup process.
- **Extensive Support**: Docker has a robust community and extensive resources for troubleshooting.

**Disadvantages** of this approach:
- **Daemon Requirement**: Docker requires a daemon running in the background, which may be less secure than Podman.
- **Overhead**: Docker may incur more overhead due to the need for a background process.

### 4.3 Pre-requisites

#### 4.3.1 Hardware Requirements
- **RAM**: Minimum 2 GB RAM for smooth operations.
- **Disk Space**: Minimum 10 GB of disk space.

#### 4.3.2 Software Requirements
- **Docker** (Version 20.x or higher) for container management.
- **Docker Compose** for orchestrating multiple containers.
- **Git** for pulling Laravel’s code.
- **VS Code** for editing and testing the code.
- **Linux OS** (Ubuntu 20.04 recommended).

#### 4.3.3 Networking Requirements
- **Port 8080**: Must be open to access Laravel through a browser.
- **Internet**: Needed to pull Docker images and dependencies.

---

## 5. Comparison & Chosen Approach

### Comparison of Approaches:

| Feature                | Podman                             | Docker                             |
|------------------------|------------------------------------|------------------------------------|
| **Security**           | Daemonless, no root privileges needed | Requires daemon with root privileges |
| **Learning Curve**     | Slightly more complex to learn     | Easier for beginners, widely adopted |
| **Flexibility**        | More flexible in CI/CD environments | Simplified but less flexible than Podman |
| **Resource Overhead**  | Lightweight, lower overhead        | Slightly higher due to daemon      |
| **Community Support**  | Smaller, growing community         | Larger, well-established community |

---

### Chosen Approach: **Approach 1 - Podman**

After evaluating both approaches, we have chosen **Approach 1 (using Podman)** because of its **security features** (daemonless, no root privileges) and **lightweight nature**, which aligns better with the project’s needs for minimal overhead and flexibility. Podman’s increasing adoption and suitability for containerized environments make it the preferred choice for this project.

This approach paper provides a comprehensive solution for the Laravel installation using Podman. It includes detailed architectural diagrams, descriptions, pros and cons of each approach, and the prerequisites for both approaches.

