# Drupal 11 Development Environment

A containerized local development environment for **Drupal 11**, built using Docker, Lando, Composer, Drush, MySQL, and Git.

This project demonstrates a structured Drupal development workflow, including environment setup, dependency management, contributed module installation, configuration management, and version control best practices.

## Tech Stack

| Technology | Purpose |
|---|---|
| Drupal 11 | Content Management System |
| PHP | Backend programming language |
| Docker | Containerization |
| Lando | Local development environment orchestration |
| Composer | PHP dependency management |
| Drush | Drupal command-line administration |
| MySQL | Relational database |
| Git | Version control |

## Implemented Features

### 1. Admin Toolbar

Installed and enabled the Admin Toolbar contributed module.

- Improves Drupal administration navigation.
- Provides quick access to administrative pages.
- Makes backend content management more efficient.

### 2. Pathauto

Installed and enabled the Pathauto contributed module.

- Automatically generates URL aliases for Drupal content.
- Reduces manual URL management.
- Supports configurable URL alias patterns.

**Dependencies installed automatically:**
- Token
- Chaos Tools (CTools)

## Project Structure

```text
recommended-project/
│
├── config/
│   └── sync/              # Exported Drupal configuration
│
├── web/                   # Drupal application root
│   ├── core/
│   ├── modules/
│   ├── themes/
│   └── sites/
│
├── vendor/                # Composer dependencies
│
├── composer.json          # Project dependencies
├── composer.lock          # Locked dependency versions
├── .lando.yml             # Lando environment configuration
└── README.md              # Project documentation
```

## Prerequisites

Ensure the following tools are installed before setting up the project:

- Docker Desktop
- WSL2
- Ubuntu (WSL2)
- Git
- Composer
- Lando

## Getting Started

Follow these steps to set up the project locally.

### 1. Clone the Repository

```bash
git clone <repository-url>
cd recommended-project
```

### 2. Start the Development Environment

```bash
lando start
```

Lando initializes the required Docker containers and starts the local development services.

### 3. Verify the Environment

```bash
lando info
```

Displays information about the running services, application URLs, and database connection details.

### 4. Verify Drupal Installation

```bash
lando drush status
```

Expected results:

```text
Database         : Connected
Drupal bootstrap : Successful
```

### 5. Open the Drupal Website

```bash
lando open
```

Opens the local Drupal application in your default browser.

## Installed Modules

The following contributed modules have been installed and enabled.

| Module | Purpose | Status |
|---|---|---|
| Admin Toolbar | Improved admin navigation | Enabled |
| Pathauto | Automatic URL alias generation | Enabled |
| Token | Reusable dynamic tokens | Enabled |
| CTools | Additional Drupal API functionality | Enabled |

## Configuration Management

Drupal configuration management allows developers to move configuration changes between environments using YAML files and version control.

**Configuration directory:**

```text
config/sync/
```

### Export Configuration (CEX)

Exports active configuration from the Drupal database into YAML files.

```bash
lando drush cex -y
```

**Data flow:**

```text
Drupal Database
       |
       v
  Drush CEX
       |
       v
 config/sync/
       |
       v
   Git Commit
       |
       v
    Git Push
```

### Import Configuration (CIM)

Imports configuration from YAML files into the active Drupal configuration.

```bash
lando drush cim -y
```

**Data flow:**

```text
    Git Pull
       |
       v
 config/sync/
       |
       v
  Drush CIM
       |
       v
 Drupal Database
```

**Important:** Configuration synchronization and database updates are different operations. CEX/CIM handles configuration, whereas `drush updb` handles pending database updates.

## Useful Drush Commands

| Command | Description |
|---|---|
| `lando drush status` | Check Drupal environment status |
| `lando drush cr` | Clear Drupal cache |
| `lando drush uli` | Generate a one-time login URL |
| `lando drush cex -y` | Export configuration |
| `lando drush cim -y` | Import configuration |
| `lando drush cget system.site` | View site configuration |
| `lando drush updb -y` | Apply pending database updates |
| `lando drush watchdog:show` | View Drupal log messages |

## Git Workflow

The project follows a feature-branch-based development workflow.

### 1. Create a Feature Branch

```bash
git checkout -b feature/<feature-name>
```

### 2. Check Working Tree Status

```bash
git status
```

### 3. Stage Changes

```bash
git add .
```

### 4. Commit Changes

```bash
git commit -m "feat: implement feature"
```

### 5. Push Changes

```bash
git push origin feature/<feature-name>
```

### 6. View Commit History

```bash
git log --oneline
```

## Commit History

The following milestones represent the implementation completed so far:

```text
chore: initialize Drupal 11 development environment
feat: install and enable Admin Toolbar module
feat: install and enable Pathauto module
```

## Learning Outcomes

This project provides practical experience with:

- Drupal 11 installation and environment setup.
- Docker containers and Lando orchestration.
- Composer dependency management.
- Drupal contributed module installation and dependencies.
- Drush command-line administration.
- Configuration management using CEX and CIM.
- Git branching and version control workflows.
- Linux filesystem and permission fundamentals.
- Local Drupal development workflows.

## Development Workflow

The overall development process follows this sequence:

```text
Developer
    |
    v
WSL2 / Ubuntu
    |
    v
Lando
    |
    v
Docker Containers
    |
    +------------------+
    |                  |
    v                  v
Drupal / PHP         MySQL
    |
    v
Drush Commands
    |
    v
Configuration / Modules
    |
    v
Git Version Control
    |
    v
GitHub Repository
```

## Start Development

Once the repository has been cloned and configured, use:

```bash
# Start local environment
lando start

# Verify Drupal
lando drush status

# Open application
lando open
```

## Project Status

**Current Status:** Initial Development Environment Setup Completed

Implemented:
- Drupal 11 environment setup.
- Lando and Docker integration.
- Admin Toolbar installation and enablement.
- Pathauto installation and enablement.
- Automatic dependency installation.
- Drupal configuration management workflow.
- Git version control setup.

---

**Built for learning and practicing professional Drupal 11 development workflows.**
