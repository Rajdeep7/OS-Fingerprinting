OS-Fingerprinting
=================

Objectives
----------
* Develop an OS fingerprinting tool
* Develop a tool that detects OS fingerprinting

Requirements
------------
* The tools can be developed under the OS of your choice.
* OS fingerprinting can be done using any combination of techniques.
* Use any approach that might help you avoid detection.
* Give a list of potential OS running on your opponent’s machine with a justification.
* IP address of the source of the attack.
* Your detection tool must not mistake legitimate traffic as a fingerprinting attempt.
* Your host must be running a web server on port 80. Extra credit if you identify the web server used by your opponent with a justification.


Attack Tool
-----------
Each Operating System (OS) has unique characteristics in its TCP/IP stack implementation that may serve to identify it on a network. There is a wide range of techniques and methods that helped us get a good estimate of the operating system running on a certain remote machine.

One approach is to use active fingerprinting. That is, special “probe” packets are sent to a certain machine, and based on its response, a certain OS is assumed.

Another approach is to use passive fingerprinting (as used in our project), where legitimate traffic is analyzed and compared for certain key differences in the TCP/IP stack implementation on different versions and types of operating systems.

This tool sends a legitimate HTTP request to the victim’s web server, and based on the response packets, different tests are applied to determine the installed OS and web server.

A total of ten techniques are used to filter out a final choice from 24 OS Versions. These techniques have different weight values based on their accuracy.

Technique | Description | Weight
:---: | :--- | :---:
**TTL** | Test the initial TTL value used by the OS | 0.5
**DF** | Some OSes set the DF bit in the IP header while others don’t | 1
**IP ID** | Different IPIDs may be sent in the IP header | 1
**Window Size** | Differentiate implementations based on default Window Size in TCP | 1
**SYN Packet Size** | May differ between different OSes | 1
**Window Scale Option (TCP)** | Not all OSes implementation use this option | 1
**TCP Options Order** | The order of TCP options may vary from one system to another | 2.5
**ACK Flag** | Differentiate OSes based on the value of the Acknowledgment Number field in the TCP header when the ACK flag is set to zero | 1
**URG flag** | Differentiate OSes based on the value of the Urgent Pointer field in the TCP header when the URG flag is set to zero | 1
**Banner Grabbing** | The HTTP reply from the web server may contain valuable information revealing the web server name and version as well as the OS name in some cases |

You can run the attack tool by issuing the following command:

> ./ofp_tool victim_ip

References
----------
Imad Elhajj, American University of Beirut, <a href="http://staff.aub.edu.lb/~ie05/" target="_new">More</a>.

Project site -- https://rajdeep7.github.io/OS-Fingerprinting/
