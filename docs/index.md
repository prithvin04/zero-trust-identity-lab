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

