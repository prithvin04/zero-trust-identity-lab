# Zero Trust & Identity Lab

## Introduction

Traditional computer networks often trust devices once they are inside the network.  
For example, if a device connects to an office Wi-Fi or VPN, it may automatically gain access to internal systems.

This can be risky because if an attacker gains access to the network, they may be able to move between systems easily.

**Zero Trust Architecture (ZTA)** removes this assumption.  
Instead of trusting devices automatically, every user and device must be **verified before access is granted**.

In this lab you will build a simple environment that demonstrates how Zero Trust security works.

This guide is written so that **someone with little or no prior experience can follow it step-by-step**.

---

## Prerequisites

Before starting this lab, make sure you have:

- A computer running **Windows, macOS, or Linux**
- An **Ubuntu Linux environment** (WSL, Virtual Machine, or native install)
- A **GitHub account**
- Internet connection
- Basic ability to run commands in a terminal

---

## Lab Objectives

After completing this lab you will be able to:

- Understand the concept of **Zero Trust Architecture**
- Configure **identity-based networking using Tailscale**
- Deploy a simple internal service
- Implement **micro-segmentation**
- Apply the **Principle of Least Privilege**
- Use **Generative AI to analyze authentication logs**

---

## Architecture Overview

The diagram below shows the architecture used in this lab.

```mermaid
graph TD

User[Security Analyst]

User -->|GitHub Login| Tailscale[Tailscale Identity Network]

Tailscale --> Server[Ubuntu Server]

Server --> Service[Internal Web Service :8080]

Server --> Logs[Authentication Logs]

Logs --> GenAI[Generative AI Analysis]

GenAI --> Analyst[Security Insight]
```

In this architecture:

- The user authenticates using **GitHub**
- Tailscale creates a **secure identity-based network**
- The Ubuntu server runs an internal service
- Access policies restrict network access
- Authentication logs can be analyzed using AI

---

# Step 1 — Configure Identity-Based Connectivity

Traditional networks rely on **IP-based trust**, where devices inside the network are automatically trusted.

Zero Trust systems verify **identity instead of network location**.

In this step we will use **Tailscale** to create a secure identity-based network.

---

## Open a Terminal

If you are using **Ubuntu on WSL**:

1. Open the **Ubuntu application** on your computer.
2. A terminal window will appear.
3. All commands in this guide should be run in this terminal.

---

## Install Tailscale

Run the following command:

```
curl -fsSL https://tailscale.com/install.sh | sh
```

This command downloads and installs the Tailscale software.

---

## Start Tailscale

Run:

```
sudo tailscale up
```

A browser window will open asking you to authenticate.

Choose **GitHub login**.

---

## Verify the Connection

Run:

```
tailscale status
```

Example output:

```
100.x.x.x   ubuntu-server   username@   linux
```

If you see an IP address starting with **100.x.x.x**, your device has successfully joined the Tailscale network.

---

**Tip:**  
Your output may look slightly different. That is normal.

---

### Why This Step Matters

Identity verification ensures that only **authenticated users and devices** can join the network.

This is one of the core ideas of **Zero Trust security**.

---

# Step 2 — Deploy a Protected Service

Next we create a simple internal service.

Run:

```
python3 -m http.server 8080
```

Expected output:

```
Serving HTTP on 0.0.0.0 port 8080
```

Open a browser and go to:

```
http://localhost:8080
```

You should see a **directory listing page**.

---

### Why This Step Matters

This web server represents an **internal application** that must be protected from unauthorized access.

---

# Step 3 — Implement Micro-Segmentation

Micro-segmentation restricts access to specific services instead of allowing full network access.

This prevents attackers from moving between systems inside the network.

Open the Tailscale admin console:

```
https://login.tailscale.com/admin
```

Navigate to:

```
Access Controls
```

Replace the policy with the following example:

```json
{
  "grants": [
    {
      "src": ["user_identity"],
      "dst": ["*"],
      "ip": ["*:8080"]
    }
  ]
}
```

Explanation:

- `src` → user identity  
- `dst` → destination device  
- `ip` → allowed port  

This rule allows access **only to port 8080**.

---

### Why This Step Matters

Even if a user joins the network, they cannot access every service.

This reduces the risk of **lateral movement**.

---

# Step 4 — Apply the Principle of Least Privilege

The **Principle of Least Privilege** means that users should receive only the permissions necessary to perform their tasks.

---

## Create the User

Run:

```
sudo adduser junioradmin
```

Verify the user exists:

```
id junioradmin
```

---

## Configure Limited Administrative Access

Edit the sudo configuration:

```
sudo visudo
```

Add this rule at the bottom of the file:

```
junioradmin ALL=(ALL) NOPASSWD: /bin/systemctl restart nginx
```

This allows the user to restart the nginx service but nothing else.

---

## Test the Policy

Switch to the user:

```
su - junioradmin
```

Allowed command:

```
sudo systemctl restart nginx
```

Restricted command:

```
sudo cat /etc/shadow
```

The second command should be denied.

---

### Why This Step Matters

Limiting privileges reduces the damage that could occur if an account is compromised.

---

# Step 5 — Use Generative AI as a Security Copilot

Security analysts often review logs to identify suspicious activity.

View recent authentication logs:

```
sudo tail -n 20 /var/log/auth.log
```

Example log entry:

```
sudo: junioradmin : command not allowed ; COMMAND=/usr/bin/cat /etc/shadow
```

These logs can be analyzed using an AI assistant.

Example prompt:

```
Analyze the following Linux authentication logs.

Identify suspicious login attempts, privilege escalation attempts,
and potential security issues. Explain what happened and recommend
mitigation steps.
```

AI tools can help analysts:

- interpret log entries
- identify suspicious behavior
- suggest security improvements

---

# Conclusion

In this lab you implemented several important Zero Trust concepts:

- Identity-based networking
- Micro-segmentation
- Least-privilege access control
- AI-assisted log analysis

These techniques help organizations improve security by verifying identity, restricting access, and monitoring system activity.

---

# Check Your Understanding

1. What is the main idea behind Zero Trust Architecture?
2. Why is identity verification important in modern networks?
3. How does micro-segmentation reduce risk?
4. Why is least privilege important for system security?
