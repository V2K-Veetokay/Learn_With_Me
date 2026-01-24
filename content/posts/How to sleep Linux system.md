---
date: 2026-01-24
title: Sleep Linux system
weight: 10
tags:
  - Linux
linktitle: Sleep Linux System
---


**Use systemctl to suspend, hibernate, or hybrid-sleep from a terminal.**

Common commands (run as your user with sudo if needed):

- Suspend (RAM sleep):
  `sudo systemctl suspend`

- Hibernate (to disk):
  `sudo systemctl hibernate`

- Hybrid-sleep (hibernate then suspend — safe for laptops):
  `sudo systemctl hybrid-sleep`

Notes:
- Ensure swap is large enough for hibernate (>= RAM) and hibernation is enabled in your bootloader (resume kernel param).  
- To test without sudo (if polkit permits): systemctl suspend
- To check available targets: systemctl list-units --type=target