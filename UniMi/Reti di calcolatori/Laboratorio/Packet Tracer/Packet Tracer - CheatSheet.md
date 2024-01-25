VLAN
1. `(config)`, eseguo `interface nomeInterfaccian/k.IDVLAN`
2. `(config-subif)`, eseguo `encapsulation dot1Q IDVLAN`
3. Eseguo `ip address indirizzoDaAssegnare subNetMask`

Router
- DHCP da un altra rete: 
	- `(config-subif)`, eseguo `ip helper-address indirizzoDHCPServer`
- RIPv2: 
1. `(config)`, eseguo `router rip`
2. `(config-router)`, eseguo `version 2`
3.  `network baseAddressReteAdiacente`
- OSPF:
1. `(config)`, eseguo `router ospf 1`
2. `(config-router)`, eseguo `area 1 stub`
3.  `network indirizzoBase wildcard area 1`
4. `(config-router)`, eseguo `passive interface nomeInterfaccian/k.IDVLAN`
- NAT
1. `(config-subif)`, eseguo `ip nat inside` (interface dalla parte della subnet)
2. `(config-subif)`, eseguo `ip nat outside` (interface dalla parte di Internet)
3. `(config)`, eseguo `access-list IDACL permit ip any any`
4. `(config)`, eseguo `ip nat inside source list IDACL interface nomeInterfacciaOUT n/k`