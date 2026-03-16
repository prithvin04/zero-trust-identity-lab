# Zero Trust & Identity Lab

## What This Project Is About

Most traditional computer networks trust devices once they are inside the network.

For example, if a device connects to a company network or VPN, it may automatically gain access to internal systems.

This approach can be risky. If an attacker gains access to the network, they may be able to move freely between systems.

**Zero Trust Architecture (ZTA)** removes this assumption. Instead of trusting devices automatically, every user and device must be **verified before access is granted**.

This project provides a **beginner-friendly lab** that demonstrates how Zero Trust security concepts can be implemented using simple tools.

Even if you have **no prior experience**, you should be able to follow the instructions step-by-step.

---

## What You Will Learn

By completing this lab, you will learn how to:

- Create an identity-based network using **Tailscale**
- Deploy a simple internal service on a Linux system
- Restrict network access using **micro-segmentation**
- Apply the **Principle of Least Privilege**
- Use **Generative AI** to analyze authentication logs

These concepts are widely used in modern cybersecurity environments.

---

## Tools Used in This Lab

The following tools are used in this project:

| Tool | Purpose |
|-----|--------|
| Tailscale | Creates a secure identity-based network |
| Ubuntu Linux | Provides the server environment |
| GitHub SSO | Used for identity authentication |
| Tailscale ACLs | Restricts access to specific services |
| Linux sudoers | Controls administrative permissions |
| auth.log | Stores authentication activity |
| Generative AI | Helps analyze system logs |

---

## Who This Lab Is For

This lab is designed for:

- Students learning cybersecurity
- Beginners exploring Zero Trust concepts
- Anyone interested in modern network security

No previous experience with Zero Trust or Tailscale is required.

---

## Lab Guide

The full **step-by-step beginner guide** is available here:

**GitHub Pages Lab Guide**

https://prithvin04.github.io/zero-trust-identity-lab

Follow the instructions in the guide to complete the lab.

---

## What You Will Build

During this lab you will create a simple Zero Trust environment where:

1. A user authenticates using **GitHub identity**
2. A secure network is created using **Tailscale**
3. An internal web service runs on **port 8080**
4. Network access is restricted using **micro-segmentation policies**
5. A limited administrator account is created
6. System logs are analyzed using **AI tools**

This demonstrates how Zero Trust security works in practice.

---

## Repository Structure

```
zero-trust-identity-lab
│
├── README.md
└── docs
    └── index.md   # Full beginner-friendly lab guide
```

---

## Author

Prithvin M  
Cyber Security Internship Technical Challenge Submission
