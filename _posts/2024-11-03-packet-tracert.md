---
title: "Uso de Packet Tracer"
date: 2024-11-03 00:00:0
categories: [redes]
tags: [redes, packet_tracer]
---

### Objetivo
- Conocer el funcionamiento de la herramienta TRACEROUTE

### Topologia
<img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/topologia.png" 
alt="Topologia Packet Tracer"
style="border-radius: 15px;">

<a href="https://github.com/ElChe1/blog/blob/main/files/packet_tracer" download>Descargar archivo</a>

> Necesitas instalar Packet Tracert para poder abrir este archivo.


### Situación
La empresa para la que usted trabaja ha adquirido una nueva sucursal. Usted solicitó un mapa de topología de la nueva ubicación, pero al parecer no existe. Sin embargo, tiene información de nombres de usuario y contraseñas para los dispositivos de red de la sucursal nueva y conoce la dirección web del servidor de la sucursal nueva. Por lo tanto, verificará la conectividad y usará el comando tracert para determinar la ruta a la ubicación. Se conectará al router perimetral de la nueva ubicación para determinar los dispositivos y las redes conectados. Como parte de este proceso, utilizará diferentes comandos show para recopilar la información necesaria para terminar de documentar el esquema de asignación de direcciones IP y crear un diagrama de la topología.

> La contraseña de EXEC del usuario es **cisco**. La contraseña de EXEC privilegiado es **class**.


### Trazar y documentar una ubicación remota

> A medida que completa los siguientes pasos, copie el resultado del comando en un archivo de texto para facilitar la consulta y registrar la información que falta en la tabla de Documentación del esquema de asignación de direcciones.


1. Haga clic en Sales (Ventas) y en la ficha Desktop > Command Prompt (Escritorio > Símbolo del sistema). Use el comando ipconfig para revisar la configuración de la dirección IP de Sales.

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/Sales-Command-Prompt.png" alt="Prompt Sales Command" style="border-radius: 15px;">

2. La dirección del nuevo servidor web es b2server.pt.pka. Introduzca el siguiente comando nslookup para descubrir la dirección IP de b2server:

    ```terminal
    PC> nslookup b2server.pt.pka
    ```

    - ¿Qué dirección devolvió el comando para b2server? <kbd>172.16.0.3</kbd>

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/b_nslookup_b2server.pt.pka.png" alt="Nslooup b2server" style="border-radius: 15px;">

3. Introduzca el comando tracert para determinar la ruta desde Sales hasta b2server.pt.pka.
    
    ```terminal
    PC> tracert b2server.pt.pka
    ```

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/c_tracert_b2server.png" alt="Tracert b2server" style="border-radius: 15px;">

    > El tracert és un comando que lo que hace es ver los saltos que tenemos desde Ventas asta nuestro destino b2server.pt.pka, es decir 5 saltos . Los saltos hace referencia a los servidores, routers o switches a los cuales nos tenemos que conectar para llegar a nuestro destino. 

4. Telnet a la primera dirección IP del resultado de tracert e inicie sesión.

    ```terminal
    PC> telnet 172.16.0.1
    ```

5. Ya está conectado al router R4. Emita el comando traceroute en el router utilizando la dirección para b2server determinada en el paso b. 

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/e_traceroute.png" alt="Traceroute" style="border-radius: 15px;">

    - ¿Cuál es la diferencia entre el comando traceroute en el router y el comando tracert en la PC? 
    <kbd> El propósito de traceroute y tracert es el mismo, sus diferencias principales son la compatibilidad con el sistema operativo y los protocolos que utilizan por defecto. Ambos son útiles para diagnosticar problemas de conexión y para entender la estructura de la red entre el origen y el destino. 
    </kbd>

    <a href="https://www.xataka.com/basics/tracert-traceroute-que-como-funciona-como-se-utiliza">Más Información</a>

    - ¿Cuál es la importancia del R4 para Sales? <kbd>És el router de Sales</kbd>

6. Use el comando show ip interface brief para mostrar el estado de las interfaces en el R4. 

    - Según el resultado del comando, ¿qué interfaz se utiliza para alcanzar el siguiente dispositivo en el resultado de lista del comando tracert? <kbd>GigabitEthernet0/0</kbd>


    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/f_show_ip.png" alt="Show IP" style="border-radius: 15px;">

    > Sugerencia: utilice el comando show running-config para ver los valores de la máscara de subred para las interfaces.

