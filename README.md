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
```

### Semi-Automated

Provide most parameters but securely prompt for password:

```powershell
.\Set-ESXi-AccessTimeouts.ps1 `
    -vCenter vcsa.lab.local `
    -User administrator@vsphere.local `
    -ShellTimeoutMinutes 30 `
    -SshTimeoutMinutes 60 `
    -ClusterName "All"
```

### Fully Automated

Provide all inputs up front (note: only use plain text passwords if you're in a secure context):

```powershell
.\Set-ESXi-AccessTimeouts.ps1 `
    -vCenter vcsa.lab.local `
    -User administrator@vsphere.local `
    -Password VMware123! `
    -ShellTimeoutMinutes 30 `
    -SshTimeoutMinutes 60 `
    -ClusterName "ProdCluster"
```

---

## 🔧 Settings Applied

| Setting Name                            | Affected Component | Description                            |
|----------------------------------------|---------------------|----------------------------------------|
| `UserVars.ESXiShellTimeOut`            | DCUI shell          | Timeout for the local ESXi Shell       |
| `UserVars.ESXiShellInteractiveTimeOut` | SSH shell           | Timeout for remote SSH sessions        |

Timeouts are input in **minutes**, but stored in **seconds** on the host.

---

## 📄 Files Included

- `Set-ESXi-AccessTimeouts.ps1` – Main script
- `README.md` – Usage documentation
- `LICENSE` – MIT License

---

## 📬 Contributions

Feel free to fork, submit issues, or contribute enhancements via PR.

---

## 📝 License

MIT License. See `LICENSE` file for details.
