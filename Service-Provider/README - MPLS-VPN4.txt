		**** MPLS L3 VPN ****

---- Section 1 - IP Addressing ----

1.) Configure loopback, external (customer-facing), and
internal (provider-facing) IP addresses on service provider routers.

2.) Configure loopback and provider edge-facing interfaces on customer site routers (for example, HQ, Branch-1, Branch-2 et cetera).

---- Section 2 - Service Provider Routing ----

1.) Configure an IGP (OSPF) in the service
provider network. Only advertise the SP loopbacks and 
backbone links.

3.) Ensure that OSPF comes up in all links. The SP2
router should have two neighbors.

---- Section 3 - MPLS in SP ----

1.) Enable loopback0 with LDP (MPLS label protocol) with
the 'force' parameter. 

2.) Configure MPLS only on backbone links. Use the
'mpls ip' command.

---- Section 4 - VRF for L3VPN ----

1.) Create a VRF route distinguisher and target for the customers. 

2.) Import and export route distinguishers.

3.) Designate 'IP VRF forwarding' for the customer VRF on the interfaces that face the customer edge router.

---- Section 5 - Customer Routing ----

1.) Implement OSPF for the customer routers and configure it on the provider edge and customer edge routers. Use a different area for
the customer routes instead of the provider area router. The provider routers will not know of this OSPF process. Use a different area # than the ISP. 

---- Section 6 - BGP ----

1.) Enable iBGP on the provider edge routers. This will create a full mesh.

2.) Redistribute OSPF subnets for the AS under global BGP configuration on service provider routers.

3.) Redistribute BGP subnets for the AS under global OSPF configuration on service provider routers.
