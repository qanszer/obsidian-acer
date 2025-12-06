
2025-12-04  18:43

Tags: [[Networking]] [[School]]

---

# Subnetting Computations


## Quiz on Finals

### Bits:
1
2
4

8
16
32
64
128

### GIVEN
192.100.168.0
Subnets: 6
Hosts: 14

1+2+4 = 7
7 > 6 (given subnet)

#### Subnet mask: 
255.255.255.248 or
255.255.255.0/29


	An octet IP has 8 bits (.11111111)
	As seen above, we borrowed 3 bits (1, 2, and 4)
	So borrowed bits = 3
	And remaining bits = 5


#### Formula for computing usable subnets: 
`2^borrowed-bits  -  2`

2^3 = 8 total subnets
8 - 2 = 6 usable subnets


#### Formula for computing usable hosts:
``2^remaining-bits

2^5 = 32 total hosts(ip address) for each subnet
32 - 2 = 30 usable hosts for the devices of each subnet


### Subnetting Table
#### Subnet 0 - Network Admin
network address: 192.100.168.0
hosts: .1 - .30
broadcast address: .31

#### Subnet 1
network address: .32
hosts: .33 - .62
broadcast address: .63
usable: no

#### Subnet 2
network address: .64
hosts: .65 - .94
broadcast address: .95
usable: yes

#### Subnet 3
network address: .96
hosts: .97 - .126
broadcast address: .127
usable: yes

#### Subnet 4
network address: .128
hosts: .129 - .158
broadcast address: .159
usable: yes

#### Subnet 5
network address: .160
hosts: .161 - .190
broadcast address: .191
usable: yes

#### Subnet 6
network address: .192
hosts: .193 - .222
broadcast address: .223
usable: yes

#### Subnet 7 - Also for admin
network address: .224
hosts: .225 - .254
broadcast address: .255
usable: no



## Cafe Project Subnet v1
### Bits:
1
2

4
8
16
32
64
128

### Given
Subnets - 2
Hosts - 18

1+2 = 3
3 > 2

borrowed bits = 2
remaining bits = 6

2^2 = 4 total subnets
4 - 2 = 2 usable subnets

2^6 = 64 total hosts
64 - 2 = 62 usable hosts

### Subnet mask
255.255.255.0/30 or
255.255.255.252

### Subnetting Table

#### Subnet 0
network address: 192.168.1.0
usable hosts: .1 - .62
broadcast address: .63
usability: no

#### Subnet 1
network address: 192.168.1.64
usable hosts: .65 - .126
broadcast address: .127
usability: yes

#### Subnet 2
network address: 192.168.1.128
usable hosts: .129 - .190
broadcast address: .191
usability: yes

#### Subnet 3
network address: 192.168.1.192
usable hosts: .193 - .254
broadcast address: .255
usability: no







---

## References