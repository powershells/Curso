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

    Start-Sleep -Seconds (10)
}
```

#### Ejercicio: crear un calendario
```PowerShell
foreach($dia in -100..100)
{
    mkdir (Get-Date).AddDays($dia).ToString("yyyy/MM/dd")
}
```
