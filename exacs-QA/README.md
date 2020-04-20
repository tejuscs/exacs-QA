<table class="tbl-heading"><tr><td class="td-logo">[![](images/obe_tag.png)](README.md)

Last Updated:<br>April 08, 2020
</td>
<td class="td-banner">
# Working with Exadata Cloud Service On OCI
</td></tr><table>

An Exadata Cloud Service DB system consists of a quarter rack, half rack, or full rack of compute nodes and
storage servers, tied together by a high-speed, low-latency InfiniBand network and intelligent
Exadata software. You can configure automatic backups, optimize for different workloads, and
scale up the system to meet increased demands.

The compute nodes are each configured with a virtual machine (VM). You have root privilege for
the compute node VMs, so you can load and run additional software on them. However, you do
not have administrative access to the Exadata infrastructure components, such as the physical
compute node hardware, network switches, power distribution units (PDUs), integrated lights-out
management (ILOM) interfaces, or the Exadata Storage Servers, which are all administered by
Oracle.

You have full administrative privileges for your databases, and you can connect to your databases
by using Oracle Net Services from outside Oracle Cloud Infrastructure. You are responsible for
database administration tasks such as creating tablespaces and managing database users. You
can also customize the default automated maintenance setup, including backups, and you have
full control of the recovery process in the event of a database failure.

These hands-on lab guides provide step-by-step directions to setting up and using your Exadata Cloud Service platform in the Oracle Cloud Infrastructure.

Lab 1 - 5 deals with setting up the infrastructure and connectivity to EXACS.

Labs 6 & 7 are geared towards Monitoring and Managing your EXACS databases.

Labs 8 - 11  are intended for Backup, Recovering and Migrating your databases.

Lab 12 - 14 onwards demonstrate advanced lab guides for Database Vault, Key Management using Oracle Key Vault and advanced Data safe lab guides.

Lab 15 - 19 are additonal labs which talks about connectig your EXACS databases with Python application, working with OCI CLI, build APEX applications and automating with Terraform.

## Goals for this workshop
1. Prepare your private network in the Oracle Cloud Infrastructure
2. Provision Exadata Cloud Service Infrastructure in a private OCI network
3. Provision databases on your ExaCS Infrastructure
4. Configure a development system for use with your EXACS database
5. Setup VPN Connectivity to your Exadata Cloud Service Infrastructure
6. Setup, Discover, Manage and Monitor database with Enterprise Manager
7. Data Safe with EXACS
8. Migrate an on-prem application schema usign Data Pump
9. Real time migration of database using Oracle Goldengate Replication
10. Backup and Recovery using Console, RMAN and API's
11. Protect your data with Database Vault
12. Key Management using Oracle Key Vault
13. Data Safe Advanced lab
14. Use OCI CLI commands to wrok with EXACS
15. Automation with Terraform*
16. Build and deploy Python application stacks on EXACS
17. Build APEX applicaiton on EXACS


# Workshop Overview

## Before You Begin
**What is Exadata Cloud Service?**

- Exadata Cloud Service is offered on Oracle Cloud Infrastructure, within OCI regions.
- Exadata Cloud Service available in quarter Rack, Half Rack or full Rack configurations.
- Exadata rack in OCI includes DB nodes, storage nodes and InfiniBand switches.
- The storage and compute nodes are connected via high bandwidth Infiniband network that
provides RDMA based storage access to the compute nodes.
- Exadata storage software runs on storage servers and offloads database SQL processing
overheads.
- Currently, a single VM per compute node is supported. It allows root access for customers
while protecting hardware and network, DB nodes are virtualized using Xen based OVM.
- Oracle Manages storage cells, switches, management or IB network while customer manages
database compute nodes.
- Exadata Cloud Service provides a control Plane, a Web-based self-service management
interface for Exadata cloud service provisioning and interactive access to service administration function

**You are all set, let's begin!**


## Lab 1: Prepare your private network in the Oracle Cloud Infrastructure (demo only)

**Key Objectives**:
- Create compartments and user groups with the right set of access policies for separation of duties
- Create admin and database user accounts
- Layout a secure network for the database and application infrastructure

**[Click here to run Lab 1](EXACS-Networking.md)**


## Lab 2: Provision Exadata Infrastructure in a private OCI network (demo only)

**Key Objectives**:

