## Overview

The De-Bloat script removes unwanted Windows Store and Win32 apps, manufacturer bloat, and other components from Windows 10 and 11. This platform deployment script (`Deploy-RemoveBloat.ps1`) automates:

1. **Folder creation** for storing the main script and logs.
2. **Downloading** the latest `RemoveBloat.ps1` from GitHub.
3. **Executing** the downloaded script with optional parameters, including a custom whitelist.

By leveraging the `-customwhitelist` parameter, administrators can specify apps to retain while still benefiting from the latest version of the main script hosted on GitHub.

---

## Prerequisites

- Devices running **Windows 10** or **Windows 11**.
- **Intune** license and administrative access to create a PowerShell device script.
- Internet connectivity on target devices to download the script from GitHub.
- PowerShell execution policy set to **Bypass** during the script run.

---

## Files

| File                              | Description                                                  |
|-----------------------------------|--------------------------------------------------------------|
| `Deploy-RemoveBloat.ps1`          | The Intune platform script that downloads and runs `RemoveBloat.ps1`. |
| `RemoveBloat.ps1` (on GitHub)     | Main script hosted at:
|                                   | `https://github.com/Team-TiQHUB/Debloat-Windows-11/blob/main/RemoveBloat.ps1` |

---

## Using Custom Whitelist

To preserve specific apps during de-bloating, pass the `-customwhitelist` parameter to the main script. This should be a comma-separated list of AppX package names (or parts thereof).

## Script Parameters

| Parameter             | Type    | Description                                                                                         |
|-----------------------|---------|-----------------------------------------------------------------------------------------------------|
| `-customwhitelist`    | String  | Comma-separated list of AppX package names (partial or full) to exclude from removal.                |
| `-language`           | String  | (Optional) Override auto-detected language code (e.g., `en-US`, `fr-FR`).                            |
| `-logpath`            | String  | (Optional) Path to write the log file (default: `C:\ProgramData\Debloat\Debloat.log`).            |

---

## Logging and Output

- All actions performed by the De-Bloat script will be recorded in the log file at:

  ```text
  C:\ProgramData\Debloat\Debloat.log
  ```

- Review this log for details on removed packages, errors, and parameter values used.

---

## Troubleshooting

- **Script not downloading**: Ensure devices have internet access and can reach GitHub raw content URLs.
- **Execution policy errors**: Confirm the script runs with `-ExecutionPolicy Bypass` under the system context.
- **Whitelist not applied**: Verify `-customwhitelist` spelling and comma separation; check log for parameter recognition.

---

## Maintenance

- The deployment script always downloads the latest `RemoveBloat.ps1`, so updates on GitHub are automatically applied.
- Periodically review the GitHub repository for new parameters or enhancements:
  `https://github.com/Team-TiQHUB/Debloat-Windows-11`

---

