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
- 