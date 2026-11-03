# Drupal 11 — AI Learning Prompts

**Assignment 1 | Conceptual Understanding, Practical Implementation & Verification**

This document contains three structured AI prompts designed to help understand important Drupal 11 development concepts through real-world examples, practical verification, and independent explanation.

**Learning Approach:**

Understand → Implement → Verify → Explain

---

## 01. Configuration Management — CEX vs CIM

**Objective:** Understand how Drupal configuration moves between the database, YAML files, and development environments.

### AI Learning Prompt

> I am developing a Drupal 11 application using Lando, Drush, and MySQL.
>
> Explain the difference between `drush cex` (Configuration Export) and `drush cim` (Configuration Import) from a real development perspective.
>
> Cover the following:
>
> 1. Where does Drupal store its active configuration?
> 2. What is the purpose of the `config/sync` directory?
> 3. What happens step by step when I run `lando drush cex -y`?
> 4. What happens step by step when I run `lando drush cim -y`?
> 5. Why do developers commit exported YAML configuration files to Git instead of sharing the entire database?
> 6. How does another developer receive configuration changes from the first developer?
> 7. What can go wrong if CEX or CIM is executed at the wrong time?
>
> Use a simple data-flow diagram and explain why each operation is necessary.
>
> Finally, ask me three practical questions to evaluate whether I genuinely understand CEX and CIM.

### Verification

- Review Drupal.org Configuration Management documentation.
- Execute CEX and CIM in the local project.
- Inspect the changes generated inside `config/sync`.
- Understand the difference between active and exported configuration.

---

## 02. Composer & Module Dependencies — Pathauto

**Objective:** Understand the difference between downloading a contributed module and enabling it in Drupal.

### AI Learning Prompt

> I am working on a Drupal 11 project where I installed the Pathauto module using Composer.
>
> Explain how Composer installation differs from enabling a module using Drush.
>
> Use Pathauto and its actual declared dependencies as practical examples.
>
> Cover the following:
>
> 1. What is a Drupal contributed module?
> 2. What is the difference between installing a module using Composer and enabling it using Drush?
> 3. Why does Pathauto require Token, if declared by the installed version?
> 4. How does Drupal define module dependencies?
> 5. What happens when I execute `composer require drupal/pathauto`?
> 6. What is the difference between `composer.json`, `composer.lock`, and the modules directory?
> 7. How can I check which dependencies a module requires?
> 8. What happens if I try to enable a module without its required dependencies?
> 9. Why should I avoid manually downloading and copying contributed modules into the modules directory?
>
> Explain the complete development flow:
>
> **Composer → Download Dependencies → Drupal Module Discovery → Drush Enable → Drupal Database**
>
> Verify the actual dependency declarations instead of assuming that every Pathauto version requires CTools.
>
> Finally, give me a practical scenario and ask me to explain the complete installation and enablement process in my own words.

### Verification

- Review the Pathauto project page on Drupal.org.
- Inspect the installed module's `.info.yml` dependency declarations.
- Review `composer.json` and `composer.lock`.
- Verify module installation and enablement using Composer and Drush.

---

## 03. Configuration Sync Directory — settings.php

**Objective:** Understand how Drupal identifies the configuration synchronization directory and manages configuration between YAML files and the database.

### AI Learning Prompt

> I am developing a Drupal 11 application using Lando and MySQL.
>
> My project contains a `config/sync` directory. I want to understand how Drupal identifies this directory and uses it for configuration synchronization.
>
> Cover the following:
>
> 1. What is `settings.php` and why is it important?
> 2. What is the purpose of the configuration sync directory?
> 3. What is the role of `$settings['config_sync_directory']`?
> 4. How does Drupal identify the directory used for configuration export and import?
> 5. What happens if the sync directory is not configured correctly?
> 6. What is the difference between active configuration in the database and exported YAML files?
> 7. Why should `config/sync` be committed to Git?
> 8. How does another developer use these configuration files after cloning the repository?
> 9. What is the difference between configuration synchronization and database updates using `drush updb`?
>
> Explain the complete workflow using a practical example:
>
> **Admin Configuration Changes → Active Configuration → Drush CEX → config/sync → Git Commit → Git Pull → Drush CIM → Updated Active Configuration**
>
> Also explain how I can safely verify the configuration directory in my existing Lando project.
>
> Do not generate setup scripts or modify my project. Explain the commands, their purpose, and the expected behavior.
>
> Finally, ask me to explain the complete workflow without looking at my notes and evaluate my understanding.

### Verification

- Inspect the existing `settings.php`.
- Verify the configured `$settings['config_sync_directory']` path.
- Compare the configured path with the actual `config/sync` directory.
- Export configuration and inspect the generated YAML files.

---

## Learning & Evaluation Strategy

For each topic, follow these four steps:

| Step | Activity | Expected Outcome |
|---|---|---|
| 1. Understand | Learn the concept and its purpose | Understand WHY it is used |
| 2. Implement | Execute commands in the local project | Understand HOW it works |
| 3. Verify | Check Drupal.org documentation and project behavior | Confirm actual implementation |
| 4. Explain | Describe the complete flow without notes | Demonstrate genuine understanding |

### Self-Evaluation Checklist

- [ ] I can explain the concept without memorizing definitions.
- [ ] I understand why the technology or command is needed.
- [ ] I can explain its role in an actual Drupal project.
- [ ] I have verified its behavior in my local environment.
- [ ] I can explain the complete workflow to another developer.

---

**Learning Principle:** The goal is not just to remember Drupal commands. The goal is to understand what happens behind each command, why developers use it, and how it fits into a real-world Drupal development workflow.
