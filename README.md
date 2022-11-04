# Codepath Unit 9
# Honeypot Assignment

**Time spent:** **4** hours spent in total

**Objective:** Create a honeynet using MHN-Admin. Present your findings as if you were requested to give a brief report of the current state of Internet security. Assume that your audience is a current employer who is questioning why the company should allocate anymore resources to the IT security team.

### MHN-Admin Deployment (Required)

**Summary:**

I have used GCP and step-by-step guide from Codepath. For the credit card I have used website privacy.com to get gift card and set limit to $1 not to go over limit. To run all the commands i was using macOS operating system

**Created mhn-admin VM:**

<img width="774" alt="Screen Shot 2022-11-03 at 9 37 12 PM" src="https://user-images.githubusercontent.com/79866644/199878896-23f38fe2-9df3-4869-925d-b85c044c3af4.png">

**Established SSH access to the VM using `gcloud compute ssh mhn-admin`:**

<img width="770" alt="Screen Shot 2022-11-03 at 9 38 25 PM" src="https://user-images.githubusercontent.com/79866644/199878947-dfe5e906-db71-4910-b8c6-e37aa75754bc.png">

**Completed installation of MHN Admin Application:**

<img width="744" alt="Screen Shot 2022-11-03 at 9 51 10 PM" src="https://user-images.githubusercontent.com/79866644/199879442-9bb0f4a2-98be-45e3-8ca9-232878c0eee5.png">

<img src="mhn-admin.gif">

### Dionaea Honeypot Deployment (Required)

**Summary:** Dionaea is a tool that will help us to catch any payload/malware and other attacks performed on our honeypot VM

**Created firewall rules for our honeypot VM**

<img width="563" alt="Screen Shot 2022-11-03 at 9 52 34 PM" src="https://user-images.githubusercontent.com/79866644/199880359-bd2359fa-8627-494d-9773-b99c7b653da7.png">

**Then, I proceed with creating the honeypot VM**

<img width="559" alt="Screen Shot 2022-11-03 at 9 53 10 PM" src="https://user-images.githubusercontent.com/79866644/199880402-cacfdd40-9457-4348-8dfc-1053b10e4d18.png">

**After that I'm using `gcloud compute ssh honeypot-1` command to establish SSH access to the honeypot VM**

<img width="575" alt="Screen Shot 2022-11-03 at 9 53 42 PM" src="https://user-images.githubusercontent.com/79866644/199880738-43d87dd0-551f-46cd-ab30-7d75b8ffa693.png">

Then I'm going to Google Cloud dashboard > VMs > copy mhn VM IP address and go to that address

<img width="818" alt="Screen Shot 2022-11-03 at 10 14 20 PM" src="https://user-images.githubusercontent.com/79866644/199881211-b9723187-e62a-4950-ae8d-69822fbdf926.png">
<img width="1104" alt="Screen Shot 2022-11-03 at 10 14 22 PM" src="https://user-images.githubusercontent.com/79866644/199881323-c8befa84-dd3b-440b-bccd-5d4123645cf2.png">


I'm clicking on Deploy tab at the top of the web page to get the deploy command for the dionaea

<img width="1095" alt="Screen Shot 2022-11-03 at 10 15 38 PM" src="https://user-images.githubusercontent.com/79866644/199881113-bc995f9f-ab05-4856-8b55-bb614786041a.png">

Then I go to the honeypot VM and use the command to install dionaea

_picture below shows finished process of installing dionaea_

<img width="566" alt="Screen Shot 2022-11-03 at 10 22 40 PM" src="https://user-images.githubusercontent.com/79866644/199881540-b1af8179-5414-48a2-ba64-c8c1b71bb40d.png">

Then I go back to the MHN server web page to see if dionaea was installed on honeypot VM

<img width="1104" alt="Screen Shot 2022-11-03 at 10 23 04 PM" src="https://user-images.githubusercontent.com/79866644/199881776-d734ebe3-a03c-4679-b97c-1a8a4ad8d5bf.png">

Tried to use `nmap 35.227.41.129` command on Kali Linux VM to check for open ports

![Screenshot 2022-11-03 224949](https://user-images.githubusercontent.com/79866644/199881895-c79be92a-907d-4fb4-9556-d159edbd3d8e.png)

<img src="dionaea-honeypot.gif">

### Database Backup (Required) 

**Summary:** 
What is the RDBMS that MHN-Admin uses? What information does the exported JSON file record?

**_MHN-Admin uses MongoDB to accumulate attacks performed on the honeypot VM and saves it in session.json file._**


## Challenges

Deleted everything before exporting session.json but didn't have deletion protection on VM that I have created in Google Cloud so wasn't able to restore them.
