<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img width="813" height="368" alt="image" src="https://github.com/user-attachments/assets/ea4a691f-fa67-40ae-b9f3-251d6b923141" />

</p>
<p>
ping mainframe
</p>
<br />

<p>
<img width="908" height="694" alt="image" src="https://github.com/user-attachments/assets/84c0483e-95d3-4fb4-9e30-6968ddc6c555" />

</p>
<p>
pointer
</p>
<br />

<p>
<img width="735" height="446" alt="image" src="https://github.com/user-attachments/assets/8e1c808d-99fb-4275-a212-77198e9e93ae" />
</p>
<p>
pinged mainframe on client 1
</p>
<br />

<p>
<img width="976" height="830" alt="image" src="https://github.com/user-attachments/assets/70e2a6aa-ae97-4ff3-86c7-38f0ec450826" /> 
</p>
<p>
point to google's dns. 
</p>
<br />

<p>
<img width="769" height="592" alt="image" src="https://github.com/user-attachments/assets/07c198cc-2f57-4a2d-9472-bea2ba3416e6" /> <img width="1121" height="617" alt="image" src="https://github.com/user-attachments/assets/ad384684-7b37-4b4d-b79a-d9c890f29603" />

</p>
<p>
Local dns cache
</p>
<br />

<p>
<img width="427" height="301" alt="image" src="https://github.com/user-attachments/assets/f5f60938-6812-400a-ad77-2fc77df8b112" /> <img width="567" height="487" alt="image" src="https://github.com/user-attachments/assets/d1d54965-be59-4785-978f-07bb7b26f77d" />

</p>
<p>
flush dns What happened was that the computer checked the local cache and nothing was in there because we flushed the dns, then it checked the local host file and there was no mainframe entry in there. Finally, it reached out to the DNS server over the network and now it's able to get the new ip address when doing ping mainframe.
</p>
<br />

<p>
<img width="994" height="820" alt="image" src="https://github.com/user-attachments/assets/19b6a9e2-53ef-49b5-b39f-4af14ecceb1a" /> <img width="782" height="726" alt="image" src="https://github.com/user-attachments/assets/66114323-d27b-4138-8363-70e46b612a75" />
</p>
<p>
search to google
</p>
<br />

