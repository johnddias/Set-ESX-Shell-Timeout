# Set-ESXi-AccessTimeouts.ps1

This PowerShell script connects to a vCenter Server and sets timeout values for:

- **ESXi Shell (DCUI console)** via `UserVars.ESXiShellTimeOut`
- **SSH Shell sessions** via `UserVars.ESXiShellInteractiveTimeOut`

It supports both interactive and non-interactive usage, handles secure credential input, and can target a specific cluster or all clusters in the vCenter.

---

## 📋 Requirements

- PowerShell 5.1+ or PowerShell Core
- VMware PowerCLI (`Install-Module -Name VMware.PowerCLI`)
- Permissions to read and write advanced settings on ESXi hosts

---

## 🚀 Usage

### Interactive Mode

Run the script without parameters to be prompted for all required input:

```powershell
.\Set-ESXi-AccessTimeouts.ps1