As a fleet administrator,
- deploy an Exadata Cloud Service Infrastructure in a pre-provisioned private network in your OCI account


**[Click here to run Lab 2](ProvisionExaInfra.md)**


## Lab 3: Provision databases on your ExaCS Infrastructure (demo only)

**Key Objectives**:

As a database administrator,
- Deploy database onto an  Exadata Cloud Service Infrastructure

**[Click here to run Lab 3](ProvisionDatabase.md)**


## Lab 4: Configure a development system for use with your EXACS database

**Key Objectives**:

As a database user, DBA or application developer,

- Configure a secure connection from your application instance to your dedicated autonomous database using Oracle SQL Developer, SQLCL and SQL*Plus.

**[Click here to run Lab 4](ConfigureDevClient.md)**



## Lab 5: Setup VPN Connectivity to your Exadata Cloud Service Infrastructure

**Key Objectives**:
As a database user, DBA or application developer,
- Configure a VPN server in OCI based on OpenVPN software
- Configure your VPN client and connect to VPN Server

**[Click here to run Lab 5](ConfigureVPN.md)**

## Lab 6: Setup, Discover, Manage and Monitor database with Enterprise Manager

**Key Objectives**:

As a System admin,

- Install and configure Enterprise Manager on OCI
- Configure Enterpise Manager with Exadata Cloud Service


**[Click here to run Lab 6](MonitorAndManageWithEM.md)**


## Lab 7: Data Safe with EXACS

**Key Objectives**:

As an database admin,
- Assess the security of a database by using the Security Assessment feature in Oracle Data Safe
- Assess user security in your target database by using the User Assessment feature in Oracle Data Safe.
- Fix some of the security issues based on the assessment findings

**[Click here to run Lab 7](DataSafe.md)**

## Lab 8: Migrate an on-prem application schema usign Data Pump

**Key Objectives**:

As an database admin,
- Download a sample datapump export dump file
- Upload .dmp file to OCI Object storage bucket
- Setup cloud credentials and use data pump import to move data to your EXACS database

**[Click here to run Lab 8](DataPump.md)**

## Lab 9: Real time migration of database using Oracle Goldengate Replication

**Key Objectives**:

As an database admin,
- Replicate real time data from a simulated on-premise database to EXACS database.


**[Click here to run Lab 9](Goldengate.md)**

## Lab 10: Backup and Recovery using Console and API's

**Key Objectives**:

As an application developer, DBA user,

- Configure Exadata Cloud Service database backup and Recovery using Console and API

**[Click here to run Lab 10](Backup&Recovery.md)**


## Lab 11: Protect your data with Database Vault

**Key Objectives**:

As a database security admin,

- Enable database vault in your EXACS database
- Implement separation of duties to protect sensitive data in your database

**[Click here to run Lab 11](DBVault.md)**

## Lab 12: Key Management using Oracle Key Vault

**Key Objectives**:

As a database admin or user,

- To be written...

**[Click here to run Lab 12](KeyVault.md)**

## Lab 13: Data Safe Advanced lab

**Key Objectives**:

As a database security admin,

- Configure Data Masking and Auditing and Reporting for EXACS database

**[Click here to run Lab 13](DataSafePE.md)**

## Lab 14: Use OCI CLI commands to wrok with EXACS


**Key Objectives**:

As a application developer, DBA or DevOps user,

- Interact with Oracle Cloud Infrastructure resources using CLI

**[Click here to run Lab 14](OCI-CLI.md)**

## Lab 15: Automation with Terraform*


**Key Objectives**:

As a database or System admin,

- Deploy EXACS database using Terraform

**[Click here to run Lab 15](Terraform.md)**

## Lab 16: Build and deploy Python application stacks on EXACS


**Key Objectives**:

As an application developer,

- Learn how to deploy a python application and connect it your EXACS database instance

**[Click here to run Lab 16](BuildPythonApps.md)**


## Lab 17: - Build APEX applicaiton on EXACS


**Key Objectives**:

As an application developer, DBA or DevOps user,

- Access OCI autonomous database console and get URL for apex web cosole
- Create a VNC connection to developer client VM and access apex on your database
- Setup additional apex developer users

**[Click here to run Lab 17](APEX.md)**

## Appendix

**Common tools for windows Users**
**Finding the IP address of your Database*

**[Click here to access appendix](Appendix.md)**