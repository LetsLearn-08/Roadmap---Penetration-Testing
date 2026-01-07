# 📊 Splunk Dashboards & Alerts

This document explains how to create dashboards and alerts in Splunk for SOC monitoring.

---

## 📥 Prerequisites
- Splunk VM integrated with Windows SOC VM logs

---

## 📊 Dashboard Creation
1. In Splunk Web → **Search & Reporting**
2. Run query:
   `index=winlogs EventCode=4625`
(Failed login attempts)
3. Save as dashboard panel → “Failed Logins”

✅ *Verification*: Dashboard shows login failures.  
📸 *Screenshot*: `images/splunk-dashboard.png`

---

## 🚨 Alert Setup
1. Create alert for multiple failed logins:
`index=winlogs EventCode=4625 | stats count by Account_Name`
2. Trigger if count > 5 in 10 minutes
3. Action: Email or log entry

✅ *Verification*: Alert triggers on simulated brute force.  
📸 *Screenshot*: `images/splunk-alert.png`

---

## 🎯 Goal
Provide visibility into suspicious activity and automate detection with Splunk dashboards.

