# Sistema de archivos
* https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/

#### Ejercicio: leer de un fichero nombres de ficheros y directorios y crearlos (solución switch y function avanzada, realizada por Cristian G.)
```PowerShell
# fichero, compras.txt
# directorio, pedidos

function GenerarItems($tipo){
    $tipo = $tipo.Split(",")
    switch($tipo[0]){
        'fichero'{
            if(New-Item $tipo[1] -ItemType File){
                Write-Host("Fichero creado: " + $tipo[1])
            }
            
        }
        'directorio'{
            if(New-Item $tipo[1] -ItemType Directory){
                Write-Host("Directorio creado: " + $tipo[1])
            }
        }
    }
}
$path = "C:\Users\cgil\Documents\PowerShell\Curso2021\Ejemplos\nombres.txt"

$lista = Get-Content $path 

foreach ($tipo in $lista){
    GenerarItems($tipo)
}
```

#### Ejercicio: leer de un fichero nombres de ficheros y directorios y crearlos (solución if simple)
```PowerShell
# fichero, compras.txt
# directorio, pedidos

foreach ($linea in Get-Content .\nombres.txt)
{
    if ($linea.Split(",")[0] -eq "fichero")
    {
        New-Item -Name $linea.Split(",")[1] -Value "hola"
    }
    elseif ($linea.Split(",")[0] -eq "directorio")
    {
        New-Item -Name $linea.Split(",")[1] -ItemType Directory
    }
    else
    {
        "otra cosa"
    }
}
```

#### Ejercicio: crear un disco virtual, ponerlo en funcionamiento y cifrar el contenido con BitLocker
```PowerShell
New-VHD -Path disc1.vhdx -SizeBytes 100mb
Mount-VHD .\disc1.vhdx
Get-Disk
Initialize-Disk -Number 1
New-Partition -DiskNumber 1 -UseMaximumSize -AssignDriveLetter
Get-Volume
Format-Volume -FileSystem NTFS -DriveLetter d 
Enable-BitLocker -MountPoint "d:" -RecoveryPasswordProtector -UsedSpaceOnly -Verbose
```

#### Ejercicio: de todos los procesos que se están ejecutando realizar el hash de cada uno de ellos
```PowerShell
foreach ($fichero in Get-Process | select name,path)
{
    Write-Host $fichero.name, (Get-FileHash $fichero.Path).Hash
}
```

#### Ejercicio: de todos los ficheros dll que se utilizando para ejecutar procesos realizar el hash de cada uno de ellos
```PowerShell
```

----------------------

# PSProviders y PSDrives

## PSProvider
### Definición
- Proveedores de datos que son mostradas en un formato entendible por PowerShell en la sesión actual.

#### Ver los proveedores disponibles
```PowerShell
Get-PSProvider
```
#### Ver si existe una función
* https://www.jesusninoc.com/04/16/ejercicios-de-powershell-ver-si-existe-una-funcion/

#### Registro de Windows
* https://www.jesusninoc.com/03/23/ver-informacion-en-el-registro-de-windows-sobre-las-variables-de-entorno/
* https://www.jesusninoc.com/05/07/ejecutar-la-informacion-que-se-encuentra-en-un-valor-binario-del-registro-de-windows/
* https://www.jesusninoc.com/02/11/artefactos/
* https://www.jesusninoc.com/10/03/crear-una-entrada-del-registro-desde-powershell-que-permita-ejecutar-siempre-un-programa-al-iniciar-la-sesion-de-un-usuario/

## PSDrives
### Definición
- Puede usar el comando New-PSDrive para agregar sus propias unidades de Windows PowerShell. Para obtener la sintaxis del cmdlet New-PSDrive, escriba un comando Get-Command con el parámetro Syntax.
* https://docs.microsoft.com/es-es/powershell/scripting/samples/managing-windows-powershell-drives?view=powershell-7.2

#### Crear recursos compartidos
* https://www.jesusninoc.com/02/16/ejercicios-de-powershell-crear-recursos-unidades-con-new-psdrive-de-para-varias-carpetas-compartidas-leyendo-de-un-fichero-las-rutas-compartidas-y-los-nombres-de-los-recursos-que-se-van-a-crear/
