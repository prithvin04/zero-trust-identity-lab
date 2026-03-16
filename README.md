# Zero Trust & Identity Lab

## Overview

This project demonstrates a hands-on implementation of **Zero Trust Architecture (ZTA)** based on the concepts described in NIST SP 800-207.

The lab guides learners through building a simple environment where access to an internal service is controlled using identity-based networking, micro-segmentation, and least-privilege access control.

The environment is built using free and open tools including **Tailscale, Linux RBAC, and Generative AI for log analysis**.

---

## Learning Objectives

After completing this lab, learners will be able to:

• Understand the principles of Zero Trust Architecture
• Configure identity-based connectivity using Tailscale
• Implement micro-segmentation using access control policies
• Apply the principle of least privilege using Linux sudo rules
• Use Generative AI to analyze authentication logs

---

## Technology Stack

| Component      | Purpose                          |
| -------------- | -------------------------------- |
| Tailscale      | Identity-based networking (ZTNA) |
| Ubuntu Linux   | Server environment               |
| GitHub SSO     | Identity provider                |
| Tailscale ACLs | Micro-segmentation policies      |
| Linux sudoers  | Role-based access control        |
| auth.log       | Security monitoring              |
| Generative AI  | Log analysis and explanation     |

---

## Lab Guide

The complete step-by-step lab instructions are available here:

➡ **GitHub Pages Lab Guide**
https://prithvin04.github.io/zero-trust-identity-lab

---

## Architecture

The lab demonstrates the transition from traditional perimeter security to **identity-centric Zero Trust networking**.

Key security controls implemented:

1. Identity-centric connectivity
2. Micro-segmentation of network services
3. Principle of least privilege
4. AI-assisted security monitoring

---

## Repository Structure

```
zero-trust-identity-lab
│
├── README.md
├── docs
│   └── index.md      # Full lab guide (GitHub Pages)
```

---

## Author

Prithvin M
Cyber Security Internship Technical Challenge Submission

