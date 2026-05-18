# Kubernetes-EKS-
# AWS EKS Cluster Setup using eksctl

## Overview
This project explains how to setup a Kubernetes cluster in AWS using Amazon EKS and eksctl.

EKS (Elastic Kubernetes Service) is a managed Kubernetes service provided by AWS.

Using this setup we can:
- Create Kubernetes Cluster
- Manage Worker Nodes
- Deploy Applications
- Practice Kubernetes Commands

---

# Prerequisites

- AWS Account
- EC2 Instance (Ubuntu)
- IAM Permissions
- Internet Connection

---

# Architecture

Developer
   ↓
EC2 Management Host
   ↓
kubectl / eksctl
   ↓
AWS EKS Cluster
   ↓
Worker Nodes
   ↓
Pods & Containers

---

# Step - 1 : Create EC2 Management Host

## Launch Ubuntu EC2 Instance

Recommended:
- OS : Ubuntu
- Instance Type : t2.micro

Connect to machine using SSH.

---

# Step - 2 : Install kubectl

kubectl is Kubernetes command line tool used to communicate with cluster.

Run below commands:

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin

kubectl version --short --client
