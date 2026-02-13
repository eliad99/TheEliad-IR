# /var/log in Linux
## Log Files, Locations & DFIR / SOC Reference Guide

---

## Overview
# Summary

The `/var/log` directory in Linux systems stores system logs, service logs, security logs, and application logs.

The `/var/log` directory is critical for:

- Security monitoring
- Incident response
- Threat detection
- Troubleshooting
- Compliance auditing


Most logs are plain text and can be viewed using:

    cat
    less
    tail
    tail -f
    grep

Example:

    tail -f /var/log/syslog

---

# Core System Logs

## /var/log/syslog
General system activity log (Debian/Ubuntu systems).

Contains:
- Service events
- System messages
- Kernel messages (non-critical)
- Cron activity

---

## /var/log/messages
General system log (RHEL/CentOS systems).

Similar purpose to syslog.

---

## /var/log/kern.log
Kernel-specific logs.

Contains:
- Kernel errors
- Hardware issues
- Driver problems
- Boot-time messages

---

## /var/log/dmesg
Boot and hardware-related messages.

View using:

    dmesg

---

# Authentication & Security Logs

## /var/log/auth.log  (Debian/Ubuntu)
Authentication logs.

Contains:
- SSH login attempts
- sudo usage
- Failed login attempts
- User switching
- PAM activity

SOC Relevance:
- Brute force detection
- Privilege escalation tracking
- Suspicious logins

---

## /var/log/secure  (RHEL/CentOS)
Equivalent to auth.log.

---

## /var/log/faillog
Failed login attempts database.

View with:

    faillog

---

## /var/log/lastlog
Last login information per user.

View with:

    lastlog

---

## /var/log/wtmp
Successful login history.

View with:

    last

---

## /var/log/btmp
Failed login attempts history.

View with:

    last -f /var/log/btmp

---

# Package Management Logs

## Debian / Ubuntu

### /var/log/dpkg.log
APT package installation and removal history.

### /var/log/apt/history.log
APT command history.

### /var/log/apt/term.log
APT installation output.

---

## RHEL / CentOS

### /var/log/yum.log
YUM package manager activity.

### /var/log/dnf.log
DNF package manager activity.

---

# Service & Application Logs

## /var/log/apache2/
Apache web server logs (Debian/Ubuntu).

Contains:
- access.log
- error.log

---

## /var/log/httpd/
Apache logs (RHEL/CentOS).

---

## /var/log/nginx/
Nginx web server logs.

Contains:
- access.log
- error.log

---

## /var/log/mysql/
MySQL database logs.

May include:
- error.log
- slow query log

---

## /var/log/postgresql/
PostgreSQL logs.

---

## /var/log/mail.log
Mail server activity (Postfix, Exim, etc.).

---

## /var/log/cron
Cron job activity.

---

# Boot & System Startup Logs

## /var/log/boot.log
System boot messages.

---

# Systemd Journal (Modern Systems)

Most modern Linux distributions use systemd.

Logs are stored in:

    /var/log/journal/

View logs using:

    journalctl

Examples:

    journalctl -xe
    journalctl -u ssh
    journalctl --since "1 hour ago"

---

# Log Rotation

Linux uses logrotate to manage log sizes.

Configuration:

    /etc/logrotate.conf
    /etc/logrotate.d/

Rotated logs appear as:

    syslog.1
    syslog.2.gz
    auth.log.1
    auth.log.2.gz

Compressed logs can be viewed using:

    zcat
    zless
    zgrep

---

# DFIR & SOC Investigation Quick Commands

Search failed SSH attempts:

    grep "Failed password" /var/log/auth.log

Find sudo usage:

    grep "sudo" /var/log/auth.log

Find suspicious IP address:

    grep "192.168.1.50" /var/log/auth.log

Monitor logs live:

    tail -f /var/log/syslog

List login history:

    last

Check failed logins:

    last -f /var/log/btmp

---
