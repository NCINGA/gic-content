# ---
title: AAA Service Restart Procedure
document_id: [insert document id]
document_type: guide
version: 1.0.0
category: [insert category]
subcategory: [insert subcategory]
status: draft
department: [insert department name]
division: [insert division name]
authority: [insert authority]
language: english
available_translations: [english]
published_date: [insert YYYY-MM-DD]
last_updated: 2026-05-11
next_review: [insert YYYY-MM-DD]
applicable_laws: [insert applicable laws]
geographic_scope: national
contact_division: [insert division name]
contact_phone: [insert country code and phone number]
contact_email: [insert official email address]
---
AAA Service Restart Procedure.pdf

## Page 1

AAA Service Restart Procedure 
Version 1.0.0

## Page 2

Document Information 
Prepared By: 
Shachini Thakshila 
Date:2026-05-11 
1.0.0v 
Reviewed By: 
Dilshani Abeywickrama 
Date:2026-05-11 
1.0.0v

## Page 3

Table of Content 
1. Purpose​
4 
2. Scope​
4 
3. Pre-Checks​
4 
4. Recommended Restart Procedure​
5 
4.1 Restart MySQL Database​
5 
4.2 Restart Vault Service​
5 
4.3 Restart Vault Agent​
6 
4.4 Restart UIB Service​
6 
4.5 Restart RADIUS Service​
6 
4.6 Restart Reset Cycle Service​
7 
4.7 nginx Service​
7 
5. Post Restart Validation​
7 
5.1 Verify Service Status​
7 
5.2 Verify UIB Logs​
8 
6. Additional Notes​
8

## Page 4

None
1. Purpose 
This document defines the standard procedure to safely restart AAA system services in a 
controlled and consistent manner. 
2. Scope 
This procedure applies to all AAA-related services deployed in the environment, including: 
●​ MySQL Database (mysqld.service) 
●​ RADIUS Server (radiusd.service) 
●​ UIB Service (uib.service) 
●​ Vault Service (vault.service) 
●​ Vault Agent (vault-agent-freeradius.service) 
●​ Reset Cycle Service (resetcycled.service) 
●​ Nginx Service (nginx.service) 
This procedure applies to both Production and Disaster Recovery (DR) environments. 
3. Pre-Checks 
Before performing any restart activity, verify the current status of all services as mentioned 
below. 
systemctl status mysqld.service 
systemctl status radiusd.service 
systemctl status uib.service 
systemctl status vault.service 
systemctl status vault-agent-freeradius.service 
systemctl status resetcycled.service 
systemctl status nginx.service

## Page 5

None
None
4. Recommended Restart Procedure 
 
The restart procedure must be performed strictly in the order specified below. 
 
Note 1: The systemctl status commands can be executed using a non-root user with the 
required permissions. Service restart operations require root or sudo privileges. 
 
Note 2: Restart activities should be performed during an approved maintenance window to 
minimize service impact. 
4.1 Restart MySQL Database 
 
systemctl restart mysqld.service 
systemctl status mysqld.service 
 
Validation: 
●​ MySQL service is in an active (running) state 
●​ No database startup errors are observed in /var/log/mysql/mysqld.log 
4.2 Restart Vault Service 
 
systemctl restart vault.service 
systemctl status vault.service 
 
Validation: 
 
●​ Vault service should be in an active (running) state 
●​ No startup errors observed in the logs 
 
Note: If Vault enters a sealed state after a server reboot or service restart, perform the Vault 
Unseal Procedure provided in Section 6.

## Page 6

None
None
None
4.3 Restart Vault Agent 
 
systemctl restart vault-agent-freeradius.service 
systemctl status vault-agent-freeradius.service 
 
Validation: 
●​ Vault agent service should be in an active (running) state 
●​ No token or authentication-related errors are observed 
●​ Check the logs using journalctl -u vault-agent-freeradius.service -b for 
any startup errors 
4.4 Restart UIB Service 
 
systemctl restart uib.service 
systemctl status uib.service 
Validation: 
●​ Service is running successfully 
●​ No errors observed in /opt/uib/logs 
4.5 Restart RADIUS Service 
 
 
systemctl restart radiusd.service 
systemctl status radiusd.service 
Validation: 
●​ No module loading errors 
●​ Database connectivity is successful 
●​ Authentication requests are being processed successfully ( check the logs at 
/usr/local/var/log/radius/radius.log for errors)

## Page 7

None
None
None
4.6 Restart Reset Cycle Service 
 
systemctl restart resetcycled.service 
systemctl status resetcycled.service 
Note: 
●​ In High Availability (HA) deployments, resetcycled.service should run only on the active 
node to avoid duplicate processing. 
4.7 nginx Service 
 
systemctl restart nginx.service 
systemctl status nginx.service 
 
Validation: 
 
●​ nginx service is in active (running) state 
●​ No errors are observed in the nginx logs 
 
 
5. Post Restart Validation 
5.1 Verify Service Status 
 
 
systemctl status mysqld.service radiusd.service uib.service vault.service 
vault-agent-freeradius.service resetcycled.service nginx.service 
 
Expected: 
●​ All services should be in an active (running) state

## Page 8

None
None
5.2 Verify UIB Logs 
 
tail -500f /opt/uib/logs/uib.log 
Expected: 
●​ No database connectivity or API-related errors 
 
6. Additional Notes 
Note: Vault is sealed after a reboot because it is designed to be in a locked state, requiring 
authorization to decrypt the master key and access data. 
If Vault enters a sealed state after a server reboot or service restart, perform the Vault Unseal 
Procedure below. 
 
Vault Unseal Procedure 
 
export VAULT_ADDR=http://127.0.0.1:8200 
vault operator unseal ​
## Use three keys to unseal the vault 
export VAULT_TOKEN=“<initial_root_token>” 
systemctl restart vault-agent-freeradius.service 
 
The Vault unseal keys and initial root tokens are not included in this document and are shared 
separately through secure channels.
