# Repaso módulos anteriores

----------------

# Scripting

## Introducción
* https://www.jesusninoc.com/08/03/3-creacion-de-scripts-en-powershell-nivel-avanzado/

## Input
* https://www.jesusninoc.com/02/05/read-and-write-host/
* https://www.jesusninoc.com/02/17/pasar-parametros-en-scripts-de-powershell/

#### Ejercicios de PowerShell: GET y POST
```PowerShell
$postParams = @{'edad'=34
'nombre'="carlos"}

(Invoke-WebRequest "http://localhost/GetPost/exampleget.php?nombre=carlos&edad=34").content
(Invoke-WebRequest -Uri "http://localhost/GetPost/exampleget.php" -Method Post -Body $postParams).content
```

#### Ejercicios de PowerShell: crear un script en el que pasemos como parámetros el número de procesos que queremos listar y el orden en el que queremos ver el resultado
```PowerShell
Param(
    [int] $numero,
    [string] $tipodeorden
)

Invoke-Expression "Get-Process | select -First $numero | sort $tipodeorden"
```

### Ejercicios de PowerShell: crear un script que permite mostrar los procesos cuyo tiempo de consumo de CPU sea mayor que 10
```PowerShell
Param(
    [int] $valorconsumo
)

foreach($proceso in Get-Process)
{
    if($proceso.cpu -gt $valorconsumo)
    {
        $proceso.Name
    }
}
```

## Programación de scripts
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/

## Funciones

### Explica cómo agregar parámetros a funciones avanzadas
* https://docs.microsoft.com/es-es/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.1

### Funciones complejas
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Funciones

#### Ejercicio realizar un login
* https://www.jesusninoc.com/10/19/ejercicios-de-powershell-realizar-una-funcion-de-login/

#### Ejercicios de PowerShell: crear una función que valide un usuario leyendo el nombre y el password (en hash) correcto de un fichero. En el caso de que el login sea correcto se almacena la palabra "correcto" en un fichero y si es incorrecto el login se almacen la palabra "incorrecto" (añadir la fecha del intento)
```PowerShell
# Crear una función que valide un usuario leyendo el nombre
# y el password (en hash) correcto de un fichero. En el caso de que el login sea 
# correcto se almacena la palabra "correcto" en un fichero y si es incorrecto el login
# se almacen la palabra "incorrecto" (añadir la fecha del intento)

[Reflection.Assembly]::LoadWithPartialName("System.Web")

function validar
{
  param
  (
    [String[]]$usuario,$password
  )
  begin
  {
    $infodelogin = Get-Content .\login.txt
    $passusuariohash = [System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile($password, "SHA256")
  }
  process
  {
    if($usuario -eq $infodelogin.Split(",")[0] -and $passusuariohash -eq $infodelogin.Split(",")[1])
    {
        $ok = $true
    }
    else
    {
        $ok = $false
    }
  }
  end
  {
    if($ok -eq $true)
    {
        "correcto "+(Get-Date) | Out-File logcorrecto.txt -Append
    }
    else
    {
        "incorrecto "+(Get-Date) | Out-File logcorrecto.txt -Append
    }
  }
}
```

### Funciones dinámicas
* https://www.jesusninoc.com/02/27/crear-una-funcion-dinamica-en-powershell-que-obtiene-el-contenido-de-la-funcion-de-un-fichero-json-que-esta-en-un-servidor-web/

## Módulos
* https://www.jesusninoc.com/04/09/crear-un-modulo-en-powershell/
* https://www.jesusninoc.com/11/01/instalar-y-ejecutar-ssh-para-powershell/

#### Ejemplos de creación de módulos
```PowerShell
New-Module -ScriptBlock {function Hello {"Hello!"}}
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
```
