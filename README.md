<div align="center">

# Nick

### Production Infrastructure & Systems Administration

![Windows Server](https://img.shields.io/badge/Windows_Server_2025-0078D4?style=flat-square&logo=windows11&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active_Directory-1F6FEB?style=flat-square)
![Proxmox VE](https://img.shields.io/badge/Proxmox_VE-E57000?style=flat-square&logo=proxmox&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

</div>

## Production work

| Project | Real infrastructure | Why this design |
| --- | --- | --- |
| **Fundacja Integracja poprzez Sztukę** | Dell PowerEdge · Proxmox VE · Windows Server 2025 · AD DS/DNS/GPO · LAPS · BitLocker · Ubuntu/Docker · VM backups · rollback · alerts · Tailscale | Hypervisor stays clean; workloads run in isolated VMs. Management access is private rather than exposed to the Internet. |
| **Tealista** | Cloudflare · Render · MongoDB Atlas · Cloudinary · GitHub Actions · self-hosted runner · deployment verification · production hardening | Customer-facing commerce stays on managed cloud services. Owned infrastructure is used where it reduces cost without increasing customer-facing risk. |

## Architecture

```mermaid
flowchart LR
    A[Admin devices] --> T[Tailscale]
    T --> P[Proxmox VE]

    P --> W[Windows Server 2025\nAD DS · DNS · GPO]
    P --> U[Ubuntu VM\nDocker · Web]
    P --> C[CI workload\nSelf-hosted runner]

    I[Internet] --> CF[Cloudflare]
    CF --> U
    CF --> R[Managed application platform]
    R --> DB[(Managed data services)]
```

## Hands-on

**Windows:** AD DS · DNS · OU/groups · GPO · Windows LAPS · BitLocker · SCCM · troubleshooting  
**Infrastructure:** Proxmox VE · VM isolation · storage · networking · backup/restore  
**Linux:** Ubuntu Server · Docker / Compose · systemd · deployment / rollback  
**Automation:** PowerShell · GitHub Actions · self-hosted runners

## Public evidence

- **[PowerShell Corporate Automation](https://github.com/myducks/powershell-corp-automation)** — reusable Windows administration tooling
- **[Tealista Technical Case Study](https://github.com/myducks/tealista-case-study)** — architecture, commerce, CI/CD, security and production engineering

## Security

- Management plane is not publicly exposed
- No production credentials, tokens, internal addresses or recovery secrets are published
- Separate workloads are isolated in separate VMs
- Backup/recovery is independent from application deployment

> **Current trade-off:** one physical virtualization host remains a single point of failure. The current mitigation is backup-based recovery rather than high availability.

---

**Target:** System Administrator · Windows Administrator · IT Administrator · Infrastructure Support
