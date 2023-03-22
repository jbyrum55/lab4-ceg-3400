# Lab 4 : CEG 3400 Intro to Cyber Security

## Name: Jason Byrum

### Task 1: A Shell Game 

Answer the following:

* What port does the provided command open?
  * It opens the port 1234.
* What is a Bind Shell and a Reverse Shell (include the links you used in 
  your research!)
  * A blind shell is when an attacker finds an open port on the desired server and then connects their shell to that port
  * A reverse shell is when an attacker has their own port and waits for the user to connect giving the attacker access.
  * https://www.geeksforgeeks.org/difference-between-bind-shell-and-reverse-shell/
  * https://infosecwriteups.com/reverse-shell-vs-bind-shell-d5a1e80b6a6c
* Which type of shell does this command open?
  * This opens a reverse shell. 
* What/whose permissions does this shell provide?
  * It opens a listening port and allows the attacker to run commands without physically accessing the system.
* Give evidence of your malicious shell running a command:

```
evidence
```

---

### Task 2: Iptables

**Reminder Deliverable:** Your iptables file created with `iptables-save`

Please name your file `task2.rules`

* Would this iptables firewall configuration (`task2.rules`) be considered a whitelist or blacklist?  Explain.
  * This is blacklist because it blocks all of the incoming traffic to the shell. It would be whilelist if it let in certain traffic with specifications.
* How did you verify that this worked?  Be verbose!
  * To verify that this worked I used the command iptables -L -v to see it was accepting no traffic. Then I tried to ping the ip and the port and got no response back, so therefore it does not accept traffic.
---

### Task 3: Any Port in a Storm

**Reminder Deliverable:** Your iptables file created with `iptables-save`

Please name your file `task3.rules`

Answer the following:

* Would this iptables firewall configuration (`task3.rules`) be considered a whitelist or blacklist?  Explain.
  * This is blacklist becasue it blocks out all of the traffic to all of the ports no traffic what so ever.
* Did you lock yourself out?
  * Yes, I got locked out.
  * If no: How did you verify that this worked?  
  * If yes: triage, what did you do wrong?  How would you fix it (paste a 
    new attempt at your `task3.rules` right here and try to fix your error)
      * I believe that I need to take a whitelist approach and block out all of the attacker traffic but add a special request that lets only me in.

---

### Extra Credit

Packet.show()

```

>>> capture = sniff(count=10)
>>> capture
<Sniffed: TCP:8 UDP:0 ICMP:0 Other:2>
>>> capture.show()
0000 Ether / IP / TCP 174.97.116.191:60648 > 10.0.0.20:ssh A
0001 Ether / IP / TCP 174.97.116.191:60648 > 10.0.0.20:ssh A
0002 Ether / IP / TCP 174.97.116.191:60648 > 10.0.0.20:ssh A
0003 Ether / ARP who has 10.0.0.20 says 10.0.0.1 / Padding
0004 Ether / ARP is at 02:93:a8:dd:bd:63 says 10.0.0.20
0005 Ether / IP / TCP 174.97.116.191:60580 > 10.0.0.20:ssh PA / Raw
0006 Ether / IP / TCP 10.0.0.20:ssh > 174.97.116.191:60580 PA / Raw
0007 Ether / IP / TCP 174.97.116.191:60580 > 10.0.0.20:ssh A
0008 Ether / IP / TCP 174.97.116.191:60580 > 10.0.0.20:ssh PA / Raw
0009 Ether / IP / TCP 10.0.0.20:ssh > 174.97.116.191:60580 PA / Raw
>>> capture[9].show()
###[ Ethernet ]###
  dst= 02:55:61:0e:ac:cf
  src= 02:93:a8:dd:bd:63
  type= IPv4
###[ IP ]###
     version= 4
     ihl= 5
     tos= 0x10
     len= 88
     id= 19009
     flags= DF
     frag= 0
     ttl= 64
     proto= tcp
     chksum= 0xc31a
     src= 10.0.0.20
     dst= 174.97.116.191
     \options\
###[ TCP ]###
        sport= ssh
        dport= 60580
        seq= 151933327
        ack= 3582235927
        dataofs= 8
        reserved= 0
        flags= PA
        window= 269
        chksum= 0x2d7f
        urgptr= 0
        options= [('NOP', None), ('NOP', None), ('Timestamp', (12711, 2275513115))]
###[ Raw ]###
           load= '2\xfe\n\xa0\xdf\x11\xc8\x10\x0c\xf4\xff\x93\x9a\xd5\x91\x15I\xb7\xca\x190\xfc\xc8\x0e\r\x16\xff{\xa3\xe2\xbd\xcc\xa9\xcdq\xd3'



``` 

* What scapy sniff options did you use to JUST show needed packets for this task?
  * I used the sniff command to capture 10 packets and then you can tell which ones are being sent to the shell based off of the IPs.
* What are the contents of the packet (what command or response did you capture)?
  * The source was 10.0.0.20 and they were being sent to the IP of 174.97.116.191

