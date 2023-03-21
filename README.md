# Lab 4 : CEG 3400 Intro to Cyber Security

## Name: Jason Byrum

### Task 1: A Shell Game 

Answer the following:

* What port does the provided command open?
* What is a Bind Shell and a Reverse Shell (include the links you used in 
  your research!)
  * A blind shell is when an attacker finds an open port on the desired server and then connects their shell to that port
  * A reverse shell is when an attacker has their own port and waits for the user to connect giving the attacker access.
  * https://www.geeksforgeeks.org/difference-between-bind-shell-and-reverse-shell/
  * https://infosecwriteups.com/reverse-shell-vs-bind-shell-d5a1e80b6a6c
* Which type of shell does this command open?
* What/whose permissions does this shell provide?
* Give evidence of your malicious shell running a command:

```
evidence
```

---

### Task 2: Iptables

**Reminder Deliverable:** Your iptables file created with `iptables-save`

Please name your file `task2.rules`

* Would this iptables firewall configuration (`task2.rules`) be considered a whitelist or blacklist?  Explain.
* How did you verify that this worked?  Be verbose!

---

### Task 3: Any Port in a Storm

**Reminder Deliverable:** Your iptables file created with `iptables-save`

Please name your file `task3.rules`

Answer the following:

* Would this iptables firewall configuration (`task3.rules`) be considered a whitelist or blacklist?  Explain.
* Did you lock yourself out?
  * If no: How did you verify that this worked?  
  * If yes: triage, what did you do wrong?  How would you fix it (paste a 
    new attempt at your `task3.rules` right here and try to fix your error)

---

### Extra Credit

Packet.show()

```python

``` 

* What scapy sniff options did you use to JUST show needed packets for this task?

* What are the contents of the packet (what command or response did you capture)?


