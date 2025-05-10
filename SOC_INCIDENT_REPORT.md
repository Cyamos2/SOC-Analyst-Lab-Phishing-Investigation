# SOC Incident Report – Phishing Investigation

## Executive Summary
> Brief description of the alert, what was investigated, and the outcome.

## Timeline of Events
| Time (UTC) | Event |
|------------|-------|
| 2025-05-10 13:42 | User reported suspicious email |
| ...        | ...   |

## Indicators of Compromise
See `IOC_LOG.md`

## Analysis
Typed in the link to both places. One was showing Fortinet as a phishing attempt and the other produced a 400 HTTP error.

## Outcome
Improved phishing simulations and awareness.

The investigation determined that the phishing email originated from an external threat actor using a spoofed domain. One user clicked the malicious link but did not enter credentials. Another user reported the email to the SOC, enabling a timely response.

The following actions were taken:
- The domain securelogin-verification.com was blocked at the firewall and email gateway.
- All endpoints that communicated with the domain were scanned for malware; no payload was found.
- A communication was sent to all staff to alert them to the phishing attempt.
- The incident was documented for compliance, and the IOCs were added to threat detection feeds.

## Lessons Learned
- Were there any detection gaps?
-   Yes, the phishing email bypassed the organization's initial spam filter and was not flagged by the email security gateway. Additionally, there was no immediate alert generated when the domain was first accessed, indicating a need to improve URL reputation monitoring and integrate threat intelligence feeds into the SIEM more effectively.
- Did user awareness training help?
-   Yes, user awareness training proved valuable--one of the targeted users recognized the suspicious email format and reported it to the SOC before entering credentials. This proactive response limited exposure and allowed a quicker investigation and response.
- Any recommendations for the future?
-   Implement real-time URL scanning and sandboxing for all external email links.
-   Updated email filters to flag domains similar to internal company names (ex. lookalike domains).
-   Continue regular phishing simulations and reinforce training on how to identify spoofed domains and suspicious requests.
-   Review SIEM alerting rules to include newly observed IOCs like the domain used in this attack.
