# Crear y recibir un job

```PowerShell
Start-Job -ScriptBlock {ps}

Get-Job -Id 1

Receive-Job -Id 1
```
