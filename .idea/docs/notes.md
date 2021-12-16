- 1 namespace per site per technology ( LTE(4g) vs  NRFR1(mmwave) vs NRFR2(sub6 low and mid) )
    - site1-4glte
    - site1-5gmmw
    - site1-5gsub6
    - 
- FrontH (per port)
    - PF s-plane
    - VF m-plane (netdevice) (tagged or untagged but still a VF) routable - vran-mgmt for CNF management
    - VF cu-plane (vfio) # c and u planes together but can have separate too
    - 2x VFs to cater transition during pod delete and create
- 
- 1 or more FHs in a node
- 1 MH per DU instance (number depends on number of instances), vlan per CU neighbour
- 1 MH per CU instance (number depends on number of instances)
- 
- BH s1c and s1u VF per CU instance 
    - actually bonded (inside pod) active/backup so therefore need 2 
    - s1c (4G) a.k.a. N2 (5G), really aka s1mme (3gpp)
    - s1u (4G) a.k.a. N3 (5G)
- 
- node-network-policy profile for FH (DU), MH (CU and DU) or BH (CU and Core)

  numVfs: 6 (sum of VFs for netdevice and vfio)
  nicSelector:
    pfNames:
      - ens1f0#0-3
      - LIST

  nodeSelector  # ex. ran.openshift.io/oran-mh-netdevice: ""




==========================ROLE Manifest in roles application
=== MCP per site per profile to control upgrades
=== Site can have multiple profiles
=== profile = hardware layout or use-case
name:
role_labels:
 -
role_annotations:
 -
#pao as manifest




WORKER COmpleted in aci status
    "event_time": "2021-12-10T13:27:37.071Z",
    "message": "Host: w0, reached installation stage Rebooting",
