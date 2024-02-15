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
--------------------------------------------------------------------
## Configuración de STP

Para la primera configuracion no es necesario introducir comandos ya que el protocolo PVST esta configurado por defecto en los switches

**Comandos para configuracion RPVST**
```
enable
configure terminal
spanning-tree mode rapid-pvst
exit
show running-config
```
**Comandos para realizar las pruebas de rendimiento y recuperacion :**
```
enable
configure terminal
interface FastEthernet0/10
shutdown
no shutdown (prender)
```

## Seguridad de interfaces de red

### Políticas de puerto compartidas

#### Desactivar el protocolo DTP de los puertos troncales:
- Estado del protocolo DTP
    ```
    show interfaces FastEthernet0/2 switchport
    ```
- Desactivar el DTP en un puerto
    ```
    switchport mode trunk
    switchport nonegotiate
    ```


### Seguridad para interfaces asignadas a la VLAN

#### Primaria
- SW5

    PC1
    ```
    enable
    configure terminal
    interface fastEthernet 0/14
    switchport port-security
    ```
    PC2
    ```
    enable
    configure terminal
    interface fastEthernet 0/15
    switchport port-security
    ```
- SW12

    PC9
    ```
    enable
    configure terminal
    interface fastEthernet 0/15
    switchport port-security
    ```
    PC10
    ```
    enable
    configure terminal
    interface fastEthernet 0/14
    switchport port-security
    ```

#### Basicos
- SW6

    PC3
    ```
    enable
    configure terminal
    interface fastEthernet 0/16
    switchport port-security
    switchport port-security maximum 1
    switchport port-security mac-address 0001.63D9.D589
    ```
- SW11

    PC8
    ```
    enable
    configure terminal
    interface fastEthernet 0/16
    switchport port-security
    switchport port-security maximum 1
    switchport port-security mac-address 0004.9ABA.D139
    ```

    
#### Diversificado
- SW7

    PC4
    ```
    enable
    configure terminal
    interface fastEthernet 0/17
    switchport port-security
    ```
    PC5
    ```
    enable
    configure terminal
    interface fastEthernet 0/18
    switchport port-security
    ```
- SW10

    PC6
    ```
    enable
    configure terminal
    interface fastEthernet 0/18
    switchport port-security
    ```
    PC7
    ```
    enable
    configure terminal
    interface fastEthernet 0/17
    switchport port-security
    ```

## Elección de escenario con mejor resultado de convergencia
Para la eleccion del mejor escenario se realizó una serie de pruebas configurando los switches con los distintos protocolos (PVST y RPVST)

#### Tiempos de recuperación de red   
| Escenario | Protocolo spanning-tree | Red primaria | Red Básicos | Red Diversificado |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| 1 | PVST | 47.12 *seg* | 44.5 *seg* | 60.44 *seg* |
| 2 | Rapid PVST | 1.44 *seg* | 0.96 *seg* | 1.22 *seg* |

**Elección de escenario**

Al hacer la comparativa de los tiempos de repcuperacion de cada red llegamos a la cconclusión de que el protocolo RPVST es mas rapido y no se nota la perdida de conexion haciendo de este el ideal para la topografía propuesta