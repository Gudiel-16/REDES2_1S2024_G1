# Manual Técnico Proyecto 1

## Objetivos 
+ Realizar las configuraciones de switches multicapa y capa 2.
+ Implementar los protocolos de capa 3: RIP, OSPF, EIGRP y BGP.
+ Aplicar los conocimientos de redes MAN, LAN y WAN.
+ Aplicar los conocimientos de LACP.
+ Implementar el protocolo VTP.
+ Familiarizarse con el protocolo VRRP(HSRP).
+ Familiarizarse con las configuraciones de DHCP y sus conceptos.

## Definicion del Problema 
Manos Solidarias es una empresa comprometida con la responsabilidad social, se dedica a apoyar a personas en situación de escasez de recursos y sin hogar. Su enfoque se basa en brindar ayuda humanitaria y asistencia social a  quienes más lo necesitan, a través de diversos programas y proyectos que tienen como objetivo mejorar las condiciones de vida de estas personas. Con un equipo altamente capacitado y motivado, Manos Solidarias trabaja incansablemente para brindar apoyo a la comunidad y crear un mundo más
justo y equitativo para todos. Actualmente, deciden emprender su nueva red y lo contratan a usted, experto en redes para que haga todo el análisis correspondiente. Manos Solidarias cuenta con cuatro edificios en diferentes zonas de la ciudad, cada edificio es una red LAN que al mismo tiempo desean que estén conectados para tener comunicación.

## Topologías

### Topologia propuesta
![Topologia del eneunciado!](img/Topo1.png "Topologia propuesta")

### Topologia Completa
![Topologia completa!](img/Topo1.png "Topologia hecha por los estudiantes")

### Configuracion VTP 
#### Modo Servidor(sw0,msw5,msw0)
```
vtp domain g1
vtp mode server
exit
show vtp status
```
#### Modo Cliente(sw1,sw2,sw3,msw6,msw4,msw3,msw1,msw11,msw2,msw7,msw8,msw9,msw10)
```
vtp domain g1
vtp mode client
exit
show vtp status
```

#### Configuracion LACP
MSW0 - MSW12
```
enable
configure terminal
interface range fastEthernet 0/1-3
channel-protocol lacp
channel-group 1 mode active

show etherchannel summary
```
MSW2 - MSW3
```
enable
configure terminal
interface range ge 1/0/1-3
channel-protocol lacp
channel-group 1 mode active

show etherchannel summary
```

#### Configuracion OSPF
MSW1 - MSW2 - MSW3 - MSW4
```
ip routing
router ospf 10

network 3.0.0.0 0.0.0.255 area 10
network 192.168.13.0 0.0.0.255 area 10
network 192.168.23.0 0.0.0.255 area 10

show running-config
```
#### Configuracion HSRP
MSW9 - MSW10 - MSW13 - MSW14
```
int range fe0/11-12
switchport trunk encapsulation dot1q
switchport trunk allowed vlan all
switchport mode trunk

interface vlan 13
ip add 192.168.13.6 255.255.255.0
ip helper-address 192.168.13.2
standby 10 ip 192.168.13.1
standby 10 priority 110
standby 10 preempt

interface vlan 23
ip add 192.168.23.6 255.255.255.0
ip helper-address 192.168.23.2
standby 10 ip 192.168.23.1
standby 10 priority 110
standby 10 preempt
```

#### Configuraciones Trunk y Access
Modo Troncal(aplica para todos los demas switches que se requiera la configuracion)

MSW11
```
int range fe0/11-12
switchport trunk encapsulation dot1q
switchport trunk allowed vlan all
switchport mode trunk
```

Modo acceso

SW2 - SW3
```
int fe0/1-2
switchport mode access
switchport access vlan 13
```

SW1 - SW4
```
int fe0/1-2
switchport mode access
switchport access vlan 23
```