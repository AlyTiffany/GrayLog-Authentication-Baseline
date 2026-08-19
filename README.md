# Active Directory Authentication Baseline – Graylog

## Overview

I created a Graylog dashboard to establish a baseline of normal Windows authentication activity within an Active Directory environment. The goal is to understand typical authentication volume and source behaviour so that unusual activity can be identified more easily during security monitoring and investigation.

> **Note:** Identifying network information has been redacted from the dashboard screenshot.

![Graylog Authentication Baseline Dashboard](GrayLog_Dashboard.png)

## Dashboard Metrics

The dashboard currently tracks:

- **Successful logons – last 24 hours** using Windows Event ID **4624**
- **Failed logons – last 24 hours** using Windows Event ID **4625**
- **Successful logons over 7 days** to identify normal authentication patterns and changes in volume
- **Failed logons over 7 days** to identify spikes or unusual failure patterns
- **Top successful logon source IPs** to establish which sources normally generate authentication activity
- **Top failed logon source IPs** to identify the systems most frequently associated with authentication failures
- **Top Failed Logon Accounts (not visible in screenshot)
- **Top Failed Logon Devices (not visible in screenshot)
- **Privileged Account Logons (not visible in screenshot)

## Baselining Approach

A single day's authentication activity does not provide enough context to determine whether activity is unusual. I am using the dashboard to collect and compare authentication data over time and establish what normal behaviour looks like within the environment.

The initial baseline focuses on:

- Typical daily successful and failed logon volumes
- Normal variation between days
- Recurring high-volume authentication sources
- Sources that regularly generate failed authentication attempts
- New or unusual source IPs
- Significant deviations from established authentication patterns

The initial baseline will be developed over approximately **30 days**. Once enough historical data has been collected, it can be used to determine normal ranges and identify activity that warrants further investigation.

## Security Value

Baselining provides context that static thresholds alone cannot. A large number of failed logons may be normal for one environment but highly unusual for another.

Establishing normal authentication behaviour makes it easier to recognize:

- Sudden increases in failed authentication
- Abnormal increases in overall authentication volume
- New or unexpected authentication sources
- Significant changes in the behaviour of known sources
- Patterns that may warrant investigation for password spraying, brute-force attempts, stale credentials, misconfigured services, or other authentication issues

## Next Steps

As additional baseline data is collected, I plan to use it to define meaningful thresholds and identify deviations from normal behaviour. The dashboard can then support both routine monitoring and investigation by providing historical context for authentication activity.
