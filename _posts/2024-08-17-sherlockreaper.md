---
title: SHERLOCKS REAPER - Writeups
categories: [DFIR]
tags: [sherlocks]
image: /assets/thumbnails/reaper.jpg
---

## Reaper - Very Easy - [Room Link](https://app.hackthebox.com/sherlocks/Reaper)

### Scenarious 

```
Our SIEM alerted us to a suspicious logon event which needs to be looked at immediately . The alert details were that the IP Address and the Source Workstation name were a mismatch .You are provided a network capture and event logs from the surrounding time around the incident timeframe. Corelate the given evidence and report back to your SOC Manager.
```

### Task 1 : What is the IP Address for Forela-Wkstn001? 

> Answer : 172.17.79.129

![image](https://github.com/user-attachments/assets/9d1f4966-abcc-45cc-84f5-b896c62a739a)
 
> Open the `pcapng` file, view the packets, the `3rd` packets, can clearly see in the packet info mentioned `Forela-Wkstn001?` with `nbns` or `netbios` protocol (protocols that a Windows computer uses to look for a host on the internal network when a host's IP address cannot be resolved through the organizational DNS).

### Task 2 : What is the IP Address for Forela-Wkstn002?

> Answer : 172.17.79.136

![image](https://github.com/user-attachments/assets/a6b48a25-7ccc-41d4-8c01-fd45242ea4b9)

> Same as the first task, but instead of looking each packet, we can just filter packets with  the `nbns` protocol.

### Task 3 : Which user account's hash was stolen by attacker? 

> Answer : Arthur Kyle

![image](https://github.com/user-attachments/assets/4098f06e-db5c-41b1-86a5-48b90aeae826)

> Filter the the packets with `ntlmssp` protocol and look for weird authentication logo event. found a logon event under name `Arthur.Kyle`


### Task 4 : What is the IP Address of Unknown Device used by the attacker to intercept credentials?

> Answer : 172.17.79.135

![image](https://github.com/user-attachments/assets/10e1a87a-11de-48db-9d52-b1b982caa9ae)

> The hint say that to `Look for an IP Address that do not belong to any workstation but is involved in authentication flow for the victim user.`, using the same fither `ntlmssp`, as you can see there is only one ip that does not belong to anyworkstation but involved in the authentication.


### Task 5 : What was the fileshare navigated by the victim user account?

> Answer : \\DC01\Trip

![image](https://github.com/user-attachments/assets/a515c15d-e722-4f6b-8bd1-53fcc60c824a)

> Filter packets with `smb2` protocol, and Search for keywords "BAD_NETWORK_NAME" in packet details.

### Task 6 : What is the source port used to logon to target workstation using the compromised account?

![image](https://github.com/user-attachments/assets/63996df5-30eb-4f16-8be6-8a7942c5a583)

> Open the eventlog file, filter log with event ID `4624` and search for source port in the events log details.

### Task 7 : What is the Logon ID for the malicious session?

> Answer : 0x64A799

![image](https://github.com/user-attachments/assets/b7bd93a6-a257-46ac-aba3-deb3967c6440)

> In the same event properties from task 6, view the details to find the logon ID.


### Task 8 : The detection was based on the mismatch of hostname and the assigned IP Address.What is the workstation name and the source IP Address from which the malicious logon occur?

> Answer : FORELA-WKSTN002, 172.17.79.135

![image](https://github.com/user-attachments/assets/852bdaa4-c79a-44c5-906f-fb29d4879d43)

> Still in the same event log properties, in the `Network infromation`, view the workstation and ip address stated.

### Task 9 : When did the malicious logon happened. Please make sure the timestamp is in UTC?

> Answer : 2024-07-31 04:55:16

![image](https://github.com/user-attachments/assets/3f5da1eb-a5cb-44ab-a0fa-c89fbc0caa5a)

> Same log properties, click on the `details` tab, view in `XML` view, search for keyword `TimeCreated SystemTime`

### Task 10 : What is the share Name accessed as part of the authentication process by the malicious tool used by the attacker?

> Answer : \\*\IPC$

![image](https://github.com/user-attachments/assets/11476dff-8263-448f-84c2-44801bc5cca3)

> Filter log with `5140` or task category `File Share`, look for `Share Information` and the answer is under the `share name`





