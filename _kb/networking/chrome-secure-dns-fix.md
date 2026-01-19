---
layout: term
title: "Detailed Resolution Summary: Chrome Policy Lockout"
category: networking
last_updated: 2025-05-20
tags: [chrome, macos, policy, troubleshooting]
---

This document summarizes the troubleshooting steps and final resolution for enabling the "Use secure DNS" setting in Google Chrome on macOS when it was disabled by a persistent enterprise policy.

### **1\. The Core Problem**

* **Symptom:** The "Use secure DNS" setting was greyed out in Chrome settings with the message **"This setting is disabled on managed browsers."**
* **Diagnosis (chrome://policy):** The browser was locked by the policy key **BuiltInDnsClientEnabled** set to **false**.  
* **Source of Policy:** The policy was consistently tagged as **Source: Platform**, indicating it was enforced by the macOS system layer (a remnant of the user's previous corporate environment.  
* **Challenge:** The policy was exceptionally tenacious, persisting after the deletion of common configuration files, suggesting it was being immediately re-injected or stored in a deep system cache.

### **2\. Required Diagnostic Steps (Confirmed Lockout)**

| Step | Action | Outcome | Policy Status |
| :---- | :---- | :---- | :---- |
| **Initial Check** | chrome://policy analysis. | Confirmed BuiltInDnsClientEnabled: false and Source: Platform. | **LOCKED** |
| **Constraint Check** | Ruled out Google Advanced Protection Program as the cause. | The policy conflict did not align with APP's known control points. | **LOCKED** |
| **Profile Check (Step 1\)** | Checked macOS System Settings for Configuration Profiles. | No profiles found or removal was ineffective. | **LOCKED** |

### **3\. Execution of Cleanup (The Escalation)**

The fix required sequentially escalating cleanup actions, specifically targeting known preference locations for system, managed, and user settings until the policy enforcement was removed.

| Escalation Level | Command(s) Executed | Purpose | Final Policy Status |
| :---- | :---- | :---- | :---- |
| **Tier 1: System/Cloud Policy Files** | sudo rm \-f /Library/Preferences/com.google.Chrome.plist sudo rm \-f /Library/Managed\\ Preferences/com.google.Chrome.plist rm \-rf \~/Library/Application\\ Support/Google/Chrome\\ Cloud\\ Enrollment/\* | Remove all common system-wide and cloud management policy files. | **Still Locked** |
| **Tier 2: User-Level Policy Files** | rm \-f \~/Library/Preferences/com.google.Chrome.plist | Remove the primary user-level preference file. | **Still Locked** |
| **Tier 3: The Nuclear Cleanup (Successful Break)** | defaults read com.google.Chrome (Diagnostic to confirm domain deletion). | Confirmed the preference domain itself was gone, isolating the issue to caching/re-injection. | N/A |
|  | **rm \-rf \~/Library/Application\\ Support/Google/Chrome/Default/Preferences rm \-rf \~/Library/Application\\ Support/Google/Chrome/Local\\ State** | **Final, successful action:** Deleted core, non-synced user configuration files and the local state file, forcing Chrome to rebuild its settings without the policy artifact. | **Policy Removed** |
|  | sudo killall cfprefsd | Force-cleared the macOS preference caching daemon. | **Policy Removed** |

### **4\. Final Status**

After executing the Tier 3 cleanup and relaunching Chrome:

* **Policy Verification:** The chrome://policy page displayed **"No policies set"** for Chrome Policies.  
* **Functionality:** The **"Use secure DNS"** toggle became **enabled and fully functional** for the user to control.