# PBR 001 

    
    Set up an isolated lab with 3 VMs: Kali (Host-Only + NAT), Ubuntu (Host-Only) and Windows (Host-Only).

    Host-Only network without DHCP, /24 static IPs and complete connectivity between VMs verified with ping, ARP and traceroute.

    Internet available only in Kali via NAT; Ubuntu/Windows without gateway or exit; validate ip_forward=0 and absence of MASQUERADE in Kali.

    Evidence organized in ~/lab/pbr001/ (Linux) and C:\lab\pbr001\ (Windows), 3x3 evidence matrix and final report 99_reporte.md.

    Strict evaluation: fails if there is Internet on Ubuntu/Windows, if Host-Only has DHCP or NAT exists between interfaces; target time 10 h.

    ---
    
