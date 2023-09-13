# Codepath Unit 9 Honeypot Project

   _As an aspiring computer science professional, I pursued this project to gain practical insights into cybersecurity and honeypot deployment. My academic background includes a Bachelor of Science in Computer Science from Temple University, where I acquired a strong foundation in programming languages and problem-solving skills. I also completed the Codepath Intermediate Cybersecurity Course, equipping me with the knowledge necessary for offensive security techniques._

### Objective:
Create a honeynet using MHN-Admin. Present your findings as if you were requested to give a brief report on the current state of Internet security. Assume that your audience is a current employer who is questioning why the company should allocate any more resources to the IT security team.

### Background:
A honeypot serves as a deceptive application, server, or networked asset intentionally designed to expose vulnerabilities. When an attacker attempts to exploit these vulnerabilities, it provides insights into the attacker's methods, tools, and potentially their identity. Security researchers frequently employ honeypots to gain a deeper understanding of the challenges faced by developers and system administrators. They collect various data points, including:

- Details about the origins of malicious network traffic, such as IP addresses and geographic locations.
- Information that aids in fortifying resources against email spammers.
- Samples of malware encountered during the honeypot's operation.
- Insights into database vulnerabilities, including SQL injection (SQLI) techniques.

Honeypots play a crucial role in enhancing security measures by shedding light on potential threats and assisting in proactive defense strategies.



## MHN-Admin Deployment

### Description

In order to complete this assignment, I had to access a cloud hosting provider that provisions VMs. I've decided to go with Google Cloud Platform’s Free Tier.
I utilized GCP and followed a step-by-step guide from Codepath for its deployment. To ensure that I don't go over the free time limit allowed by Google, I purchased a virtual credit card from privacy.com with a limit set to $1. I executed all the commands on a macOS operating system.

## Walkthrough

**Created mhn-admin VM:**

<img width="774" alt="Screen Shot 2022-11-03 at 9 37 12 PM" src="https://user-images.githubusercontent.com/79866644/199878896-23f38fe2-9df3-4869-925d-b85c044c3af4.png">

**Established SSH access to the VM using `gcloud compute ssh mhn-admin`:**

<img width="770" alt="Screen Shot 2022-11-03 at 9 38 25 PM" src="https://user-images.githubusercontent.com/79866644/199878947-dfe5e906-db71-4910-b8c6-e37aa75754bc.png">

**Completed installation of MHN Admin Application:**

<img width="744" alt="Screen Shot 2022-11-03 at 9 51 10 PM" src="https://user-images.githubusercontent.com/79866644/199879442-9bb0f4a2-98be-45e3-8ca9-232878c0eee5.png">

<img src="mhn-admin.gif">

## Dionaea Honeypot Deployment

**Description:** Dionaea is a malware-capturing honeypot that aims to trap malware exploiting vulnerabilities exposed by services offered over a network, and ultimately obtain a copy of the malware. In other words, Dionaea will help us catch any payload/malware and other attacks performed on our honeypot VM.

**Created firewall rules for our honeypot VM**

<img width="563" alt="Screen Shot 2022-11-03 at 9 52 34 PM" src="https://user-images.githubusercontent.com/79866644/199880359-bd2359fa-8627-494d-9773-b99c7b653da7.png">

**Then, I proceeded with creating the honeypot VM**

<img width="559" alt="Screen Shot 2022-11-03 at 9 53 10 PM" src="https://user-images.githubusercontent.com/79866644/199880402-cacfdd40-9457-4348-8dfc-1053b10e4d18.png">

**Afterward I execute `gcloud compute ssh honeypot-1` command to establish SSH access to the honeypot VM**

<img width="575" alt="Screen Shot 2022-11-03 at 9 53 42 PM" src="https://user-images.githubusercontent.com/79866644/199880738-43d87dd0-551f-46cd-ab30-7d75b8ffa693.png">

Then I'm going to Google Cloud dashboard > VMs > copy mhn VM IP address and go to that address

<img width="818" alt="Screen Shot 2022-11-03 at 10 14 20 PM" src="https://user-images.githubusercontent.com/79866644/199881211-b9723187-e62a-4950-ae8d-69822fbdf926.png">
<img width="1104" alt="Screen Shot 2022-11-03 at 10 14 22 PM" src="https://user-images.githubusercontent.com/79866644/199881323-c8befa84-dd3b-440b-bccd-5d4123645cf2.png">


I'm clicking on the Deploy tab at the top of the web page to get the deploy command for the Dionaea

<img width="1095" alt="Screen Shot 2022-11-03 at 10 15 38 PM" src="https://user-images.githubusercontent.com/79866644/199881113-bc995f9f-ab05-4856-8b55-bb614786041a.png">

Then I go to the honeypot VM and use the command to install Dionaea

_picture below shows the finished process of installing Dionaea_

<img width="566" alt="Screen Shot 2022-11-03 at 10 22 40 PM" src="https://user-images.githubusercontent.com/79866644/199881540-b1af8179-5414-48a2-ba64-c8c1b71bb40d.png">

Then I go back to the MHN server web page to see if Dionaea was installed on Honeypot VM

<img width="1104" alt="Screen Shot 2022-11-03 at 10 23 04 PM" src="https://user-images.githubusercontent.com/79866644/199881776-d734ebe3-a03c-4679-b97c-1a8a4ad8d5bf.png">

Tried to use `nmap 35.227.41.129` command on Kali Linux VM to check for open ports

![Screenshot 2022-11-03 224949](https://user-images.githubusercontent.com/79866644/199881895-c79be92a-907d-4fb4-9556-d159edbd3d8e.png)

<img src="dionaea-honeypot.gif">

**Summary:** Successfully deployed malware-capturing honeypot Dionaea on Kali Linux VM

### Challenges:
I didn't have a backup for the VM. I ended up deleting everything before exporting session.json but didn't have deletion protection on the VM that I created in Google Cloud which caused a loss of the data that I was unable to restore.
If I did implement database backup, the RDBMS that I'm going to use will be MongoDB where **_MHN-Admin will utilize it to accumulate attacks performed on the honeypot VM and will save the data in the session.json file._**

### Conclusion:

This project underscored the importance of proactive security measures in today's digital landscape. Honeypots like Dionaea play a vital role in identifying and analyzing potential threats, helping organizations bolster their security defenses. As an aspiring cybersecurity professional, I am committed to continued learning and contributing to enhancing Internet security.
