# Variables
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Variables

#### Ejercicio: realizar una copia de seguridad sobre los ficheros dll que tenemos el sistema (crear un fichero con información sobre los ficheros dll que se están ejcutando) realizar dicha operación cada 10 minutos, por lo tanto tenemos que crear cada 10 minutos una carpeta nueva
```PowerShell
for(1)
{
    $fecha = Get-Date
    $nombre = [String]$fecha.Year + [String]$fecha.Month + [String]$Fecha.Day + "-" + [String]$fecha.Hour + [String]$fecha.Minute + [String]$fecha.Second

    New-Item -ItemType Directory -Name $nombre

    # Redirección
    # (Get-Process).Name > ($nombre+"\dlls.txt")

    # Con Out-File accediendo a la carpeta
    # Set-Location $nombre
    # (Get-Process).Name | Out-File dlls.txt
    # Set-Location ..
    
    # Con Out-File
    (Get-Process).Name | Out-File -FilePath ($nombre+"\prueba.txt")

    Start-Sleep -Seconds (10*60)
}
```

#### Ejercicio: crear un calendario
```PowerShell
foreach($dia in -100..100)
{
    mkdir (Get-Date).AddDays($dia).ToString("yyyy/MM/dd")
}
```

#### Ejercicio: crear una función que cifre una palabra y otra función que descifre la palabra cifrada
```PowerShell
function cifrar( $array )
{
    $palabracifrada = foreach($num in 0..($array.Length-1))
    {
        [char]([Int]$array[$num]+1)
    }
    $palabracifrada -join ""
}

$cifrada = cifrar hola

function descifrar( $cifrada )
{
    $palabradescifrada = foreach($num in 0..($cifrada.Length-1))
    {
        [char]([Int]$cifrada[$num]-1)
    }
    $palabradescifrada -join ""
}

descifrar $cifrada
```

#### Ejercicio: adivinar un número entre 1 y 10
``` PowerShell
$adivinar = Get-Random (1..10)

for(1)
{
    $numerouser = Read-Host "introduzca número: "
    if($numerouser -eq $adivinar)
    {
        "has acertado"
        break;
    }
    else
    {
        "no has acertado"
    }
}
```

#### Ejercicio: poner en mayúscula la primera letra de un nombre y de los apellidos
``` PowerShell
$palabra = " JUAN IglesiaS "
$palabra = $palabra.ToLower().Trim()
$palabras = $palabra.Split(" ")
$resultado = foreach ($cadapalabra in $palabras)
{
    $cadapalabra.substring(0,1).ToUpper()+$cadapalabra.substring(1).ToLower()
}
$resultado -join " "
```

----------------

# Ejercicio integrador: crear para cada proceso una carpeta con el nombre del proceso y dentro de cada carpeta creamos un fichero con toda la información del proceso, almacenar toda esta información cada 10 minutos

## - Función crea nombre de proceso y dentro de cada carpeta fichero con toda la información del proceso
``` PowerShell
function crear()
{
    foreach ($proceso in (Get-Process).Name)
    {
        mkdir $proceso -Force
        Get-Process -Name $proceso > ($proceso+"\informacion.txt")
    }
}
```

##- Ejecutar la función anterior cada 10 minutos
``` PowerShell
for(1)
{
    $fichero = (Get-Date).ToString("yyyyMMddhhmmss")
    mkdir $fichero
    cd $fichero
    crear
    cd ..
    Start-Sleep -Seconds (10*60)
}
```
