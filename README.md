# Zero Trust & Identity Lab

## Overview

This project demonstrates a **hands-on implementation of Zero Trust Architecture (ZTA)** using open-source tools.

Traditional networks rely on perimeter-based security where devices inside the network are automatically trusted.  
Zero Trust removes this assumption and verifies **every user, device, and request before granting access**.

In this lab, we build a simple environment that demonstrates key Zero Trust security principles including:

- Identity-based connectivity
- Micro-segmentation
- Least privilege access control
- AI-assisted log analysis

The lab is designed so that **beginners with minimal security knowledge can follow it step-by-step**.

---

## Learning Objectives

After completing this lab you will be able to:

- Understand the concept of **Zero Trust Architecture**
- Configure **identity-based networking using Tailscale**
- Deploy a simple internal service
- Implement **micro-segmentation using access control policies**
- Apply the **Principle of Least Privilege** in Linux
- Use **Generative AI to analyze security logs**

---

## Technology Stack

| Tool | Purpose |
|-----|--------|
| Tailscale | Identity-based networking |
| Ubuntu Linux | Server environment |
| GitHub SSO | Identity provider |
| Tailscale ACLs | Micro-segmentation |
| Linux sudoers | Role-based access control |
| auth.log | Security monitoring |
| Generative AI | Log analysis |

---

## Lab Guide

The complete beginner-friendly lab instructions are available here:

👉 **GitHub Pages Lab Guide**

https://prithvin04.github.io/zero-trust-identity-lab

---

## What This Lab Demonstrates

This lab demonstrates the transition from traditional network trust to a **Zero Trust security model**.

Key security concepts implemented:

1. **Identity-Centric Connectivity**  
   Users authenticate using GitHub identity through Tailscale.

2. **Micro-Segmentation**  
   Network access is restricted to a specific service (port 8080).

3. **Principle of Least Privilege**  
   A junior administrator account can only restart a service.

4. **AI-Assisted Security Analysis**  
   Generative AI helps interpret authentication logs.

---

## Repository Structure

```
zero-trust-identity-lab
│
├── README.md
├── docs
│   └── index.md     # Complete lab guide
```

---

## Author

**Prithvin M**

Cyber Security Internship Technical Challenge Submission
