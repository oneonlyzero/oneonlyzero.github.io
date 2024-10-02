---
title: Vesper Challenge- Writeups
categories: [Event,CTF]
tags: [OSINT]
image: /assets/thumbnails/vesper.png
---

About : Vesper challenge is another OSINT challenge from Hacktoria, but on another level of concept, theme, and storyboard. Inside the challenge there is 5 sub challenge with different storyboard that player need to solve. Therefore as appreciation for the challenge author, i create a post special for this chall only :3.

## Vesper Challenge - Insane 

###  1 Mission : Le Grand Prix de la Cyber

![Le Grand Prix de la Cyber](https://github.com/user-attachments/assets/d46a9d7b-b85d-4d84-b863-58bddd488121)

#### Briefing 

```
Welcome to "Le Grand Prix de la Cyber," the ultimate test of cyber security skills! In this high-stakes challenge, you'll dive deep into a sophisticated drive-by compromise attack targeting a single high-profile website: the official site of the Monaco Grand Prix (simulated for this challenge).

As a top-tier cybersecurity analyst, you've been called in to investigate suspicious activities on this prestigious site. Your mission is to uncover and neutralize a multi-stage drive-by attack orchestrated by a skilled adversary.

Throughout the challenge, you'll analyze different components of the website, each representing a crucial stage in the drive-by compromise attack chain. Your goal is to understand the attack methodology, identify vulnerabilities.
```

#### Answer Instruction 

```
Lauch the challenge Environment & Answer the questions 
```


#### Solution

```
1) Examine the JavaScript in the <head> of index. What malicious combination function is being used to obfuscate a data exfiltration attempt?
```

![image](https://github.com/user-attachments/assets/aaa8e6aa-8a13-4325-bb24-8ab95cd234cd)

> View the source code of the website index and scroll down to the `<script>` section and you will get the answer. `Answer : eval(atob)`

```
2) Investigate the third-party script loaded in index. What potentially dangerous JavaScript function is used to execute this script?
```

> Look at code snippet at the first question, instead of taking the full combination of the malicious code, we just take the one at the front.Dont forget to put "()" cause the question ask for "function". `Answer : eval()`

```
3) Examine the HTML elements within the 'tickets' section. Identify any malicious code that has been injected. What type of malicious element is present, and where is it located within the HTML structure?
```

![image](https://github.com/user-attachments/assets/ae89a9b3-d888-4416-913c-ea4c0a87710d)

> View Tickets.html source code file and see on what html tag was the "malicious code" injected. Answer : `<iframe>`

```
4) Examine the functionality of the 'Download PDF' button in the memorabilia.html file. Identify the sensitive user data that is being collected when this button is clicked. What specific data is being gathered, and how is it being transmitted to a malicious server?
```

![image](https://github.com/user-attachments/assets/a5e1edae-7c1d-405a-91ec-6285847b9e4f)

> View the memoribillia.html file source code, and look at the the "Download PDF" function. There is a few data that being trasmitted inside the "JSON.stringify" function. Answer : `userAgent,cookies,localStorage`

```
5) In the context of the MITRE ATT&CK Matrix, under which tactic is 'Drive-by Compromise' classified?
```

> Search for "Drive-by compromise" mitre attack on the internet and you got the answer. Answer : `T1189`


### 2 Mission : L'Énigme du Casino Royale

![L'Énigme du Casino Royale](https://github.com/user-attachments/assets/ad0b7c49-10cf-4f75-b671-00284693b99b)

#### Briefing 

```
Welcome to "L'Énigme du Casino Royale," a high-stakes cyber threat investigation set in the glittering world of Monaco's premier casino. As an elite cybersecurity analyst, you've been called in to unravel a sophisticated cyber heist that has rocked the foundations of the gambling world.

Your mission is to piece together the puzzle of a multi-faceted attack that combines advanced persistent threats, social engineering, cryptographic breaches, and insider threats. The Monaco Grand Casino has fallen victim to a heist of unprecedented scale and complexity, leaving traditional investigative methods baffled.

Your task is to analyze a network of ten highly skilled operatives, each bringing unique expertise to this audacious crime. From APT specialists to dark web operators, from social engineers to AI experts, you must understand their roles, backstories, and potential contributions to the heist.

As you navigate through this challenge, you'll need to:

Scrutinize detailed profiles of each suspect
Analyze a comprehensive intelligence report
Identify potential biases and inconsistencies in the available information
Connect the dots between seemingly unrelated pieces of evidence
Uncover the true nature and extent of this groundbreaking cyber attack
Your findings could reshape our understanding of modern cyber threats and potentially unveil a new era of hybrid attacks that blur the lines between digital and physical security breaches.

Are you ready to dive into the depths of this digital mystery and bring the perpetrators to justice? The clock is ticking, and the stakes have never been higher. Welcome to "L'Énigme du Casino Royale."
```

#### Answer Instruction 

```
Lauch the challenge Environment & Answer the questions 
```

#### Solution 

```
1) Who is the most likely individual responsible for the casino heist? 
```

> Based on the hint, it said "spotted in monaco". So reading every suspect details we can find who was spotted in monaco. Answer : `Eva Schmidt`

```
2) What key bias is present in the analyst report that could mislead the investigation?
```
> The key bias present in the analyst report was "Confirmation bias", Confirmation bias is people's tendency to process information by looking for, or interpreting, information that is consistent with their existing beliefs. Answer : `Confirmation bias`.

```
3) Whose alibi conflicts with the findings in the report?
```

> Read the analyst report, read the "key finding" section. On the key finding, all the report is based on different role, read it and look at each of the suspect recent activity, the one who was the key finding and the recent activity not tally is our answer. Mei Lin, who was a Advanced Persistent Threat (APT) Specialist and former member of the APT41 ,her recent activity was "attended a cybersecurity conference in Singapore"  while on the key finding no 2 said that "deployed malware shares similarities with tools used by APT41". Got a conflict there so her name was our answer. Answer : `Mei Lin`

```
4) Which suspect's expertise aligns with the AI technologies used in the heist?
```

> Look at each suspect roles, and the who was specialist in AI is our answer. As you can see in the report only one suspect is Ai specialist, Amara Okafor. She is our answer. Answer : `Amara Okafor`.

```
5) Who might be orchestrating a false flag operation to misdirect investigators?
```

> The hint said that "Disinformation expert, possibly retired.", and the chall also mentioned "orchestrating a false flag operation", Sophia volkov who expetise in disinformation campaigns and on recent activies said that she possibly retired, therefore she should be our answer. Answer : `Sophia Volkov`

### 3 Mission : Opération Côte d'Azur

![Opération Côte d'Azur](https://github.com/user-attachments/assets/18015d59-b008-43e3-a28f-4c8e3044d7a7)

#### Briefing 

```
Welcome to "Opération Côte d'Azur," an urgent cyber mission set against the glittering backdrop of the French Riviera. LeRoux, our elite operative from Hacktoria, has successfully infiltrated the current operating site of a clandestine network of sophisticated cybercriminals. In a daring move, he's managed to extract crucial information before communications were cut. You have two paths to solve the non geolocation challenges:

- Employ your OSINT skills to uncover the answers hidden in the vast ocean of open-source information.
- Complete the Diamond Model by piecing together the fragments of information LeRoux has provided.

Each challenge represents a crucial piece of the puzzle. Your expertise in cyber analysis and your ability to connect the dots will be put to the test. The fate of this operation rests in your hands. Are you ready to dive into the depths of this high-stakes cyber intrigue?
```

#### Answer Instruction 

```
Lauch the challenge Environment & Answer the questions, there are 2 ways to solve the challenge (refer briefing). Here i solve using OSINT skills.
```

#### Solution 

```
1) What is the codename of the Advanced Persistent Threat group associated with Russia's GRU military intelligence agency?
```

> Do a little bit on research regarding the APT group that associated with Russian GRU and found the answer which is one on the group in APT28. Answer : `Fancy Bear`

```
2) What is the MITRE ATT&CK Group ID assigned to this APT group?
```

> Find the Group ID of the `Fancy Bear` team on Mitre Attack website and we will get the answer. Answer : `G0007`

```
3) Name the popular post-exploitation tool commonly used for credential harvesting by threat actors.
```

> Do the research on the internet and found the answer which is `Mimikatz`. Answer : `Mimikatz`.

```
4) Which commercial penetration testing software is frequently misused by threat actors for Command and Control (C2) activities?
```

> There are so many commercial penetration testing software missued by APT for C2 acitivtes, but base on the hint, it was name after the metal and action, so do a little bit of research and found the answer. Answer : `Cobalt Strike`

```
5) What is the name of the location where LeRoux will be for the rendezvous point?
```

![image](https://github.com/user-attachments/assets/aba51ad7-b297-4ac5-9976-1b04057251ec)

> First, i reverse search the image to get a closer possible location of the picture, after spending a few time looking for it, when i was street viewing on the place where the environment is quite simillar like in this image (refer image below), i can see that the mountain (round in red) is kindly look a like the mountain in the picture.

![Screenshot 2024-10-01 225907](https://github.com/user-attachments/assets/cd9b2558-ded7-408e-a83d-a38d0c30c91e)

> From there, i know that, i'm in the right place, so just street viewing the place to find the exact match place in the picture, and after a couple of minute i found it. The answer is the hotel name. Answer : `L´Escale du Ciel`

![image](https://github.com/user-attachments/assets/afcd5d8c-b0e6-442d-860d-3d9a2f144116)

### 4 Mission : Le Trésor de Monte-Carlo

![Le Trésor de Monte-Carlo](https://github.com/user-attachments/assets/11a07cbc-f786-4dd8-96e4-135d9b6edf89)

#### Briefing 

```
Welcome to "Le Trésor de Monte-Carlo," an intricate intelligencemission set in the opulent principality of Monaco. A high-stakes theft has rocked the city's elite: a rare, multi-million dollar hypercar has vanished from one of the most secure private garages in Monte Carlo.

Your objective is to analyze a detailed intelligence report on this sophisticated heist. The perpetrators employed a lethal combination of advanced cyber techniques and physical intrusion methods. Your task is to meticulously dissect each step of their operation, from the initial network infiltration to the final moment when they drove away with the prized vehicle.

This challenge will put your skills to the test in:

Critical thinking and problem-solving
Decoding and interpreting code snippets
Understanding advanced security system bypasses
Following a chain of events
Understanding mission objectives and goals
You'll need to uncover how the attackers managed to circumvent state-of-the-art security measures and steal a vehicle that was believed to be impenetrable. Your findings could reshape the future of high-end automotive security and cyber-physical system protection.

Are you prepared to unravel this intricate digital puzzle and shed light on one of the most daring heists in Monaco's history? The clock is ticking, and the world of luxury and cybersecurity hangs in the balance.
```

#### Answer Instruction 

```
Lauch the challenge Environment & Answer the questions
```

#### Solution 

```
1) What is the name of the function that sets up malware persistence by modifying the registry?
```

![image](https://github.com/user-attachments/assets/3697af3d-d6fa-4fa0-bb54-84e1ec483b6f)

> View the Operation Analysis and view the "Fig. 2: Malware establishing persistence", inside the code , you can see the function for registry persistence. Follow the answer example, we no need to include "()". Answer : `setup_persistence`

```
2) In the exfiltrate_data function, what is the URL to which the data is sent?
```

![image](https://github.com/user-attachments/assets/9a6e42dd-fb95-4a7a-916c-7d86a24d8f32)

> insid the operation analysis, view the "Fig. 4: C2 communication flow" sections, and you can see the "exfiltrate_data" function and which URL the data is sent. Answer : `https://legitimate-site.com/api`

```
3) What function amplifies the key signal for increased transmit range?
```

![image](https://github.com/user-attachments/assets/bd964f46-561d-4d2c-adaf-ef0122bc8256)

> The answer can be found in the "Fig. 6: Vehicle theft execution". Inside the answer you can there was function to increase transmit range. Answer : `amplify_key_signal`

```
4) What registry value name is used to set the persistence in the setup_persistence function?
```

![image](https://github.com/user-attachments/assets/2d1c9d04-1ef9-4f7e-85d9-7e8b18ffe668)

>  View the Operation Analysis and view the "Fig. 2: Malware establishing persistence", you can see the registry value for persistence. Dont forget to include the bookmark. Answer : `"ShadowService"`

```
5) What file path does the extract_biometrics function read to obtain fingerprint data?
```

![image](https://github.com/user-attachments/assets/8b5bbebd-7bdc-43ba-9872-163f506381d2)

> Read the "Fig. 3: Biometric data being exfiltrated" sections, and view the function "let fingerprint" function to find the answer. Answer : `"/sys/biometrics/fingerprints.dat"`


### 5 Mission : La Dernière Danse à l'Hôtel de Paris

![La Dernière Danse à l'Hôtel de Paris (2)](https://github.com/user-attachments/assets/a13aa046-5512-40a9-aed1-47ac50a98cad)

#### Briefing 

```
Welcome to "La Dernière Danse à l'Hôtel de Paris". This challenge plunges you into a simulated DarkNet marketplace, a digital underworld teeming with illicit activities and shadowy figures.

As an elite cyber analyst, your mission is to navigate this treacherous digital bazaar, uncovering crucial information about the vendors operating within. You'll need to employ a combination of analytical rigor and critical thinking to piece together the puzzle.

Your task involves:
Analyzing vendor profiles
Conduct OSINT research on the vendors
Identifying patterns in seemingly random data
Connecting the dots between various marketplace activities

The stakes are higher than ever. Your findings could be the key to dismantling a global cybercrime syndicate. Can you sift through the digital noise, separate fact from fiction, and uncover the truth hidden in the depths of this virtual underworld?
```

#### Answer Instruction 

```
Lauch the challenge Environment & Answer the questions
```

#### Solution 

```
1) What famous vulnerability was exposed by the Shadow Brokers hacking group's leak?
```

> Doing research on a famous APT team called Shadow Brokers. Fortunately, found a wikipedia page for the team and state a few vulnerability that was exposed by the team, one of it the EternalBlue Exploit also known as "MS17-010". Answer : `MS17-010`.

```
2) A vendor compromised their operational security by using non-Monero cryptocurrency for transactions. What blockchain address did this transaction come from?
```

![image](https://github.com/user-attachments/assets/694b0ca3-9c36-4038-8ad6-034c958daa6f)

> View and read the profile for all the vendor. On the description for one of the vendor which is "Pixel" team, you can see a telegram bot link that got attached.

![image](https://github.com/user-attachments/assets/75e1e8a1-12cc-4710-810a-adbd716555e2)

> Visit the bot link, and on the bot bio, it gave us a blockchain address.

![image](https://github.com/user-attachments/assets/fc016d8f-06b0-484b-a699-a7aec403ae7a)

> Go to blockchain explorer and look up for the address, view the transaction hash that was make into that address and vew the wallet number. Answer : `3QeRZ6htGw8xS7986FWGwPeZ1uYbFpJQY2`

```
3) One of the vendors has an old social media account they forgot to delete on the internet. What's their first and last name?
```

> This question is the most pain in the ass among others, to solve this, the intended way is too create a posibble username wordlist using the vendor name and use username reverse tool to find the social media. But on my side, i need the author to help me to explain the format of the usernmame, he said that "username of a vendor 2 words and can make unique combinations with two words an underscore _ a dash -". So from all of the vendor name, only a couple of them have a two words such as Royal Flush, Nexus Hustler, Grand Mastermand, Shadow Brokers. So basically i just try to find all of the vendor name social media but got nothin. A little hint from the author, give me a hint that from one of the vendor that i try to lookup i the truth one, just need to go deeper. After trying to use tools and go deeper to everyone account found.

![image](https://github.com/user-attachments/assets/b48fdac3-1406-4140-bb06-b44709311a55)

> I found this instagram account, as you can see in the bio, there is a name. that is the answer ( i found this account before using tools and create wordlist, just that i dont view the profile, cause i think, the profile will uisng an AI image or something more related to the challenge, so this chall teach me to always careull LOL). Answer : `Carlos Souza`

```
4) The Phantom message is decrypted. What is the target of the conversation between Phantom and the Anonymous user?
```

![image](https://github.com/user-attachments/assets/27915c4e-b1d0-4d8e-9927-e45f200feb77)

> Open the "Message" tab and read the conversation between unknown and Phantom. And view the hint for this question, it said "A famous location in Monaco." and the example of answer show that the answer have 4 words. So here i do some search about the famous location in monaco.

![image](https://github.com/user-attachments/assets/b1e92e04-b8ec-40b0-8a0e-d22cbe9a5849)

> The famous district in Monaco was Monte-Carlo, so i want to make the search scope a bit smaller. I try to find the famous location in Monte-Carlo. After a few try, the thing i got is only the dead end. Take a break and then continue. And then i remember that one of the famous location inside the Monte Carlo district was a casino. So i tried to search for famous casino in Monaco.

![image](https://github.com/user-attachments/assets/48d10f33-f89b-4652-8ef6-fbd99caa91c5)

> Fortunately my guess was right, after trying to submit possible casino as the answer, i found the real answer. Answer : `Casino Cafe De Paris`.


```
5) Spectre and an Anonymous user are plotting something in the decrypted communications. What item do they need to complete their mission?
```

![image](https://github.com/user-attachments/assets/7828816f-ba34-437d-b29e-edb24bae9860)

> Read the messages between unknown and Spectre, they mentioned about "Blind Oracle". What on earh is Blind oracle, do a research if there is any related things that some people called as "Blind oracle" in cybersecurity, but ain't nothin usefull. Later than i read the conversation back, Specter mentioned that they need the "Blind Oracle" from the "BAZAAR", "Bazaar" could be also known as market.

![image](https://github.com/user-attachments/assets/d19f4d9e-93b9-4ae2-add5-3e66e976e845)

> In the site, there is a tab called "Marketplace", so i view the item sell inside the marketplace and only this one item caught my eyes. Because the name contain the word Blind too. So i try submit it as the answer and yah. I got it. So the oracle is represnting the camera shape i guess :D. Answer : `Surveillance Blindspots`







