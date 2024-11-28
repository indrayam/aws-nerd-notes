# Subnetting Notes

- Subnetting in AWS
  + Divide VPCs into Subnets
  + Subnets are tied 1:1 with AZs
  + For example, if the VPC CIDR is set to 10.2.0.0/16, by definition it has a total of ~65k addresses it can work (read, subnet) with. If we the region has 3 AZs and we decided to create 3 subnets, one for each AZ, we could create the following subnets:
    - 10.2.0.0/24 can have a maximum of 2^8 - 2 = 254 Hosts in the Subnet
      Network IP: 10.2.0.0/24
      Broadcast IP: 10.2.0.255/24
      Usable IP Addresses: 10.2.0.1 to 10.2.0.254
    - 10.2.1.0/24 can have a maximum of 2^8 - 2 = 254 Hosts in the Subnet
      Network IP: 10.2.1.0/24
      Broadcast IP: 10.2.1.255/24
      Usable IP Addresses: 10.2.1.1 to 10.2.1.254
    - 10.2.2.0/28 can have a maximum of 2^4 - 2 = 14 Hosts in the Subnet
      Network IP: 10.2.2.0/28
      Broadcast IP: 10.2.2.15/28
      Usable IP Addresses: 10.2.2.1 to 10.2.2.14
  + Let's take a Three-Tier Architecture which includes:
    - Public LB Tier
    - Private App Tier
    - Private DB Tier
  + Each tier should have Internet Access, High Availability, Fault Tolerance along with Isolation & Security
  + In such a case, you will end up with potentially 9 unique subnets, 3 for each tier and each tier replicated across 3 AZs
  + For example, if the VPC CIDR is set to 10.2.0.0/16, we could create 9 Subnets, using the following 32 subnets (bit of an overkill) by using /21:
    - 10.2.0.0/21 can have a maximum of 2^11 - 2 = 2046 Hosts in the Subnet
      Network IP: 10.2.0.0
      Broadcast IP: 10.2.7.255
      Usable IP Addresses: 10.2.0.1 to 10.2.7.254
    - 10.2.8.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.8.0
      Broadcast IP: 10.2.15.255
      Usable IP Addresses: 10.2.8.1 to 10.2.15.254    
    - 10.2.16.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.16.0
      Broadcast IP: 10.2.23.255
      Usable IP Addresses: 10.2.16.1 to 10.2.23.254
    - 10.2.24.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.24.0
      Broadcast IP: 10.2.31.255
      Usable IP Addresses: 10.2.24.1 to 10.2.31.254
    - ...plus 28 more subnets like this
  + Subnets enable
    - Security via Isolation
    - Because subnets allow us to use multiple AZ, it enables High-Availability
    - Fault Tolerance
    - Performance: In order to achieve the lowest latency and best packet per sec performance, all of the machines would need to be in the same subnet in the same AZ. So, sometimes, you may have to compromise on HA for sake of Performance or vice versa