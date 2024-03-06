# Suspicious-Files-Labs

## Objective
In this scenario, I've received an alert about a suspicious file being downloaded on an employee's computer. After investigating the alert I've discover that the employee received an email containing an attachment. The attachment was a password-protected spreadsheet file. The spreadsheet's password was provided in the email. The employee downloaded the file, then entered the password to open the file. When the employee opened the file, a malicious payload was then executed on their computer. 

## Investigation
I have retreived the malicious file and have created a SHA 256 hash of the file. The hash output is: 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b

The timeline leading up to this alert is as follows:
1:11 p.m.: An employee receives an email containing a file attachment.

1:13 p.m.: The employee successfully downloads and opens the file.

1:15 p.m.: Multiple unauthorised executable files are created on the employee's computer.

1:20 p.m.: An intrusion detection system detects the executable files and sends out an alert to the SOC.

### Virus Total Results
Searching Virus Total, the community score of the file is shown as 57/71 as can be seen by the image below. This shows that 57 security cendors and 3 sandboxes flagged the file as malisious. 

![image](https://github.com/JustA-Byte/Suspicious-Files-Labs/assets/161458321/c76ad1b2-427b-4f2f-bce9-48e82ed41e33)

Looking into the details tab of the results shows information around network connections, relations, behaviour of the malware and TTPs.

### Addressing this incident using the 5 W's

- <b>Who</b>; Malicious actors wishing to infect host systems within the business
- <b>What</b>; A phishing email was sent to an employee which had a password protected attachment containing malware. Once the file was accessed using the password, the malware activated and further executable files were created on the host system.
- <b>When</b>; between 1:11pm-1:20pm
- <b>Where</b>; an employee’s computer at a financial services company
- <b>Why</b>: malicious actors wanting access to the system to steal input information. 

### Summary
This seems like the initial stages of infection that could lead to more severe outcomes like customer data exfiltration. The malware included data input monitoring, defensive evasion techniques and direction to malicious URLs. Poorly configured IDS may not have picked this malware up which could definitely have caused harm to customer and company data.
