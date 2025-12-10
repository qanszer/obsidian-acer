
2025-11-22  13:22

Tags: [[Networking]] [[School]]

---

# Diorama measurements


## First Floor
#### Total
length - 27in
width - 12in

#### Walls
length - 20in
height - 5.5in

#### Front Balcony
length - 5in
#### Back Balcony
length - 2in

#### Kitchen Walls
length - 4in
width - 8.7in

#### Counter
length - 8.7in
width - 1.1in

#### Extra Counter
length - 1.2in
width - 1.7in

#### High Table
length - 5.7in
width - 0.8in

#### Long Sofa
length - 7.3in
width - 1in

#### Black Sofa
length - 3.3in
width - 2in

#### Beanie Bag
length - 2.2in
width - 2.2in

#### Refrigerator
length - 2.2in
width - 1.6in

#### Steel Table (Kitchen)
length - 1.6in
width - 1.2in

#### Sink
length - 4in
width - 1.6in

#### Steel Shelf (Kitchen)
length - 5.5in
width - 1in



## Second Floor
#### Walls
length - 20in
height - 5.5in
width - 9.2in

#### Lobby Wall
length - 8.4
height - 5.5

#### Bathroom Wall and Wiring Closet Walls (Left and Bottom)
length - 3.8
height - 5.5

#### Bookshelf
top - 8.5 by 0.7
front/back - 8.5 by 5 (2 pcs)
sides - 0.7 by 5 (2 pcs)

#### Table
top - 2.5 x 1.5

#### Hanging Table
make 2 of these - 9 x 0.7

#### Wiring Closet
top - 2 x 0.6 (2 pcs)
sides - 2 x 0.6 (2 pcs)

#### Toilet Bowl
top - 0.7 x 1.3
side a - 0.6 x 1.5 (2 pcs)
side b - 1.3 x 1.5 (2 pcs)

#### Reception Desk
top - 2.5 x 0.5
side a - 2.5 x 1.9 (2 pcs)
side b - 0.5 x 1.9

#### Stairs Top Floor
7.2 x 2.1

#### IP Camera
0.3 x 0.3 (estimate)

#### NVR and PoE Switch
1.5 x 0.5 (2 pcs)



# Diorama Pictures
base ka sa pics

ref
![[Pasted image 20251124171738.png]]

sink
![[Pasted image 20251124172210.png]]

aircon
![[Pasted image 20251124172737.png]]

mirror
![[Pasted image 20251124173625.png]]

live, laugh, love (or ket ano basta pang picture frame sa wall)
6pcs
![[Pasted image 20251124190829.png]]
![[Pasted image 20251124185945.png]]
![[Pasted image 20251124190248.png]]
![[Pasted image 20251124190407.png]]
![[Pasted image 20251124190621.png]]
![[Pasted image 20251124190643.png]]


fence (same sa pic)
![[Pasted image 20251124184331.png]]


welcome mat
![[Pasted image 20251124174931.png]]

laptop
![[Pasted image 20251124184712.png]]

huawei router
![[Pasted image 20251124185858.png]]

pos
![[Pasted image 20251124175021.png]]

receipt printer
![[Pasted image 20251124175544.png]]




# Diorama Device Specifications


Router:
Huawei EchoLife EG8041V5





# Network Setup

**Router**
GUI --> Network Setup
IP Address: 192.168.1.1
Subnet mask: 255.255.255.0
DHCP: Enabled
Start IP Address: 101
Max users: 100
Static DNS 1: 8.8.8.8

Scroll to bottom --> Save settings

Scroll back to top --> Click "Wireless" --> Click "Guest Network"
Enable 2.4hz and 5hz - 1

Click "Config" on top bar
Setup the SSID and Password for the WiFis


**Switch**
CLI
enable
configure terminal

! Configure management VLAN
interface vlan 1
 ip address 192.168.1.2 255.255.255.0
 no shutdown
exit

! Set default gateway
ip default-gateway 192.168.1.1

! Save configuration
end
write memory




# IP Configurations

![[Pasted image 20251130230621.png]]



# Consultation Takeaways

Consultation Takeaways
1. required daw yung 150 nodes (devices); bale bahala na daw ket di realistic, basta may 150 nodes HAHAHAHA di ko gagawin to, mga 70 lang siguro aken
2. kelangan ayusin yung heading (nakay castaneda yung maayos na heading)
3. lagyan ng header description yung list of figures ("figure no.", "description", "page number")
4. arrange the cabling sa physical view sa packet tracer using bend points (malalagay sa walls yung cables)







---

## References