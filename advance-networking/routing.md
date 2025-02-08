Network routers learn routing information via three methods:

    - Directly Connected routes
    - Static routes
    - Dynamic routing

A router running a dynamic routing protocol shares its routing knowledge with adjacent routers.

Dynamic routing protocols fall into two main categories - Interior Routing Protocol (IGP) and Exterior Routing Protocols (EGP). 

The only EGP in use today is the Border Gateway Protocol (BGP).

Interior Routing Protocols (IGP) fall within two main classes - Distance-Vector and Link-state.

- Distance Vector Routing
    - It is a dynamic routing algorithm where each router shares its entire routing table with its immediate neighbors.
    - The sharing of information takes place at regular intervals.
    - It uses Bellman-Ford’s algorithm.
    - Problems:
        - Susceptible to routing loops.
        - Slow convergence.
        - Scales easier.
        - Count to infinity problem.
- Link State Routing
    - It is a dynamic routing algorithm where each router shares the state of all its links with all routers in the network.
    - Information sharing occurs only whenever there is a change via a process called "flooding."
    - It uses Dijkstra’s algorithm.
    - Problems:
        - Heavy traffic due to flooding of packets. 
        - CPU/RAM intensive.
        - Scales difficult.