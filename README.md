
# BoardNet Enterprise Network Topology

A complete, fault-tolerant enterprise network infrastructure designed to connect six distinct examination boards across Bangladesh. This project demonstrates core network engineering principles including IP allocation, dynamic and static routing, service automation, and redundancy failover. Developed as an infrastructure project at BRAC University.

## Project Scope
The network connects a central hub (Dhaka) with five regional boards (Chattogram, Rajshahi, Sylhet, Khulna, and Barishal). The architecture ensures strict subnet isolation, automated endpoint configuration, centralized domain resolution, and seamless application-layer communication between isolated geographic nodes.

## Key Technical Features

* **VLSM IP Addressing:** Mathematically optimized subnetting based on a `10.79.0.0/16` base. Network segments range from `/23` blocks for high-density central boards to `/30` point-to-point serial links, minimizing IP waste and isolating broadcast domains.
* **Hybrid Routing Architecture:** 
  * **RIPv2:** Drives the dynamic core triangle (Dhaka, Sylhet, Rajshahi) for fast topological convergence.
  * **Floating Static Routes:** Establishes fault-tolerant, recursive backup paths for Khulna and Barishal. If the primary Dhaka fiber link drops, traffic automatically reroutes through the neighboring board.
  * **Default Routes:** Secures the Chattogram stub network.
* **Service Automation (DHCP & IP Helpers):** Centralized DHCP pools in the Dhaka core router handle dynamic IP leasing for remote boards via `ip helper-address` broadcast interception, while dedicated physical servers handle localized leasing in Khulna and Barishal.
* **Application Layer Infrastructure (DNS, Web, Email):** 
  * A central DNS server translates localized `.edu.bd` domains.
  * Dedicated Web and Email (SMTP/POP3) servers host distinct regional portals and facilitate cross-country administrative communication.

## Repository Contents
* `BoardNet_Topology.pkt`: The interactive Cisco Packet Tracer simulation file containing all routing tables, server configurations, and endpoint setups.
* `Topology_Map.png`: High-level visual diagram of the network architecture.
* `Project_Documentation.pdf`: Complete breakdown of the routing configurations and the VLSM addressing table.
