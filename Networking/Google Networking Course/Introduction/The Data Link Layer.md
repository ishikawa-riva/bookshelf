# The Data Link Layer

**Protocols used : **
- Ethernet
- WiFi

***Data Unit : Frames***
***Addressing : MAC Address***

## Ethernet
![[Pasted image 20210405035403.png]]

CSMA/CD (Carrier Sense Multiple Access with Collision Domain) Technique is used by Ethernet protocol to resolve the collision domain.
![[Pasted image 20210405035559.png]]

## MAC (Media Access Control) Address

![[Pasted image 20210405035905.png]]
![[Pasted image 20210405035924.png]]

![[Pasted image 20210405040016.png]]

***Total Possible MAC address = 2^48
which is  ***
![[Pasted image 20210405040218.png]]

MAC address is divided into two parts - 3 Octet Each 
![[Pasted image 20210405040344.png]]
**Last 3 Octets can be assigned any way possible manufacturer wants**
![[Pasted image 20210405040518.png]]


![[Pasted image 20210405040636.png]]

## Unicast, Multicast and Broadcast  
![[Pasted image 20210405041038.png]]
![[Pasted image 20210405041059.png]]
![[Pasted image 20210405041221.png]]
![[Pasted image 20210405041321.png]]


## Dissecting Ethernet Frame
![[Pasted image 20210405041431.png]]
**Data Packets at Ethernet Level are known as Ethernet frames**
![[Pasted image 20210405041543.png]]

### Ethernet Frame
![[Pasted image 20210405041736.png]]

**Preamble :** 8bytes (64 bits ) long can be split into two sections. First 7 bytes are alternating 0s and 1s used as buffer between network devices to sync clock and transfer speed.
The **Last Byte** is called **SFD (Start Frame Delimiter) : Signals the receiving device that preamble is over and not the actual data begins.**

**Destination MAC Address :** Hardware address of the recipient. 	