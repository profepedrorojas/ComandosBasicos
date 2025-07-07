enable
configure terminal

! Configuración básica de interfaces
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

! Configuración global
hostname R1
banner motd #Acceso restringido por Profe Pedro#
line console 0
 password ulagos
 login
 exit
enable secret 2025
service password-encryption

! Configuración RIP
router rip
 version 2
 network 192.168.100.32
 network 192.168.100.72
 network 192.168.100.76
 no auto-summary
 exit

! Configuración OSPF
router ospf 1
 network 192.168.100.32 0.0.0.31 area 0
 network 192.168.100.72 0.0.0.3 area 0
 network 192.168.100.76 0.0.0.3 area 0
 passive-interface GigabitEthernet0/0
 default-information originate
 exit

! Configuración DHCP
ip dhcp pool RED_LAN
 network 192.168.100.32 255.255.255.224
 default-router 192.168.100.33
 dns-server 8.8.8.8
 exit

! Guardar configuración
end
copy running-config startup-config
presionar tecla enter

!Comandos de verificación (ejecutar en modo enable):
show running-config
show ip interface brief
show ip route
show ip ospf neighbor
show ip dhcp binding
ping 192.168.100.1
