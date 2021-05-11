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

#### Ejercicios de PowerShell: crear un script en el que pasamos como parámetros el número de procesos que queremos listar y el orden en el que queremos ver el resultado
* https://www.jesusninoc.com/05/05/ejercicios-de-powershell-crear-un-script-en-el-que-pasamos-como-parametros-el-numero-de-procesos-que-queremos-listar-y-el-orden-en-el-que-queremos-ver-el-resultado/

### Ejercicios de PowerShell: crear un script que permite mostrar los procesos cuyo tiempo de consumo de CPU sea mayor que 10
* https://www.jesusninoc.com/05/05/ejercicios-de-powershell-crear-un-script-que-permite-mostrar-los-procesos-cuyo-tiempo-de-consumo-de-cpu-sea-mayor-que-10/

## Programación de scripts
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/

## Funciones

### Explica cómo agregar parámetros a funciones avanzadas
* https://docs.microsoft.com/es-es/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.1

### Funciones complejas
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Funciones

#### Ejercicio realizar un login
* https://www.jesusninoc.com/10/19/ejercicios-de-powershell-realizar-una-funcion-de-login/

#### Ejercicios de PowerShell: crear una función que valide un usuario leyendo el nombre y el password (en hash) correcto de un fichero. En el caso de que el login sea correcto se almacena la palabra "correcto" en un fichero y si es incorrecto el login se almacene la palabra "incorrecto" (añadir la fecha del intento)
* https://www.jesusninoc.com/05/05/ejercicios-de-powershell-crear-una-funcion-que-valide-un-usuario-leyendo-el-nombre-y-el-password-en-hash-correcto-de-un-fichero-en-el-caso-de-que-el-login-sea-correcto-se-almacena-la-palabra-cor/

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

## DSC
DSC es una plataforma de administración de PowerShell que le permite administrar su infraestructura de desarrollo y TI con configuración como código.
* https://docs.microsoft.com/es-es/powershell/scripting/dsc/overview/dscforengineers?view=powershell-7.2
* https://docs.microsoft.com/es-es/powershell/scripting/dsc/getting-started/wingettingstarted?view=powershell-7.2
* https://docs.microsoft.com/es-es/powershell/scripting/dsc/configurations/write-compile-apply-configuration?view=powershell-7.2
* https://docs.microsoft.com/es-es/powershell/scripting/dsc/pull-server/pullserversmb?view=powershell-7.2
