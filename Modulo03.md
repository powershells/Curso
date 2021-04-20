# Repaso módulos 1 y 2
- Terminar con
    - https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Operaciones
- Introducir datos y leer
    - https://www.jesusninoc.com/02/05/read-and-write-host/ 
- CSV
    - https://www.jesusninoc.com/11/12/read-comma-separated-values-file/
- Partir datos
    - https://www.jesusninoc.com/12/17/partir-una-cadena-en-partes-utilizando-split-en-powershell/
- Foreach ficheros
    - https://www.jesusninoc.com/06/03/como-funciona-el-bucle-foreach-en-powershell-paso-a-paso/

--------------------

# Cmdlets para la administración

## Usuarios
* https://www.jesusninoc.com/07/08/8-gestion-de-usuarios-en-powershell/

## Exchange
* https://www.jesusninoc.com/11/12/last-longon-time-display-name-exchange-online/

## Directorio Activo
* https://www.jesusninoc.com/05/03/creacion-masiva-de-usuarios-en-el-directorio-activo-con-powershell-parte-1/
* https://www.jesusninoc.com/05/09/creacion-masiva-de-usuarios-en-el-directorio-activo-con-powershell-parte-2/

### Crear usuarios en AD, carpeta compartida y asignar permisos
```PowerShell
foreach($usuario in Get-Content .\usuarios.txt)
{
    $usuario
    $password = (ConvertTo-SecureString "Alum4dos" -AsPlainText -force)
    New-ADUSer -Name $usuario -Sam $usuario -Path "OU=asir,DC=andel,DC=local" -AccountPassword $password -Enable $true
    $HomeDirectory = ("\\localhost\log\" + $usuario)
    mkdir $HomeDirectory
    $usuariomaspermiso = $usuario + ":F"
    $rutantfs = "C:\Users\Administrador\Desktop\log\" + $usuario
    icacls $rutantfs /grant $usuariomaspermiso
    Start-Sleep -Seconds 5
}
```

## Red
* https://www.jesusninoc.com/07/09/9-gestion-de-la-red-en-powershell/

#### Ejercicio de cliente-servidor UDP
* https://www.jesusninoc.com/02/12/enviar-una-ventana-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/

#### Enviar un script remotamente que reconoce palabras activando el micrófono del equipo mediante el protocolo UDP de un ordenador a otro desde PowerShell (hacerlo de forma simple y sencilla)
* https://www.jesusninoc.com/03/23/enviar-un-script-remotamente-que-reconoce-palabras-activando-el-microfono-del-equipo-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/

## Otros cmdlets
* https://www.jesusninoc.com/07/06/6-virtualizacion-en-powershell/
* https://www.jesusninoc.com/11/01/instalar-y-ejecutar-ssh-para-powershell/
* https://www.jesusninoc.com/11/12/last-longon-time-display-name-exchange-online/
