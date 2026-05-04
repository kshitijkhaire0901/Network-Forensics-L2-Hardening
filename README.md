# Network Convergence Failure & Host Resource Exhaustion: Forensic AuditOverview

At 17:30 IST, a physical-to-logical failure occurred within a simulation environment, resulting in a Kernel Panic on the host engineering workstation. This project documents the Incident & Response (I&R) cycle used to restore system integrity and harden the network against future broadcast storms.  Root Cause Analysis (RCA)Trigger: An unintentional Layer 2 Loop between Switch0 and Switch1.  

Mechanism: Absence of active STP convergence generated a recursive frame replication (Broadcast Storm).  

Impact: Massive CPU cycle consumption led to a total system freeze and volatile data loss.  

Forensic EvidenceInterface Audit: Identification of Fa0/1 in an administratively down state post-recovery. 
See Administratively_Down.png for callouts.  

Logical Verification: Confirmed Spanning Tree Protocol (STP) "Point of Blocking" to neutralize the loop. See Network_Design.png for visual proof.  

Connectivity: Validated end-to-end data plane integrity via ICMP Echo Requests.  

Remediation & Hardening (SOPs)Administrative Recovery: Restored management interfaces via CLI.  

Incorruptible Governance: Assigned static management IPs for persistent access.  

Edge Protection: Enabled spanning-tree bpduguard enable on all access ports to prevent unauthorized loops. 

Persistence: Committed all configuration changes to NVRAM using the write memory command.  
