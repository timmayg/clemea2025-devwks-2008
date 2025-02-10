# Labs & Pods

The lab network we will be working with looks like the diagram below. 

<img src="/images/network-diagram-2025.png" alt="DEVWKS-2008 Network Diagram" width=600>


<ol>

<li> Use this table to determine what Pod you will work with. </li>


| Workstation #  | Pod IP Address  |
| -------------- | ----------- |
| Workstation #1  | pod01-xelab.cisco.com   |
| Workstation #2  | pod02-xelab.cisco.com   |
| Workstation #3  | pod03-xelab.cisco.com   |
| Workstation #4  | pod04-xelab.cisco.com   |
| Workstation #5  | pod05-xelab.cisco.com   |
| Workstation #6  | pod06-xelab.cisco.com   |
| Workstation #7  | pod07-xelab.cisco.com   |
| Workstation #8  | pod08-xelab.cisco.com   |
| Workstation #9  | pod09-xelab.cisco.com   |
| Workstation #10  | pod10-xelab.cisco.com   |
| Workstation #11  | pod11-xelab.cisco.com   |
| Workstation #12  | pod12-xelab.cisco.com   |
| Workstation #13  | pod13-xelab.cisco.com   |
| Workstation #14  | pod14-xelab.cisco.com   |
| Workstation #15  | pod15-xelab.cisco.com   |
| Workstation #16  | pod16-xelab.cisco.com   |
| Workstation #17 (if needed)  | pod17-xelab.cisco.com   |
| Workstation #18 (if needed) | pod018-xelab.cisco.com   | 
| Workstation #19 (if needed) | pod19-xelab.cisco.com   |
| Workstation #20 (if needed) | pod20-xelab.cisco.com   |
| Workstation #21 (if needed) | pod21-xelab.cisco.com   |
| Workstation #22 (if needed) | pod22-xelab.cisco.com   |
| Lab Admin Wkstn #29  | pod29-xelab.cisco.com   |

<li>Open 3 Terminal sessions on your workstation. </li>

<img src="/images/10-01-lab-workstation-web.png" alt="Fresh Lab Workstation" width=600>
<br><br>


<li>SSH to your Pod three (3) times, ADJUST the command below for your Pod ##!</li>

<code> ssh -p 443 -l ciscolive IP-ADDR-TABLE-ABOVE </code>

SSH Username & Password for the Pod & the Cat9300 switches are all the same.
<br>
**User: ciscolive**
<br>
**Password: PROVIDED ON LAB DAY**
<br><br>


<li> The first SSH session will be used for managing Ansible and the files. </li>
We will need to change directories to the CLUS folder for this lab. <br>
<code> cd clemea2025-devwks-2008 </code>
<br><br>

<li> Assure you have the latest code & docs from Github!  </li>
<code> git pull </code>
<br><br>

<li> Refresh the SSH Keys on the Ubuntu host \ Ansible Controller  </li>
<code> ./cat9k-ssh-key.sh </code>
<br><br>


<li> The second SSH session will be a jump box for you to get to the first Cat9300 switch. </li>

SSH Username & Password for the Pod & the Cat9300 switches are all the same.
<br>
**User: ciscolive**
<br>
**Password: PROVIDED ON LAB DAY**
<br>

<code> ssh 10.1.1.5 </code>
<br>

<li> The third SSH session will be a jump box for you to get to the second Cat9300 switch.</li>

<code> ssh 10.1.1.55 </code>



I arrange my SSH sessions like this for best viewing.   Adjust them for your own preferences. 

<img src="/images/10-02-lab-workstation-ssh-web.png" alt="3 SSH Sessiosn on Lab Workstation" width=600>


</ol>


[Click here to move on to the next section. Harden Services](/01-Harden_Services.md)




