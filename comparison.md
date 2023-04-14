# Comparison between Serviceguard and EXPRESSCLUSTER X
## Overview
HPE Serviceguard for Linux (Serviceguard) is a high availability software which provides high availability for applications with hot standby machine as same as EXPRESSCLUSTER X.
This article shows comparison between Serviceguard and EXPRESSCLUSTER X.

## Comparison
1. Server
	1. Onpremis server
		- Serviceguard
			- 3rd party servers are supported.
		- EXPRESSCLUSTER X
			- 3rd party servers are supported.

	1. Virtual machine
		- Serviceguard
			- Virtual machines are supported.
			- It's possible to combine with Hypervisor HA features. (For example VMware vMotion, vSphere HA, vSphere SRM... e.t.c)
		- EXPRESSCLUSTER X
			- Virtual machines are supported.
			- It's possible to combine with Hypervisor HA features. (For example VMware vMotion, vSphere HA, vSphere SRM... e.t.c)

	1. Cloud instance
		- Serviceguard
			- Cloud instances (IaaS) are supported.
		- EXPRESSCLUSTER X
			- Cloud instances (IaaS) are supported.
			- Ref:
				- EXPRESSCLUSTER is used on a lot of Cloud environment such as Amazon Web Services (AWS), Microsoft Azure (Azure), Oracle Cloud Infrastructure (OCI).  
					The reason why EXPRESSCLUSTER is used on Cloud, refer to [EXPRESSCLUSTER documant page](https://www.nec.com/en/global/prod/expresscluster/en/doc/intro.html)  
					-> [EXPRESSCLUSTER X Product Introduction for Cloud](https://www.nec.com/en/global/prod/expresscluster/en/doc/materials/EXPRESSCLUSTER_x50_salestool_for_cloud.pdf)
				- Some standard system configuration is introduced in [Officail Blog](https://www.nec.com/en/global/prod/expresscluster/en/blog/index.html).
1. CPU architecture
	1. Supported CPU
		- Serviceguard
			- x86_64
		- EXPRESSCLUSTER X
			- x86_64
			- IBM POWER LE
				- Note:
					- Kernel driver features including data mirroing are not supported for IBM POWER LE. Check "Supported Linux OS" above for more details.

1. OS
	1. Supported OS
		- Serviceguard
			- Linux
				- RedHat Enterprise Linux
				- SUSE Linux Enterprise Server
				- Oracle Linux
		- EXPRESSCLUSTER X
			- Windows
				- Windows Server
					- Ref: [Supported Windows OS](https://www.nec.com/en/global/prod/expresscluster/en/sysreq/os_win.html)
			- Linux
				- RedHat Enterprise Linux
				- SUSE Linux Enterprise Server
				- Ubuntu
				- Oracle Linux
				- Amazon Linux
					- Ref: [Supported Linux OS](https://www.nec.com/en/global/prod/expresscluster/en/sysreq/os_lin.html)
					- Note:
						- Kernel driver features including data mirroing are not supported for some distributors and kernels. Check "Supported Linux OS" above for more details.
	1. Secure boot
		- Serviceguard
			- Secure boot is supported.
		- EXPRESSCLUSTER X
			- Secure boot is not supported.

1. UI
	1. UI for cluster management
		- Serviceguard  
			You can manage a cluster with the following UI:
			- GUI (Serviceguard Manager, Serviceguard Manager+)
				- Create and modify a cluster
				- Validate cluster settings
				- Get cluster status
				- Operate a cluster
				- Alert hostory
				- Rehearsal of DR cluster
					- When dummy failure for rehearsal is executed, dry-run of recovery action will occur.
			- CLI
				- Create and modify a cluster
				- Validate cluster settings
				- Get cluster status
				- Operate a cluster
				- Alert hostory
				- Rehearsal of DR cluster
					- When dummy failure for rehearsal is executed, dry-run of recovery action will occur.
			- REST API
				- Create and modify a cluster
				- Validate cluster settings
				- Get cluster status
				- Operate a cluster
				- Alert hostory
				- Rehearsal of DR cluster
					- When dummy failure for rehearsal is executed, dry-run of recovery action will occur.
				- Note:
					- Java installation is required for REST API.
		- EXPRESSCLUSTER X  
			You can manage a cluster with the following UI:
			- GUI (Cluster WebUI)
				- Create and modify a cluster
				- Validate cluster settings
				- Get cluster status
				- Operate a cluster
				- Alert graph and hostory
				- Operation hository
				- Estimated failover time
				- Rehearsal of monitoring failure
					- When dummy failure for rehearsal is executed, actual recovery action for the monitoring failure will occur. (Not dry-run)
			- CLI
				- Create and modify a cluster
				- Get cluster status
				- Operate a cluster
			- RESTful API
				- Get cluster status
				- Operate a cluster
				- Note:
					- Node.js installation is required for RESTful API.

1. Cluster system configuration
	1. Cluster node number
		- Serviceguard
			- 1 - 32
		- EXPRESSCLUSTER X
			- 2 - 32
			- Note:
				- There is another product "EXPRESSCLUSTER X SingleServerSafe" (SSS) which is for 1 node.
				- SSS license fee is less than EXPRESSCLUSTER X.
				- Ref: [EXPRESSCLUSTER X SingleServerSafe Presentation](https://www.nec.com/en/global/prod/expresscluster/en/doc/intro.html)
	1. Cluster configuration
		- In the case that one application is clustered:
			- Serviceguard  
				- Provides Active-Standby (hot standby) cluster.
			- EXPRESSCLUSTER X
				- Provides Active-Standby (hot standby) cluster.
		- In the case that multi applications are clustered:
			- Serviceguard  
				- Provides Active-Standby (hot standby) and Active-Active cluster.  
					e.g.) APP1 and APP2 are clustered on SV1 and SV2.
					- Active-Standby: APP1 and APP2 are activated on SV1 as a default.
					- Active-Active: APP1 is activated and APP2 is activated on SV2 as a default.
				- Dependency of applications (starting/stopping order) can be set.
			- EXPRESSCLUSTER X
				- Provides Active-Standby (hot standby) and Active-Active cluster.  
					e.g.) APP1 and APP2 are clustered on SV1 and SV2.
					- Active-Standby: APP1 and APP2 are activated on SV1 as a default.
					- Active-Active: APP1 is activated and APP2 is activated on SV2 as a default.
				- Dependency of applications (starting/stopping order) can be set.
	1. Network
		- Serviceguard
			- All cluster nodes should be communicatable by IP address.
			- Cross subnet cluster can be configured.
		- EXPRESSCLUSTER X
			- All cluster nodes should be communicatable by IP address.
			- Cross subnet cluster can be configured.
	1. Application
		- Serviceguard
			- Controls applications (start/stop/failover) by commands or scripts.  
				Therefore, you can make applications which can be started or stopped by commands or scripts clustered.
		- EXPRESSCLUSTER X
			- Controls applications (start/stop/failover) by commands or scripts.  
				Therefore, you can make applications which can be started or stopped by commands or scripts clustered.
	1. Data  
		If there is data which is access by application and needs to be the same along cluster nodes, it is shared as follows:
		- Serviceguard
			- Shared disk
				-  SCSI-3 PR should be enabled for access control.
			- Data replication
				- Serviceguard itseld does not have data replication feature and 3rd party software replication feature should to be combined.  
					For example, repliaction by MD RAID or LVM RAID (ExtendedDistanceClusters, XDC), DRBD (Flex Storage Add-on), database (Oracle Data Guard, MS SQL Server AlwaysOn, SAP HANA replication) or HPE storage (Metrocluster)
			- Hybrid of shared disk and data replication
				- On shared disks, SCSI-3 PR should be enabled for access control.
				- For data replication, 3rd party software replication feature should to be combined.

		- EXPRESSCLUSTER X
			- Shared disk
				- Access control is managed by EXPRESSCLUSTER X itself.
			- Data replication
				- Data replication is done by EXPRESSCLUSTER X mirroring feature and 3rd party software replication feature is not required.  
					- For example, if you want to replicate Oracle DB, it can be done by EXPRESSCLUSTER data and you don't have purchase Oracle Data Guard.
					- If you want to combine with 3rd party software replication feature, it is also possible by creating custom script.
					- For EXPRESSCLUSTER X mirroring feature, additional license is required.
			- Hybrid of shared disk and data replication
				- On shared disks, Access control is managed by EXPRESSCLUSTER X.
				- Data replication is done by EXPRESSCLUSTER X mirroring feature.
				- For EXPRESSCLUSTER X mirroring feature, additional license is required.
		- Ref:
			- About the details for Shared disk, Data replication (Mirror disk) and Hybrid of them (Hybrid disk) configuration, refer to [EXPRESSCLUSTER documant page](https://www.nec.com/en/global/prod/expresscluster/en/doc/intro.html)  
				-> [EXPRESSCLUSTER X Product Introduction for Windows/Linux](https://www.nec.com/en/global/prod/expresscluster/en/doc/materials/ExpressCluster_x50_presentation.pdf)
	1. Access point
		- In the case of Onpremis network
			- Serviceguard
				- Relocatable IP which is a kind of virtual IP address is provided.
					- Note:
						- The relocatable IP network address depends on its subnetwork.  
							Therefore, in the case of cross subnet cluster, relocatable IP should be changed.
							- e.g.) Node1 has IP "10.1.1.11" and node2 has IP "10.1.1.12", then you can use one relocatable IP "10.1.1.20" for both nodes.
							- e.g.) Node1 has IP "10.1.1.11" and node2 has IP "10.2.1.11", then you need to configure 2 relocatable IPs, "10.1.1.20" for node1 and "10.2.1.20" for node2. (You cannot use a same relocatable IP for both nodes.)
			- EXPRESSCLUSTER X
				- Floating IP (fip) which is a kind of virtual IP address is provided.
					- Note:
						- The fip network address depends on its subnetwork.  
							Therefore, in the case of cross subnet cluster, fip IP should be changed.
							- e.g.) Node1 has IP "10.1.1.11" and node2 has IP "10.1.1.12", then you can use one fip "10.1.1.20" for both nodes.
							- e.g.) Node1 has IP "10.1.1.11" and node2 has IP "10.2.1.11", then you need to configure 2 fips, "10.1.1.20" for node1 and "10.2.1.20" for node2. (You cannot use a same fip for both nodes.)
				- Virtual IP (vip) is provided.
					- Note:
						- Vip is propagated by RIP.
						- On all network nodes among cluster nodes and clients, RIP should be enabled.
					- You can use a same vip on cross network cluster.
				- Virtual hostname is provided.
					- Note:
						- DNS Server which allows dynamic update by cluster nodes (DDNS Server) are required.
					- In the case that one DDNS Server can cover cross network, you can use a same virtual hostname on cross network cluster.
		- In the case of Cloud network
			- Serviceguard
				- Virtual IP feature is provided for AWS, Azure and GCP.
					- Note:
						- L4 load balancer is required for the virtual IP feature of AWS, Azure and Google Cloud Platform (GCP).
			- EXPRESSCLUSTER X
				- Virtual IP feature is provided for AWS, Azure, GCP and OCI.
					- Note:
						- L4 load balancer is required for the virtual IP feature of Azure, GCP and OCI.
				- Virtual hostname feature is provided for AWS, Azure, GCP and OCI.
					- Note:
						- DNS service is required.
1. Monitoring
	1. Application monitoring
		- Serviceguard
			- Application status is monitored by a monitoring script.
				- Note:
					- You need to create scripts for monitoring.
			- Monitoring script template for supported database, file server, internet server and application server are included in Toolkit.
				- Note:
					- Toolkit is not bundled with dase edition.
		- EXPRESSCLUSTER X
			- Application status is monitored by a monitoring script, process name or process id (pid).
				- Note:
					- In the case of script moniring, you need to create monitoring scripts. However, in the case of process name or pid monitoring, you can monitor by just specifying some parameters such as process name.
			- Not only status monitoring but also hang-up monitoring for supported database, file server, internet server and application server is available.
				- By specifying parameters, you can use the hang-up monitoring.
				- Note:
					- In order to use the hang-up monitoring, additional licenses are required.
	1. Network monitoring
		- Serviceguard
			- Provides relocatable IP monitoring, NIC mointoring and Ping responce monitoring.
		- EXPRESSCLUSTER X
			- Provides relocatable IP monitoring, NIC mointoring and Ping responce monitoring.
	1. Other monitoring
		- Serviceguard
			- Provides disk monitoring.
		- EXPRESSCLUSTER X
			- Provides disk monitoring.
			- Provides user space hang-up monitoring.
				- In the case that user space hang-up occurs, OS is stopped forcibly for quick recovery.
1. Sprit brain countermeasures  
	In order to avoid sprit brain, the following features can be configured:
	- Serviceguard
		- Quorum Server
		- Cluster Lock LUN which is a kind of quorum disk on a shared disk
	- EXPRESSCLUSTER X
		- Witness Server
		- Disk Heartbeat which is a heartbeat via a shared disk
1. Alert
	- EXPRESSCLUSTER X
		- You can get alert message by E-mail, SNMP, SNMP trap, Amazon SNS
	- Serviceguard
		- You can get alert message by E-mail, SNMP, WBEM

## Reference
- Serviceguread
	- "HPE Serviceguard for Linux Certification Matrix"
	- "HPE Serviceguard for Linux - Product Information Reference"
	- "Managing HPE Serviceguard for Linux"
- EXPRESSCLUSTER X
	- [EXPRESSCLUSTER X documents](https://www.nec.com/en/global/prod/expresscluster/en/doc/index.html)
