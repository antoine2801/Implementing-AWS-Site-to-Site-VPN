<h1>Implementing AWS Site-to-Site VPN </h1>



<h2>Description</h2>
The AWS Site-to-Site VPN Deployment Guide is a comprehensive open-source project aimed at providing step-by-step instructions, best practices, and resources for setting up a secure and reliable Site-to-Site VPN connection between your on-premises network and Amazon Web Services (AWS) cloud infrastructure. Source : https://learn.cantrill.io/

<h2>Languages and Utilities Used</h2>

- <b>Python</b> 


<h2>Environments Used </h2>

- <b>AWS</b> 

<h2>Project walk-through:</h2>

<p align="center"> 
 <h3> Some definitions <h3/>

- AWS Site-to-Site VPN : A logical connection between a VPC and on-premises network encrypted using IPSec, running over the public Interne
- full HA
- Quick to provision... less than an hour
- Virtual Private Gateway (CGW): It serves as an entry and exit point for network traffic between an organization's on-premises network or data center and the cloud infrastructure.
- Customer Gateway (CGW): It serves as the customer-side endpoint of a VPN connection, providing a secure link between the customer's on-premises network and the cloud infrastructure.
- VPN Connection between the VGW and CGW
  <h3> Infrastructure Design <h3/>
    <img src="https://i.imgur.com/imOtfzO.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
 
 <h3> Creating VPN Enpoints <h3/>
 - Create a customer gateway 
    <img src="https://i.imgur.com/72jOcRk.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

   
- Create a Virtual private gateway and attach it to the VPC
  
 <img src="https://i.imgur.com/OUnRs22.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
 <img src="https://i.imgur.com/FKINbdz.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

- Create VPN Connection
 <img src="https://i.imgur.com/rHgflxp.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/vsFL9qc.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

- Config onprep pfSense
  
  (1) Interface Assignments
  
  <img src="https://i.imgur.com/DymFUN0.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
  <img src="https://i.imgur.com/ZJz5Elm.pngg" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
  
  (2) Create Phase 1 and Phase 2 of 2 IPsec tunnels  (Endpoints)
    <img src="https://i.imgur.com/ehbjw1u.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
    <img src="https://i.imgur.com/lF00UjX.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
     <img src="https://i.imgur.com/Rz0Ptei.pngg" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
     <img src="https://i.imgur.com/OtHN3x8.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
     <img src="https://i.imgur.com/3Ncgzr1.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
  Add Phase 2
<img src="https://i.imgur.com/zD4cBf3.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/i7QkSmd.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/2k6Ro0v.pngg" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/1WpR0mh.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
Manually connect to the IPsec
<img src="https://i.imgur.com/QAf478b.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/87UwjjA.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>


- Routing and Security
Config Route tables : Route propagation on public on-prem aws
<img src="https://i.imgur.com/rGCFmak.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>
<img src="https://i.imgur.com/xbDWg50.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

Config Route tables : Point private on-prem aws to  pfsense firewall
<img src="https://i.imgur.com/9p9RYZV.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

Edit Security Group (Default onprem, onprem Router, Default aws)

(1) Default aws
<img src="https://i.imgur.com/W7ZTdwy.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

(2) Default A4L Router SG
<img src="https://i.imgur.com/hlb44Zo.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>

(3) onprem router 

<img src="https://i.imgur.com/8Pl6LMz.png" height="80%" width="80%" alt="Building and Securing an AWS VPC Steps"/>


<br />
