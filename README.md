# Activity: Analyze network attacks

> [!NOTE]
> This exercise is a component of the [Google Cybersecurity Professional Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity) program. It's designed as a simulated scenario to solidify my understanding of Network Analysis.
  
## Activity Overview
In this activity, you will consider a scenario involving a customer of the company that you work for who experiences a security issue when accessing the company’s website. You will  identify the likely cause of the service interruption. Then, you will explain how the attack occurred and the negative impact it had on the website. 

## Scenario
You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

# Cybersecurity Incident Report
| Section 1: Identify the type of attack that may have caused this network interruption |
|---------------------------------------------------------------------------------------|
| One potential explanation for the website's connection timeout error message is that there’s been a DoS SYN flood attack. The logs show that an unfamiliar IP (203.0.113.0) is sending too many SYN requests, which makes the web server collapse and stop responding.|

| Section 2: Explain how the attack is causing the website to malfunction |
|-------------------------------------------------------------------------|
| When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. These 3 steps are:
:one: **SYN** (synchronize)  packet being the initial request from a client trying to connect to the web page hosted on the web server. 
:two: **SYN/ACK** (synchronize acknowledge) packet is what the web server responds to the client’s request, agreeing to the connection. 
:three: **ACK** (acknowledge) packet is the client’s machine acknowledging the permission to connect. This is the final step of the handshake for a successful TCP connection.
When a malicious actor sends a large number of SYN packets all at once, the web server has a hard time trying to keep up with the abnormal number of incoming SYN requests, leading to error messages for the legitimate employee visitors, indicating that they cannot establish or maintain a connection to the web server. The logs indicate that the attacker initiated connections but continued sending SYN packets, aggravating the issue. After log item number 125, the server became completely overloaded and stopped responding to any requests, leaving only the attack-related entries in the logs.
The potential consequences of this attack are service disruption, financial loss, reputation damage and investment on security costs. Ways to secure the network to prevent an attack like this in the future are implementing regular security audits and penetration testing, web application firewalls (WAFs), intrusion detection/protection systems (IDS/IPS), and L3/L4 firewalls. |
