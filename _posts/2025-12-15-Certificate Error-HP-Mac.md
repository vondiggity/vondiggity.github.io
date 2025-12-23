---
title: "Certificate Error when adding a HP Printer to a Mac"
date: 2025-12-15 10:49:00 -0800
tags: [Sysadmin, Mac, HP Printer]
categories: [Blogging]
---


## HP Printer Certificate Error on a Mac

I received a ticket from a user who suddenly couldn’t print to the office printer, an HP Color LaserJet Enterprise M553. As a first step, I removed the printer and tried to add it back, but immediately ran into the following error:

**“Expired Certificate, check the printer for errors.”**

I logged into the printer’s web interface and confirmed that the self-signed certificate had indeed expired.

You can find it here:
**Security → Device Security → Certificates**

From there, I generated a new self-signed certificate. I set the expiration to three years, figuring the printer would likely be replaced before then based on recent history with many HP Laserjet printers.

Once the new certificate was in place, I was able to re-add the printer on the Mac without any issues, and printing was restored.

