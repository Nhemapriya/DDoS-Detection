# DDoS ATTACK SIMULATION AND DETECTION USING ENTROPY COMPUTING

### The project involves generating packets and detecting DDoS attack by using entropy computing using Mininet and Pox controller

#### HARDWARE REQUIREMENTS:
-> Hard Disk: 40GB and above
-> RAM: 2GB and above
-> Processor: Intel i3 and above

#### SOFTWARE REQUIREMENTS:
-> Windows operating system
-> Linux virtual box – with python 2 or 3
-> Mininet VM


#### Pre-Requirements:
1.	Install Python
2.	Install mininet along with pox controller
    mininet installation :  http://mininet.org/download/
    pox controller : http://github.com/noxrepo/pox
3.  Creating test environment
    Copy the following files:

    (a)  launchTraffic.py
    (b) launchAttack.py

    to  mininet/custom   and

    (a) detectionUsingEntropy.py
    (b)  l3_edited_detectionEntropy.py

    to  pox/pox/forwarding

#### Detection Using Entropy
1.	Run the pox controller:
    $ cd pox
    $ python ./pox.py forwarding. l3_detectionEntropy.py

2.	Create a mininet topology by entering the following command in another terminal:
    $ sudo mn --switch ovsk --topo tree,depth=2,fanout=8 --controller=remote,ip=127.0.0.1,port=6633

3.	Open xterm for the following hosts:
    mininet>xterm h1 h2 h3 h64

4.	In the xterm window of h1, run the following commands to launch traffic:
    $ cd ../mininet/custom
    $ python traffic.py –s 2 –e 65

5.	Now the pox controller generates a list of values for entropy. 

6.	Repeat step (4) on h1 and parallelly enter the following commands on h2 and h3 xterm windows to launch the attack:
    $ cd ../mininet/custom
    $ python attack.py targetIP

#### File Description

-> POX Detections/detection.py - The code for entropy calculation and DDoS determination
-> POX Detections/l3_learning_edited.py - l3 learning mode of POX controller with hooks into the entropy-based detection code
-> Packet Generation/launchAttack.py - Script which generates attack traffic
-> Packet Generation/launchTraffic.py - Script which generates normal traffic