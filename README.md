# Comandos Cisco Básicos para Configuración de Router

Este repositorio contiene comandos típicos para la configuración básica de un router Cisco.

## Configuración Básica

```cisco
enable
configure terminal

! Configuración de interfaces
interface GigabitEthernet0/0
 ip address 192.168.100.33 255.255.255.224
 no shutdown
 exit

interface GigabitEthernet0/1
 ip address 192.168.100.74 255.255.255.252
 no shutdown
 exit

interface GigabitEthernet0/2
 ip address 192.168.100.77 255.255.255.252
 no shutdown
 exit
