
## Description
- This file contains all works I have contributed in my job at L&T

## Format
[date time] name@dept >> Title - work done

## Logs
**[05/09/25 09:16] varun@backend >>** Metadata info to iFrame - aded InfoName tag and Techname tag infromation to displayed name of xml doc file tkinter iframe in s1kd_PMC.py program (Advanced PM Content Editor).

**[18/09/25 15:11] varun@devops >>** Deployed the Taiga instance and Gitlab instance on self-hosted server

**[18/09/25 16:30] varun@backend >>** reinstalled PostgreSQL to reset default creds. Started work on `ietm-ts-search`.
```bash
# postgres password set temp
username: postgres
password: postgres
```

**[19/09/25 14:30] varun@backend >>** IETM: Fixed indexing and English analyzer (tokenization algorithm) of `ietm` data

**[19/09/25 15:45] varun@backend >>** IETM: Implemented Elastic Search features: fuzzy, Boolean, phrase and keyword. Rewrote entire Elastic Searching controller

**[20/09/25 09:40] varun@Infra >>** Researched Backup solutions and installed and successfully made snapshots and scheduled backups to remote NAS using [[Kopia]]

**[20/09/25 15:15] varun@Infra >>** Successfully installed [[Kopia]] Server CLI for centralized backups on LAN server (GPU) PC and created backup repo

**[22/09/25 17:05] varun@Infra >>** configured [[Kopia]] Server Service on Server  and took backups 2 computers to centralized server. [[Kopia]] backups POC completed

**[23/09/25 12:03] varun@Documentation >>** wrote down Kopia Server Setup and policy creation in detail into a markdown.

**[23/09/25 17:10] varun@Documentation >>** Completed creating SOP for Kopia Server Setup.

**[24/09/25 10:30] varun@Documentation >>** Completed creating SOP for Kopia Client Setup.

**[24/09/25  17:20] varun@Infra >>** Created Docker Image for running Kopia Server as a container.

**[25/09/25 12:10] varun@Infra >>** Installed Linux (Pop!OS) on work machine. Windows 11 not suitable for development work.

**[01/10/25 10:15] varun@Infra >>** Restored broken bootloader of PC and installed Omarchy Linux successfully.

**[03/10/25 12:00] varun@Frontend >>** created ImageSideBar component for IETM project

**[03/10/25 17:05] varun@DevOps >>** containerized IETM project (both back-end (+postgres +elasticsearch), front-end )

**[04/10/25 10:00] varun@DevOps >>** created and debugged docker-entrypoint shell scripts for IETM Dockerization. All docker-compose services working correctly now.

**[04/10/25 16:13] varun@backend >>** built basic API structures in nest framework. Tested with postman REST API client

**[07/10/25 14:00] varun@Infra >>** deployed backup software kopia on 2 servers and 7 client machines at MD Dockyard office.

**[08/10/25 16:30] varun@backend >>** containerized lms-backend including core stack components: Nestjs, PostgreSQL and redis.

**[09/10/25 17:15] varun@backend >>** Integrated PrismaORM into docker-compose setup. It was NOT easy. generating client and running migrations still pending on image.