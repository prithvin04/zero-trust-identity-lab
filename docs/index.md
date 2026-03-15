# Zero Trust & Identity Lab

## Introduction

Traditional network security relies on perimeter-based protection where devices inside the network are trusted.

Zero Trust Architecture removes this assumption and verifies every user and device before granting access.

This lab demonstrates how identity-based networking and least privilege access control can be implemented using open tools.

---

## Lab Objectives

In this lab you will:

1. Configure identity-based connectivity using Tailscale
2. Deploy a protected service
3. Implement micro-segmentation
4. Configure least privilege access
5. Use Generative AI to analyze security logs

## Step 1 — Identity-Based Connectivity

Traditional networks rely on IP-based trust. Devices inside the network are implicitly trusted.

Zero Trust Architecture removes this assumption and verifies the **identity of users and devices** before allowing access.

In this step we configure identity-based connectivity using **Tailscale**.

### Install Tailscale

Run the following command:

curl -fsSL https://tailscale.com/install.sh | sh

### Start Tailscale

sudo tailscale up

A browser window will open asking you to authenticate.

Choose **GitHub SSO** to log in.

### Verify the Connection

Run:

tailscale status

Expected output example:

100.x.x.x   ubuntu-server   username@   linux

This indicates that the device has successfully joined the **Tailscale secure mesh network** using identity-based authentication.

## Step 2 — Deploy a Protected Service

To demonstrate Zero Trust access control, we first deploy a simple internal service.

Run the following command:

python3 -m http.server 8080

Expected output:

Serving HTTP on 0.0.0.0 port 8080

Now open a browser and visit:

http://localhost:8080

You should see a directory listing page.

This service represents an **internal application running on port 8080** that will later be protected using Zero Trust access policies.

## Step 3 — Implement Micro-Segmentation using Tailscale ACLs

Zero Trust architectures restrict access to specific resources instead of allowing unrestricted network access.

To implement micro-segmentation, we configure an Access Control List (ACL) policy in the Tailscale Admin Console.

Open the admin console:

https://login.tailscale.com/admin

Navigate to **Access Controls** and modify the policy.

Example rule:

{
"grants": [
{
"src": ["user_identity"],
"dst": ["*"],
"ip": ["*:8080"]
}
]
}

This rule allows the user to access only the service running on port 8080.

All other ports and services are blocked, preventing lateral movement within the network.

