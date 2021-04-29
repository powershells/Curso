# Variables
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Variables

#### Ejercicios de PowerShell: realizar una copia de seguridad sobre los ficheros dll que tenemos el sistema (crear un fichero con información sobre los ficheros dll que se están ejecutando) realizar dicha operación cada 10 minutos, por lo tanto tenemos que crear cada 10 minutos una carpeta nueva
* https://www.jesusninoc.com/04/29/ejercicios-de-powershell-realizar-una-copia-de-seguridad-sobre-los-ficheros-dll-que-tenemos-el-sistema-crear-un-fichero-con-informacion-sobre-los-ficheros-dll-que-se-estan-ejecutando-realizar-dicha/

#### Ejercicios de PowerShell: crear un calendario
* https://www.jesusninoc.com/04/29/ejercicios-de-powershell-crear-un-calendario/

#### Ejercicios de PowerShell: crear una función que cifre una palabra y otra función que descifre la palabra cifrada
* https://www.jesusninoc.com/04/29/ejercicios-de-powershell-crear-una-funcion-que-cifre-una-palabra-y-otra-funcion-que-descifre-la-palabra-cifrada/

#### Ejercicios de PowerShell: adivinar un número entre 1 y 10
* https://www.jesusninoc.com/04/29/ejercicios-de-powershell-adivinar-un-numero-entre-1-y-10/

#### Ejercicios de PowerShell: poner en mayúscula la primera letra de un nombre y de los apellidos
* https://www.jesusninoc.com/04/29/ejercicios-de-powershell-poner-en-mayuscula-la-primera-letra-de-un-nombre-y-de-los-apellidos/

----------------

# Ejercicios de PowerShell: crear para cada proceso una carpeta con el nombre del proceso y dentro de cada carpeta creamos un fichero con toda la información del proceso, almacenar toda esta información cada 10 minutos

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

## - Ejecutar la función anterior cada 10 minutos
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
