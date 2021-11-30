+++
categories = ["hacking"]
date = "2021-11-29T18:50:51+09:00"
draft = false
slug = "nmap-basics"
tags = ["nmap"]
title = "Nmap Basics"
+++

<h3>How to use Nmap, Just the Basics</h3>

Why? Because basics are the foundation of everything. Nmap (which stands for ‘network mapper’) is a  very prominent tool in the hacker's bag of tricks. While it is not the only tool of its kind, it is certainly the most widely known. I wont be going into the low level details on the inner workings of Nmap, rather I am going to go over the absolute basics that I find necessary in order to make Nmap do what Nmap does. If you want a full detailed explanation of all things Nmap has to offer, feel free to check it out at Nmap.org.

<h3>What is Nmap?</h3>

Nmap stands for "network mapper." It is a port scanner used to map out open ports, and discover software running on those ports.

<h3>How do I start using Nmap?</h3>

I am going to show how to use it on Kali Linux, but the instructions will be nearly identical if you are running any debian based linux distribution. I recommend having a virtual machine open and ready to scan.

Now on your Kali machine, open up a console and type in [nmap <x.x.x.x>] (replace <x.x.x.x> with the IP address of the machine you want to scan). 

Hit Enter and wait a minute. Nmap should now be scanning the target associated with the IP address you put into the command. Congratulations, you just did a basic Nmap scan!

How to make Nmap scan differently?

Now that the basic scan is over, let’s try adding some tags to our nmap command to make it scan a little differently.
<pre>
<li><b>Scan All Ports (1 – 65535)</b>
We can make Nmap scan all ports on a machine by using the [-p-] tag.
Like this [ nmap -p- <x.x.x.x> ]</li>

<li><b>Scan Only Certain Ports</b>
Scanning all ports takes quite some time. We can greatly reduce the amount of time it takes to do a scan by using the [-p <port>] tag. For example, maybe we only want to scan ports 80 and 443 for web servers on our target machine. 
We can do that like this [ nmap -p 80,443 <x.x.x.x> ]</li>

<li><b>Scan Faster</b>
We can speed up or slow down the execution of our scans by using the [T<1-5>] tag. By specifying a speed of T1, T2, T3, T4, or T5, we can slow down or speed up the execution of our Nmap scans. T1 being the slowest, and T5 the fastest. Typically a T4 will do fine most of the time. Let’s say, for example, I want to scan all 65,535 ports of a target machine, and I want to scan them fast.
We can do that like this [ nmap -T4 -p- <x.x.x.x> ]</li>

<li><b>Detect OS and Software</b>
A very important part of scanning is not only finding out what ports are open, but what the target is using that causes the ports to open. Using the [-A] tag will allow Nmap to make fairly accurate predictions on the software the target machine is running. Nmap will also attempt to predict what operating system the target is using. 
Using the command [ nmap -A -p 80,443 <x.x.x.x> ] will have Nmap scan ports 80 and 443, figure out what web server is being run through them (like Apache or ISS), and attempt to predict what operating system the target is using. Usually Nmap will have version numbers next to the software it thinks the target is running, this is important when we start enumerating the target later on.</li>

<li><b>Scan Only for Top Ports</b>
The tag [--top-ports <number>] will tall Nmap to only scan the top <number> most popular ports. For example, maybe you only want to scan the top 100 ports.
We can do that like this [nmap –top-ports 100 <x.x.x.x>]</li>

<li><b>Scan a range of IP addresses using CIDR notation</b>
If you want to scan a subnet of IP addresses you can since Nmap supports CIDR notation.
We can scan a subnet of /24 like this [ nmap <x.x.x./24> ]</li>
</pre>

