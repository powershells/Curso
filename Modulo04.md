# Pipeline

```PowerShell
function mostrarnombre()
{
    param([Parameter(ValueFromPipeline)]$amigo)
    Write-Host "mensaje"$amigo
}

"hola juan" | mostrarnombre
"hola juan" ; mostrarnombre
```

# PassThru
```PowerShell
Get-Process | Out-GridView -PassThru | Stop-Process
```
