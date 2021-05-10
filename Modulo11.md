# Repaso de todo el curso

## - Scripts
#### Ejercicios de PowerShell: crear un menú y realizar operaciones sobre procesos
```PowerShell
function mostramenu{
    Write-Host "0. Cerrar el programa"
    Write-Host "1. Arrancar proceso"
    Write-Host "2. Mostrar información de proceso"
    Write-Host "3. Matar proceso proceso"    
}

mostramenu

$opcion = Read-Host "Introduzca opción"

while($opcion -ne 0)
{
    switch($opcion)
    {
        0{exit}
        1{Start-Process notepad; pause}
        2{Start-Sleep -seconds 2; Get-Process -Name notepad; pause; break}
        3{Stop-Process -Name notepad; pause}
    }
    mostramenu
    $opcion = Read-Host "Introduzca opción"
}
```
#### Ejercicios de PowerShell: provocar un error y personalizar la respuesta al error
```PowerShell
Stop-Process -Name notepad -ErrorAction SilentlyContinue -ErrorVariable processerror3

if($processerror3)
{
    "No existe el proceso"
}
```
## - Características
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Caracteristicas                                                                                    
## - Variables
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Variables
## - Objetos
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Objetos
## - Canalización
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Canalizaciones
## - Operaciones
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Operaciones
## - Importar contenido
* https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#Importar_el_contenido_de_un_fichero_separado_por_comas
#### Ejercicios de PowerShell: leer operaciones de un fichero y realizarlas
```PowerShell
$operaciones = Import-Csv .\operaciones.txt -Delimiter ";"

foreach($operacion in $operaciones)
{
    if($operacion.OPERACION -eq "arrancar")
    {
        Start-Process $operacion.PARAMETRO
    }
    elseif($operacion.OPERACION -eq "verinfo")
    {
        Get-Process $operacion.PARAMETRO
    }
    elseif($operacion.OPERACION -eq "matar")
    {
        Stop-Process -name $operacion.PARAMETRO
    }
}
```
## - Procesos
* https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/
#### Ejercicios de PowerShell: ver qué usuario ejecuta un proceso
## - Funciones
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Funciones
#### Ejercicios de PowerShell: crear una función que indica el nombre del usuario que ejecuta un proceso (pasar el nombre de proceso como parámetro)
## - Usuarios
* https://www.jesusninoc.com/07/08/8-gestion-de-usuarios-en-powershell/
## - Red
* https://www.jesusninoc.com/07/09/9-gestion-de-la-red-en-powershell/
## - CIM
* https://www.jesusninoc.com/04/28/ejercicios-de-powershell-realizar-un-inventario-de-un-equipo-mediante-llamadas-cim/
## - Sofware
* https://www.jesusninoc.com/07/05/5-gestion-del-software-en-powershell/
#### Ejercicios de PowerShell: realizar una instalción si el software no está instalado
```PowerShell
if(Get-Package | Where-Object name -eq "posh-git")
{
    "Lo tengo instalado"
}
else
{
    Install-Package posh-git    
}
```
#### Ejercicios de PowerShell: realizar un inventario del software del equipo
```PowerShell
foreach($equipo in Get-Content .\equipos.txt)
{
    #Llamadas CIM
    $Sofware = Get-CimInstance Win32_product -ComputerName $equipo
 
    #Crear un objeto con todos los datos sobre el software (name, vendor y version)
    $var = [PSCustomObject]@{
        nombreequipo = $equipo
        nombre = $Sofware.Name
        fabricante = $Sofware.Vendor
        version = $Sofware.Version
    }
    $var
}
```
## - Rendimiento
* https://www.jesusninoc.com/07/10/10-gestion-del-rendimiento-en-powershell/
