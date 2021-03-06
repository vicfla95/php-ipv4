# IPv4 classes for PHP5

### Purpose

Identify, convert, and enumerate IPv4 IP addresses and subnets

### Examples

    $ip = Ipv4_Address::fromString('10.2.1.1');
    $sn = Ipv4_Subnet::fromString('10.2.0.0/16');

    // Test if IP is in subnet
    $sn->contains($ip)          // true
    $sn->contains('10.3.1.23')  // false
    Ipv4_Subnet::ContainsAddress($sn,$ip)
    Ipv4_Subnet::ContainsAddress('192.168.1.0/27','192.168.1.246')

    // Test if two IPs are on the same network
    $netmask = '255.255.255.0';
    Ipv4_Subnet::ContainsAddress(new Ipv4_Subnet($ip1,$netmask),$ip2)

    // Can be written in numerous ways...
    Ipv4_Subnet::ContainsAddress("{$ip1}/24",$ip2)
    Ipv4_Subnet::fromString("{$ip1}/24")->contains($ip2)

    // Subnet information
    $sn->getNetwork()
    $sn->getNetmask()
    $sn->getNetmaskCidr()
    $sn->getFirstHostAddr()
    $sn->getLastHostAddr()
    $sn->getBroadcastAddr()

    // Enumerate subnet addresses
    $ips = $sn->getIterator();
    foreach($ips as $addr) ...

    // Count number of usable IPs on subnet (implements Countable)
    $sn->getTotalHosts()
    $sn->count()
    count($sn)
