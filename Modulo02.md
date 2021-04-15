# Cmdlets para la administración
- Directorio Activo
- Red (ejercicio de cliente-servidor UDP)
- Otros cmdlets

------------------

## Directorio Activo
* https://www.jesusninoc.com/active-directory/

#### Ejemplo de control a usuario que inicia sesión
```PowerShell
$hora = Get-Date -Format 'HH'

if ($hora -ge 19 -and $hora -lt 22 -and $env:USERNAME -match "adminfp")
{
    "entre 20 y 22" | Out-File \\192.168.1.1\fichero.txt
}
else
{
    "fallo" | Out-File \\192.168.1.1\fichero.txt 
}
```

## Red
* https://www.jesusninoc.com/07/09/9-gestion-de-la-red-en-powershell/

#### Ejercicio de cliente-servidor UDP
* https://www.jesusninoc.com/02/12/enviar-una-ventana-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/

## Otros cmdlets
```PowerShell
Get-Command *
```
