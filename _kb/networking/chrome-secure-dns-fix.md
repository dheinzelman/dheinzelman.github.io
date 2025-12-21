---
layout: kb_article
title: "Troubleshooting: Chrome Secure DNS Connection Issues"
category: networking
last_updated: 2025-12-21
tags: [chrome, dns, networking, macos]
---

## Overview

Modern browsers like Chrome often use **Secure DNS** (DNS over HTTPS) by default. While this improves privacy, it can cause connection failures on restrictive networks (e.g., corporate VPNs, public Wi-Fi) or conflict with local network configurations (like Pi-hole).

This guide documents the steps to diagnose and resolve "This site can't be reached" errors caused by Secure DNS conflicts.

## Symptoms

* Websites fail to load with `ERR_CONNECTION_REFUSED` or `DNS_PROBE_FINISHED_NXDOMAIN`.
* Internet connection works for other applications (Slack, Spotify).
* Issue persists across different Wi-Fi networks.

<div class="kb-callout warning">
  <strong>Warning:</strong> Disabling Secure DNS may expose your browsing requests to your ISP or network administrator. Only disable it if necessary for connectivity.
</div>

## Solution: Disable Secure DNS

1.  Open Chrome Settings (`chrome://settings`).
2.  Navigate to **Privacy and security** > **Security**.
3.  Scroll down to the **Advanced** section.
4.  Locate "Use Secure DNS".
5.  Toggle the switch to **OFF** (or select "With your current service provider").

## Verification

To verify the fix, flush your local DNS cache and restart the browser.

<div class="kb-callout note">
  <strong>Terminal Command (macOS):</strong><br>
  <code>sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder</code>
</div>

Refresh the page. If the site loads, the issue was a Secure DNS conflict.