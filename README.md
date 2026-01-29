# jenkins-pipeline
Automated Cloud Infrastructure Provisioning and Deployment Platform
# Jenkins CI/CD Pipeline

This repository contains the Jenkins pipeline (Jenkinsfile) used to orchestrate
infrastructure provisioning and configuration workflows.

## Pipeline Responsibilities
- Trigger on SCM changes
- Execute Terraform provisioning (LocalStack)
- Run Ansible configuration tasks
- Archive build artifacts and logs

## Repository Contents
- `Jenkinsfile` – Pipeline as code definition
- `screenshots/` – Evidence of successful pipeline execution

## Evidence
Screenshots below demonstrate successful pipeline execution.

## Notes
This pipeline is designed to run locally using Docker and LocalStack to avoid
cloud costs while maintaining AWS-compatible infrastructure patterns.
