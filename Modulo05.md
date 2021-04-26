# Sistema de archivos
* https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/

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