7. Haciendo Telnet en la segunda dirección IP de la lista de tracert e inicie sesión. Puede utilizar el número de la columna del extremo izquierdo del resultado del comando tracert para seguir su recorrido en la lista. 

    - ¿Cuál es el nombre del dispositivo al que está conectado? <kbd>Tier3a</kbd>
    
    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/g_telnet.png" alt="Telnet" style="border-radius: 15px;">

8. Emita el comando show ip route y estudie el resultado. Según la lista de códigos que se muestra al comienzo del resultado, ¿cuáles son los diferentes tipos de rutas que se muestran en la tabla de routing?

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/h_show_ip.png" alt="Show IP" style="border-radius: 15px;">

9. Según el resultado del comando show ip route, ¿cuál es la interfaz de salida de la siguiente dirección IP que se indica en el resultado original del comando tracert?



10. Telnet a la tercera dirección IP de la lista de tracert e inicie sesión. ¿Cuál es el nombre de host del dispositivo actual?

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/j_telnet.png" alt="Telnet" style="border-radius: 15px;">

    - Emita el comando show ip route connected. ¿Cuáles son las redes conectadas directamente a este router?

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/j2_show_ip_route.png" alt="Show IP route" style="border-radius: 15px;">

11. Telnet a la cuarta dirección IP de la lista de tracert e inicie sesión. ¿Cuál es el nombre del dispositivo?

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/k_telnet.png" alt="Telnet" style="border-radius: 15px;">

12. Emita un comando para determinar a qué interfaz está conectado b2server.pt.pka.

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/l_show_ip_interface.png" alt="Show IP Interface" style="border-radius: 15px;">

13. Si utilizó la tabla de registro del esquema de direccionamiento a medida que completó los pasos anteriores, la tabla debería estar completa. Si no es así, termine la tabla.

    | Administrador | Interficie | IP | Màscara de subred |
    | :------------ |: -------------    | :-------------| ----------------: |
    | R4            | Serial0/0/0       | 64.100.150.1  | 255.255.255.252   |
    |               | G0/0              | 172.16.0.1    | 255.255.255.0     |
    |               | S0 / / 1.1        | 64.100.200.1  | 255.255.255.252   |

    | Administrador | Interficie | IP | Màscara de subred |
    | :------------ |:  -------------    | :-------------| ----------------: |
    | Tier3a        | GigabitEthernet0/0 | 64.104.222.1  | 255.255.255.252   |
    |               | G0 / 1             | 64.104.223.1  | 255.255.255.252   |
    |               | S0 / 0/0           | 64.100.100.2  | 255.255.255.252   |
    |               | Serial0/0          | 64.100.150.2  | 255.255.255.252   |

    | Administrador | Interficie | IP | Màscara de subred |
    | :------------ |:  -------------    | :-------------| ----------------: |
    | Tier3b        | FastEthernet0/2    | 64.104.222.5  | 255.255.255.252   |
    |               | G0 / 2             | 64.100.8.1    | 255.255.255.0     |
    |               | F0 / 1             | 128.107.46.1  | 255.255.255.0     |
    |               | GigabitEthernet0/1 | 64.104.222.2  | 255.255.255.252   |

    | Administrador | Interficie | IP | Màscara de subred |
    | :------------ |:  -------------    | :-------------| ----------------: |
    | B2-R1         | G0 / 0             | 64.104.222.6  | 255.255.255.255   |
    |               | GigabitEthernet0/1 | 128.107.64.1  | 255.255.255.0     |

    | Administrador | Interficie | IP | Màscara de subred |
    | :------------ |:  -------------    | :---------- ---| ----------------: |
    | b2server.pt.pka | NIC                | 128.107.64.254 | 255.255.255.0     |

14. Con la documentación completa del esquema de direccionamiento y la ruta de Sales a branch2.pt.pka, ahora debería poder dibujar la nueva ubicación de la sucursal en el espacio de registro de la topología que se encuentra a continuación.

    <img src="https://raw.githubusercontent.com/ElChe1/blog/refs/heads/main/images/packet_tracer/documentacion_topologia.png" alt="Documentación Topologia" style="border-radius: 15px;">

