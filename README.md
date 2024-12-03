# Useful-BloodHound-Cyphers

## Locations of "Owned" objects
```
MATCH p = (:Domain)-[:Contains*1..]->(n:Base)
WHERE n.system_tags CONTAINS "owned"
RETURN p
LIMIT 1000
```

## Shortest paths from "Owned" objects to Tier Zero / High Value Targets
```
MATCH p=shortestPath((n)-[:Owns|GenericAll|GenericWrite|WriteOwner|WriteDacl|MemberOf|ForceChangePassword|AllExtendedRights|AddMember|HasSession|Contains|GPLink|AllowedToDelegate|TrustedBy|AllowedToAct|AdminTo|CanPSRemote|CanRDP|ExecuteDCOM|HasSIDHistory|AddSelf|DCSync|ReadLAPSPassword|ReadGMSAPassword|DumpSMSAPassword|SQLAdmin|AddAllowedToAct|WriteSPN|AddKeyCredentialLink|SyncLAPSPassword|WriteAccountRestrictions|GoldenCert|ADCSESC1|ADCSESC3|ADCSESC4|ADCSESC5|ADCSESC6a|ADCSESC6b|ADCSESC7|ADCSESC9a|ADCSESC9b|ADCSESC10a|ADCSESC10b|ADCSESC13|DCFor|SyncedToEntraUser*1..]->(m))
WHERE "admin_tier_0" IN split(m.system_tags, ' ') AND n<>m AND n.system_tags CONTAINS "owned"
RETURN p
LIMIT 1000
```
