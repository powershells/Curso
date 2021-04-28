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
* https://www.jesusninoc.com/04/28/ejercicio-de-powershell-leer-de-un-fichero-nombres-de-ficheros-y-directorios-y-crearlos-solucion-if-simple/

#### Ejercicio: crear un disco virtual, ponerlo en funcionamiento y cifrar el contenido con BitLocker
* https://www.jesusninoc.com/04/28/ejercicio-de-powershell-crear-un-disco-virtual-ponerlo-en-funcionamiento-y-cifrar-el-contenido-con-bitlocker/

#### Ejercicio: de todos los procesos que se están ejecutando realizar el hash de cada uno de ellos
* https://www.jesusninoc.com/04/28/ejercicio-de-powershell-de-todos-los-procesos-que-se-estan-ejecutando-realizar-el-hash-de-cada-uno-de-ellos/

#### Ejercicio: de todos los ficheros dll que se están utilizando para ejecutar procesos realizar el hash de cada uno de ellos
* https://www.jesusninoc.com/04/28/ejercicio-de-powershell-de-todos-los-ficheros-dll-que-se-estan-utilizando-para-ejecutar-procesos-realizar-el-hash-de-cada-uno-de-ellos/

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

------------------

# Ejercicio integrador: crear un usuario con su contraseña, crear una carpeta para el usuario, compartir esa carpeta y añadir en esa carpeta un fichero con los hash de todos los procesos que se están ejecutando y otro fichero con los hash de los todos los ficheros dll. Todos los valores que necesitamos están escritos en un fichero

## - Crear usuario con contraseña leyendo de un fichero utilizando una función, crear una carpeta para el usuario y compartir

```PowerShell
# Fichero de ejemplo:
# pepito, P$aswo12

function crearusuario($fichero)
{
    foreach ($usuario in Get-Content $fichero)
    {
        $pass = ConvertTo-SecureString $usuario.Split(",")[1] -AsPlainText -Force
        New-LocalUser -Name $usuario.Split(",")[0] -Password $pass
        New-Item -Name $usuario.Split(",")[0] -ItemType Directory
        New-SmbShare -Name fso2 -Path ("C:\Users\juan\"+$usuario.Split(",")[0]) -FullAccess administrador,todos
        New-PSDrive -Name rutafso3 -PSProvider FileSystem -Root \\localhost\fso3
    }
}

crearusuario .\usuarios.txt
```

## - Hash de los programas que se están ejecutando

```PowerShell
function hashprogramas()
{
    foreach ($fichero in Get-Process | select name,path)
    {
        $fichero.name, (Get-FileHash $fichero.Path).Hash
    }
}

Set-Location rutafso3:\
hashprogramas | Out-File resultado.txt
```

## - Hash de todos los ficheros dll

```PowerShell
function hashdll()
{
    foreach ($fichero in ((Get-Process).Modules.FileName | group).name)
    {
        Get-FileHash $fichero | select name,hash
    }
}

Set-Location rutafso3:\
hashdll | Out-File resultadodll.txt
```
