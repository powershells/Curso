# Repaso módulo 3

## Directorio Activo
* https://www.jesusninoc.com/05/16/utilizar-un-filtro-ldap-para-localizar-un-usuario/
* https://www.jesusninoc.com/05/06/check-last-login-time-ad-users/
* https://www.jesusninoc.com/05/03/creacion-masiva-de-usuarios-en-el-directorio-activo-con-powershell-parte-1/
* https://www.jesusninoc.com/05/09/creacion-masiva-de-usuarios-en-el-directorio-activo-con-powershell-parte-2/

#### Ejercicio: crear usuarios en AD, carpeta compartida y asignar permisos
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

### Unidades organizativas
* https://www.jesusninoc.com/06/18/verificar-si-existe-una-unidad-organizativa-con-powershell/
* https://www.jesusninoc.com/05/22/ejercicios-de-powershell-crear-una-ou-unidad-organizativa/

### Políticas de grupo
* https://github.com/jesusninoc/ClasesISO/blob/master/2021-04-22.md

## Otros cmdlets
* https://www.jesusninoc.com/07/06/6-virtualizacion-en-powershell/
* https://www.jesusninoc.com/11/01/instalar-y-ejecutar-ssh-para-powershell/
* https://www.jesusninoc.com/11/12/last-longon-time-display-name-exchange-online/

## Ayuda
* https://www.jesusninoc.com/10/16/introduccion-a-los-cmdlets-comandos/
## Mail
* https://www.jesusninoc.com/03/30/enviar-un-mail-desde-powershell-utilizando-el-smtp-de-outlook/
## Scraping
* https://www.jesusninoc.com/01/25/extraer-informacion-de-sitios-web/
* https://www.jesusninoc.com/06/15/insertar-en-una-base-de-datos-las-noticias-de-una-pagina-web-crear-la-base-de-datos-y-la-tabla/

-------------------

# Funciones
* https://www.jesusninoc.com/10/14/funciones-con-parametros-y-sin-parametros/
## Función autocompletar (ejecutar en shell)
* https://www.jesusninoc.com/04/25/crear-una-funcion-en-powershell-que-permita-autocompletar/

# Pipeline avanzado

## Pasar parámetros
* https://www.jesusninoc.com/04/15/ejercicios-de-powershell-usos-de-los-parametros-valuefrompipeline/

## PassThru
* https://www.jesusninoc.com/04/15/ejercicios-de-powershell-uso-de-passthru/
