<p align="center">
<img width="750" alt="image" src="https://github.com/user-attachments/assets/4510ff06-f7ca-4197-9022-f72a31e1615b" />
</p>

<h1>Configuring DNS</h1>
In this repository, I configured DNS in a Windows Server environment by creating A and CNAME records, testing name resolution from client machines, and troubleshooting DNS caching issues using command-line tools. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Active Directory: DC-1 and Client-1

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)


<h2>Actions and Observations</h2>

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/ea4a691f-fa67-40ae-b9f3-251d6b923141" />

</p>
<p>
First, I logged into Client-1 and attempt to ping "mainframe" Right now, mainframe is just a random word that doesn't have any meaning to it.
When your computer tries to connect to any host name on the network, it will first check the DNS cache because it is the fastest.
If DNS cache isn't found, then it will then check local host file which is a bit slower.
And if nothing is found on there, it will then check the DNS server which is the slowest.
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/84c0483e-95d3-4fb4-9e30-6968ddc6c555" />

</p>
<p>
Then, on DC-1, I created a DNS A-record for “mainframe” and have it point to DC-1’s Private IP address. </p>
To do this I open DNS Manager via Administrative Tools,
navigate to my domain’s forward lookup zone (e.g., mydomain.com),
Then create a new A (Host) record: </p>
   - Name: mainframe </p>
   - IP Address: 10.0.0.4 (DC-1's private IP address)
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/8e1c808d-99fb-4275-a212-77198e9e93ae" /> 

</p>
<p>
I then switched to Client-1 and pinged mainframe. Notice how it maches to 10.0.0.4 and a ping is returned. </p>
This is because it checks the DNS cache and it found nothing there. Then it checked local DNS and nothing is there. Finally, it checks the DNS server and it got a reply because it recognized mainframe.
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/70e2a6aa-ae97-4ff3-86c7-38f0ec450826" /> 
</p>
<p>
I went back to DC1 and edited the "mainframe" record to a new IP, like 8.8.8.8 which is Google's public IP address. Now, Mainframe points to 8.8.8.8.
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/07c198cc-2f57-4a2d-9472-bea2ba3416e6" /> 

</p>
<p>
I then went back to Client-1  and pinged Mainframe again. </p>
Notice it may still resolve to the old address but not 8.8.8.8. This is due to the DNS cache. </p> This is because whenever your computer tries to look up a hostname, it always check the DNS cache first and something was in the DNS cache this time. It just happened to be the old address
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/ad384684-7b37-4b4d-b79a-d9c890f29603" />
</p>
<p>
I then checked the local DNS cache and observed. </p> We can still see the mainframe entry. </p> This is because we haven't flushed the dns cache yet.
</p>
<br />

<p>
<img width="400" alt="image" src="https://github.com/user-attachments/assets/f5f60938-6812-400a-ad77-2fc77df8b112" /> <img width="400" alt="image" src="https://github.com/user-attachments/assets/d1d54965-be59-4785-978f-07bb7b26f77d" />

</p>
<p>
I flushed DNS cache by typing `ipconfig / flushdns.` This will then remove the old IP address which was 10.0.0.4. Then, if I type `ping mainframe` again, it comes out with the new IP address because we flushed the DNS cache then it check the DNS server.
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/19b6a9e2-53ef-49b5-b39f-4af14ecceb1a" />
</p>
<p>
I go back onto DC1 and in DNS Manager, created a new CNAME record to map search to google.com: </p>
   - Name: search </p>
   - Alias to: www.google.com </p>
A CNAME record basically maps a name that points to another existing domain name instead of directly to an IP address.
</p>
<br />

<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/66114323-d27b-4138-8363-70e46b612a75" />
</p>
<p>
If I type in `nslookup search` DC-1 will then resolve it to google.com
</p>
<br />

<h2>Lab Project Summary</h2>
Through this DNS lab, I learned how domain names are resolved to IP addresses in a Windows Server Active Directory environment. I practiced creating and testing DNS A records and CNAME records, and used tools like ping and nslookup to troubleshoot name resolution issues. I also learned how local DNS caching works on client machines, including how outdated records can persist until the DNS cache is flushed. Overall, this project helped me understand how DNS functions behind the scenes and how to diagnose and fix common DNS-related connectivity problems.
