---
layout: post
title: "Server Clarity Sprint sample report"
date: 2026-11-09
author: Veruca Velharin
---

*Illustrative sample. This report describes a made-up business and a made-up server. No real client, system or data appears in it. It shows the shape and depth of a Sprint report.*

## About this engagement

- Client: Example Design Studio (fictional), a 9-person web agency
- Scope: 2 servers, web-01 (client websites) and files-01 (internal file share)
- Window: 10 business days
- Access: read-only SSH for the audit; write access only for fixes the client approved in writing

## Summary

Both servers are running and serving their sites, but neither would tell anyone if something went wrong. The biggest risks are backups that have not completed in three weeks and an operating system that leaves standard support in under six months. Three low-risk fixes were applied with approval. Four recommendations remain, in order of urgency.

## Findings

1. **Critical: backups failing silently.** The nightly backup job on files-01 has exited with an error since the 14th. Nothing alerted anyone. The most recent good copy is three weeks old.
2. **High: OS support ending soon.** web-01 runs Ubuntu 22.04 LTS, whose standard support ends in April 2027. Security updates after that need a paid extension or an upgrade.
3. **High: 41 pending security updates on web-01.** Automatic security updates were disabled at some point.
4. **Medium: disk at 87% on web-01.** Old log files are the main cause; at the current rate the disk fills in about seven weeks.
5. **Medium: SSH accepts passwords.** Key-only login is not enforced, and two former staff accounts still exist.
6. **Low: certificate renewal not tested.** Certificates renew automatically, but the renewal has never been checked end to end.

## Fixes applied (approved, within the 60-minute allowance)

- Rotated and compressed old logs on web-01, bringing disk use to 54%.
- Re-enabled automatic security updates on web-01 and applied the 41 pending updates after a snapshot.
- Disabled the two former staff accounts (not deleted, so nothing is lost).

## Recommendations

1. Fix the backup job and test a restore this week. A backup that has never been restored is a hope, not a backup.
2. Plan the move off Ubuntu 22.04 before April 2027.
3. Enforce key-only SSH once each current user has a key in place.
4. Run a test certificate renewal and confirm it succeeds.

## Monitoring set up during the Sprint

Checks configured for both servers: site reachability, certificate expiry, disk space, backup job result and pending security updates. Alerts go to the client's chosen address.

## Handover

A 30-minute walkthrough of this report, what changed, and what to watch for. The client keeps this document and all access.
