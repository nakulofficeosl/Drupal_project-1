Drupal 11 Assignment

-Overview
This project is a Drupal 11 application running on Lando with a MySQL database and managed through Composer and Drush.

-Prerequisites
Docker Desktop
WSL2
Ubuntu
Git
PHP
Composer
Lando
Clone Repository
git clone <repository-url>
cd recommended-project
Start Project
lando start

Verify:
lando info

Open site:
lando open
Install Dependencies
composer install
or

lando composer install
Database
Database is managed through Lando.

Check connection:

lando drush status
Expected:

Database: Connected
Drupal bootstrap: Successful
Installed Modules
Admin Toolbar
Pathauto
Token
Chaos Tools (CTools)
Useful Drush Commands
Clear Cache
lando drush cr
One Time Login URL
lando drush uli
Export Configuration
lando drush cex -y
Import Configuration
lando drush cim -y
View Site Configuration
lando drush cget system.site
View Logs
lando drush watchdog:show
Run Database Updates
lando drush updb -y
Configuration Management
Configuration is stored in:

config/sync
Export configuration:

lando drush cex -y
Import configuration:

lando drush cim -y
Workflow:

Drupal Admin Changes
        ↓
Database
        ↓
drush cex
        ↓
config/sync
        ↓
Git Commit
        ↓
Git Push
Another developer:

Git Pull
     ↓
drush cim
     ↓
Database Updated
Git Workflow
View status:

git status
Create branch:

git checkout -b feature/<feature-name>
Commit changes:

git add .
git commit -m "feat: implement feature"
View history:


git log --oneline
Project Structure
recommended-project/
├── config/
│   └── sync/
├── web/
├── vendor/
├── composer.json
├── composer.lock
└── .lando.yml
Current Git History
chore: initialize Drupal 11 development environment
feat: install and enable Admin Toolbar module
feat: install and enable Pathauto module
Start Development
lando start
lando drush status
lando open
