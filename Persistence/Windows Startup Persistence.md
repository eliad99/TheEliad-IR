# Windows Startup Persistence Keys

## Startup Folders
Common locations for startup files:
- `C:\Users\[Username]\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
- `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup`

---

## Registry Run Keys
Executed at user/system logon:
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
- `HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce`

---

## Startup Folder Mapping (Explorer Keys)
Control startup folder paths:
- `HKCU\...\Explorer\UserShellFolders`
- `HKCU\...\Explorer\ShellFolders`
- `HKLM\...\Explorer\UserShellFolders`
- `HKLM\...\Explorer\ShellFolders`

---

## RunServices Keys (Boot Persistence)
Older persistence via services:
- `HKLM\...\RunServices`
- `HKLM\...\RunServicesOnce`
- `HKCU\...\RunServices`
- `HKCU\...\RunServicesOnce`

---

## Policy-Based Startup (GPO)
Startup apps via policy:
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run`
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run`
