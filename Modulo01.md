# Introducción a PowerShell

## Conocimientos previos
- Programación (lenguajes, nivel, aprendido o utilizado)
- PowerShell
- Sistemas operativos (Windows, macOS, Linux)
- Bases de datos
- Redes
- Automatización
- Seguridad

## Motivación

* https://www.infodll.com/
* https://www.jesusninoc.com/04/17/como-funciona-un-bot-como-crear-un-bot-muy-simple-en-2-minutos/
* https://www.jesusninoc.com/nutrition/
* https://www.jesusninoc.com/seo/
* https://www.jesusninoc.com/mercados-y-cotizaciones/
* https://www.jesusninoc.com/recognition/

## Características
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Caracteristicas

### Core
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Introduccion

### ISE
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Entorno_de_scripting_integrado_ISE
#### Ejercicios sobre procesos
* https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/#Ejemplos

## Cmdlets
### Sintaxis
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Entorno_de_scripting_integrado_ISE
### ¿Qué es un objeto?
* https://www.jesusninoc.com/02/08/crear-objetos-en-powershell-5/
* https://www.jesusninoc.com/02/13/trabajar-con-objetos-en-powershell/
### ¿Qué es un alias?
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Alias

#### Ejercicio sobre procesos y objetos: crear un objeto que contenga la siguiente información:
- Listar todos los procesos
- Listar los 5 procesos que más consumen
- Listar los 5 procesos que menos consumen
- Listar los fabricantes de los procesos
- Crear un método que mate el proceso Calculator

```PowerShell
#Clase InformacionProcesos con propiedades
class InformacionProcesos
{ 
  $todoslosprocesos
  $los5masconsumo
  $los5menosconsumo
  $fabricantesdeprocesos
}

#Crear objeto InformacionProcesos de la clase InformacionProcesos
$informacion1 = New-Object -TypeName InformacionProcesos

$informacion1.todoslosprocesos = Get-Process 
$informacion1.los5masconsumo = Get-Process | Sort-Object cpu | Select-Object name,cpu -Last 5
$informacion1.los5menosconsumo = Get-Process | Sort-Object cpu | Select-Object name,cpu -First 5
$informacion1.fabricantesdeprocesos = Get-Process | Select-Object Company

$informacion1 | Add-Member ScriptMethod MatarProceso {(Get-Process -Name Calculator).kill()}

$informacion1.fabricantesdeprocesos

$informacion1.MatarProceso()
```

### Encontrar cmdlets
* https://www.jesusninoc.com/get-command/
* https://www.jesusninoc.com/09/05/obtener-el-alias-del-cmdlet-get-content-mediante-get-command-y-abrir-un-fichero-ofuscacion-en-powershell/

## Mezclar con...
### WSL
* https://www.jesusninoc.com/03/26/libro-de-powershell-nivel-avanzado-libro-gratis-de-powershell-tutorial-gratis-de-powershell/
* https://www.jesusninoc.com/03/30/crear-un-codigo-de-barras-en-bash-mediante-wsl-desde-powershell/
* https://www.jesusninoc.com/03/22/crear-un-codigo-qr-mediante-un-comando-en-bash-con-wsl-desde-powershell-y-codificarlo-despues-en-base64/
### ADB
* https://www.jesusninoc.com/04/17/simular-el-pulsado-de-numeros-en-android-mediante-adb-a-traves-de-powershell/
* https://www.jesusninoc.com/04/17/enviar-un-mensaje-sms-en-android-con-adb/
### Python
* https://www.jesusninoc.com/03/24/crear-y-ejecutar-un-script-de-python-desde-powershell/
* https://www.jesusninoc.com/03/24/detectar-las-coordenadas-de-una-imagen-o-un-texto-dentro-de-una-captura-de-pantalla-en-python-llamar-al-script-de-python-desde-powershell-y-hacer-clic-en-dicha-posicion/
### PHP
* https://www.jesusninoc.com/12/19/ejecutar-codigo-php-desde-powershell-utilizando-variables-en-powershell/
### Node.js
* https://www.jesusninoc.com/08/11/11-node-js-y-powershell/
* https://www.jesusninoc.com/03/22/listar-procesos-mediante-un-cmdlet-de-powershell-con-node-js-crear-el-script-desde-powershell/
* https://www.jesusninoc.com/03/21/explicacion-de-todos-los-pasos-para-apagar-y-encender-la-bombilla-inteligente-tp-link-kasa-regulable-kl110-desde-powershell/
* https://www.jesusninoc.com/04/17/obtener-el-token-y-el-deviceid-del-enchufe-inteligente-tp-link-wi-fi-hs100-desde-node-js-y-mostrarlo-en-powershell/
