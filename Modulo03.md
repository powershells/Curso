# Repaso módulos 1 y 2
- Terminar con
    - https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Operaciones
- Introducir datos y leer
    - https://www.jesusninoc.com/02/05/read-and-write-host/ 
- Concepto de variable
    - https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Asignar_un_valor_a_una_variable_y_mostrar_el_valor_por_pantalla
- CSV
    - https://www.jesusninoc.com/11/12/read-comma-separated-values-file/
- Partir datos
    - https://www.jesusninoc.com/12/17/partir-una-cadena-en-partes-utilizando-split-en-powershell/
- Foreach ficheros
    - https://www.jesusninoc.com/06/03/como-funciona-el-bucle-foreach-en-powershell-paso-a-paso/

### Ejercicios:
#### Importar CSV
```PowerShell
$todoslosusuarios = Import-Csv .\usuarioscsv.txt

foreach($usuario in $todoslosusuarios)
{
    $usuario.Name
}
```

--------------------

# Cmdlets para la administración

## Usuarios
* https://www.jesusninoc.com/07/08/8-gestion-de-usuarios-en-powershell/

### Ejecutar PowerShell como administrador
* https://adamtheautomator.com/powershell-run-as-administrator/
```PowerShell
Powershell.exe -Command "& {Start-Process Powershell_ise.exe -Verb RunAs}"
```

### Ejercicio de usuarios: crear usuarios leyendo del fichero usuarios.txt
#### Contenido del fichero
```
juan,holapepe
diego,holapepe
```
#### Script
```PowerShell
foreach ($usuario in Get-Content .\usuarios.txt)
{
    $pass = ConvertTo-SecureString $usuario.Split(",")[1] -AsPlainText -Force
    New-LocalUser -Name $usuario.Split(",")[0] -Password $pass
    # $Error[0] | Out-File logusuerro.txt
}
```

### Ejercicio de usuarios: dependiendo de un valor (0 o 1) que hay en cada línea de un fichero que tiene usuarios, realizar la operación: 0 crear el usaurio y 1 borrar el usuario
#### Contenido del fichero
```
0,juan,holapepe
0,diego,holapepe
1,diego
```
#### Script
```PowerShell
foreach ($linea in Get-Content .\usuarios.txt)
{
    if($linea.Split(",")[0] -eq 1)
    {
        Remove-LocalUser $linea.Split(",")[1] -WhatIf
    }
    else
    {
        $pass = ConvertTo-SecureString $linea.Split(",")[2] -AsPlainText -Force
        New-LocalUser -Name $linea.Split(",")[1] -Password $pass -WhatIf
    }
}
```

## Exchange
* https://www.jesusninoc.com/11/12/last-longon-time-display-name-exchange-online/

## Red
* https://www.jesusninoc.com/07/09/9-gestion-de-la-red-en-powershell/

#### Ejercicio de monitorización: obtener los identificadores de proceso de cada conexión TCP e indicar el nombre del proceso para cada identificador
```PowerShell
foreach ($conexion in Get-NetTCPConnection | Select-Object RemoteAddress, OwningProcess)
{
    Write-Host $conexion.RemoteAddress, (Get-Process -Id $conexion.OwningProcess).name
}
```

#### Ejercicio de cliente-servidor UDP
* https://www.jesusninoc.com/02/12/enviar-una-ventana-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/

#### Enviar un script remotamente que reconoce palabras activando el micrófono del equipo mediante el protocolo UDP de un ordenador a otro desde PowerShell (hacerlo de forma simple y sencilla)
* https://www.jesusninoc.com/03/23/enviar-un-script-remotamente-que-reconoce-palabras-activando-el-microfono-del-equipo-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/
