# Manual - Practica 1

## Especificaciones de Enunciado

#### VTP

* Dominio: g# `->` g1
* VLAN:
    * Primaria11
    * Basicos21
    * Diversificado31

#### Direcciones de red

* Formato: 
    * Primaria: 192.168.x.0/24
    * Basicos: 192.168.x.0/24
    * Diversificado: 192.168.x.0/24

* Quedaria: 
    * Primaria: `192.168.11.0/24`
    * Basicos: `192.168.21.0/24`
    * Diversificado: `192.168.31.0/24`

#### Nombres y password de los switches

* Cambiar el nombre desde CLI a cada switch:
    * Formato: `SW#A_G1`
        * #A: numero de switch
* Password: secreto y configurar en el switch server
    * Formato: `redes2grupo1`

## Configuracion, nombre de switch:

```
# Entrar a configuracion para cada switch
enable
configure terminal

# Asignar nombre
hostname SW1_G1
hostname SW2_G1
hostname SW3_G1
hostname SW4_G1
hostname SW5_G1
hostname SW6_G1
hostname SW7_G1
hostname SW8_G1
hostname SW9_G1
hostname SW10_G1
hostname SW11_G1
hostname SW12_G1

# Guardar
copy running-config startup-config
```

## Configuracion, IPs en PCs

* Subnet Mask: 255.255.255.0
* Primaria:
    * PC1: 192.168.11.2
    * PC2: 192.168.11.3
    * PC9: 192.168.11.4
    * PC10: 192.168.11.5
* Basicos:
    * PC3: 192.168.21.2
    * PC8: 192.168.21.3
* Diversificado:
    * PC4: 192.168.31.2
    * PC5: 192.168.31.3 
    * PC6: 192.168.31.4 
    * PC7: 192.168.31.5 

## Configuracion, VTP (modo server, modo client, enlaces trunk)

#### SW12 (Server):

* Modo servidor:

```
enable
configure terminal
vtp mode server
vtp domain g1
exit
show vtp status
```

* Crear VLANs:

```
enable
configure terminal
vlan 11
name Primaria11
vlan 21
name Basicos21
vlan 31
name Diversificado31
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/7
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/10
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW9 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/4
switchport mode trunk
description TRUNK
exit
interface range fastEthernet 0/6-9
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW11 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/8
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/11
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW8 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/3
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/5
switchport mode trunk
description TRUNK
exit
interface range fastEthernet 0/10-12
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW10 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/9
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/12
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW2 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface range fastEthernet 0/2-6
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW1 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface range fastEthernet 0/2-6
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW3 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/3
switchport mode trunk
description TRUNK
exit
interface range fastEthernet 0/6-9
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW4 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface range fastEthernet 0/4-5
switchport mode trunk
description TRUNK
exit
interface range fastEthernet 0/10-12
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW5 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/7
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/10
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW6 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/8
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/11
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

#### SW7 (Client):

* Modo client:

```
enable
configure terminal
vtp mode client
vtp domain g1
exit
show vtp status
show vlan
```

* Configuracion modo trunk:

```
enable
configure terminal
interface fastEthernet 0/9
switchport mode trunk
description TRUNK
exit
interface fastEthernet 0/12
switchport mode trunk
description TRUNK
end
show running-config
copy running-config startup-config
```

## Configuracion, VTP (enlaces access)

#### SW5 y SW12:

```
enable
configure terminal
interface range fastEthernet 0/14-15
switchport mode access
switchport access vlan 11
description ACCESS_VLAN_11
end
show running-config
copy running-config startup-config
```

#### SW6 y SW11:

```
enable
configure terminal
interface fastEthernet 0/16
switchport mode access
switchport access vlan 21
description ACCESS_VLAN_21
end
show running-config
copy running-config startup-config
```

#### SW7 y SW10:

```
enable
configure terminal
interface range fastEthernet 0/17-18
switchport mode access
switchport access vlan 31
description ACCESS_VLAN_31
end
show running-config
copy running-config startup-config
```