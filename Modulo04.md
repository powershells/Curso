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
