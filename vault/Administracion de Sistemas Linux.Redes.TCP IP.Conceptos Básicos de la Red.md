---
id: 036kvnh6s1how4ki1gm6ugb
title: 1.2 Conceptos Básicos de la Red
desc: ''
updated: 1655669168787
created: 1655668214685
---

Author: @Francisco
Tags: #sysadmin #networking

Comúnmente al TCP/IP se le considera como un `protocol suite` o un conjunto de protocolos; los cuales juntos trabajan de manera excepcional. Esto incluye varios componentes, cada uno de ellos definidos por distintos estándares. 

- IP, `Internet Protocol` el protocolo de Internet, el cual rutea paquetes de datos de una maquina a otra. 
- ICMP, `Internet Control Message Protocol`. El cual define varios tipos de soporte bajo nivel para IP, que incluye mensajes de error, ayuda de enrutamiento y la ayuda para `debugging` o depuración. 
- ARP, `Address Resolution Protocol`. Se encarga de traducir las direcciones de IP a direcciones de Hardware. 
- UDP, `User Datagram Protocol`, el cual implementa la entrega de datos de manera no verificada y en una sola via. 
- TCP, `Transmission Control Protocol`. El cual implementa conversaciones fiables, `full duplex` con control de flujo y correction de error. 

Hay que tener en cuenta que estos protocolos se encuentran arreglados de manera jerárquica o en modo `stack`, siendo los que están más arriba los protocolos de más alto nivel en abstracción. 