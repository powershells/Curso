# Acceso remoto

## Configurar acceso remoto en cliente
```PowerShell
Enable-PSRemoting -Force
Set-Item wsman:\localhost\client\trustedhosts *
Restart-Service WinRM
```
