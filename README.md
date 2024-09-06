# Elastic-SIEM-Lab

## Lab Description

The goal of this project was to set up a functional SIEM in a home lab to simulate managing events on an endpoint device. Using Elastic on a Kali Linux machine I was able to collect logs to visualize events for easier monitoring and response. I wanted to do this to experiment with virutal machines and SIEM tools. While searching for ways to do this, I found [this article](https://medium.com/@aali23/a-simple-elastic-siem-lab-6765159ee2b2) to help build my foundation.

Tools: VirtualBox, Elastic, Kali Linux

## Set up
The first step was setting up the Elastic deployment on the Kali Linux VM. The Elastic Agent can be installed on Kali  in the terminal by the command given in the deployment. Then it can be verfied with the command **sudo systemctl status elastic-agent.service**

![elastic installed](https://github.com/user-attachments/assets/b2954ed2-5946-41b5-84a1-7f9a40a38d99)

## Creating Events

Once the agent was set up some events were generated to show up in the SIEM. Here I used Nmap.

![nmaplocalhost](https://github.com/user-attachments/assets/d96a16bf-e722-4736-98b8-308d32701bc6)


Back in the elastic SIEM we can navigate to the logs and query them to search for the specifc events created.

![elasticlogs](https://github.com/user-attachments/assets/848be07d-f55b-4ef2-956d-eb73fb818a7e)

Clicking on these events shows more information about them like the specific command used. 

![logdetails](https://github.com/user-attachments/assets/0b71f4c9-5d93-41c3-8c4a-aa4d118f0e93)

## Managing Events

Now that there is data in the logs we can create easier ways to view it.

One way to do that is with the dashboard on elastic. Here is a basic dashboard that visualizes the amount of security events over time.

![dashboard](https://github.com/user-attachments/assets/0c67e8a2-7eed-43bd-8ce0-0f5715719e7c)

Another important feature of a SIEM is alerts that notify for specific security events.

Here I created one to monitor for Nmap scans by using a query just like when searching the logs manually. I also added the extra action to send an email if detected.

![ruledefinition](https://github.com/user-attachments/assets/600916f9-5a5d-4178-afb0-b89aedbb7405)


![email alert](https://github.com/user-attachments/assets/e9ac9d20-1c16-4c16-8192-690e68b1ef83)



Once the the alert rule was put in place and the commmand was ran again, the SIEM showed the alerts and performed the automated action put in place.

![elastic alertpage](https://github.com/user-attachments/assets/dd98cbee-2926-4637-880d-aab7052a4dfd)

Email notification

![nmapalert email](https://github.com/user-attachments/assets/6e9a41f7-9d55-4e0f-9263-4bbf78ea78cf)

