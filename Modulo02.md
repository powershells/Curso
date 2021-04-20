# Pipeline

## ¿Cómo funcionan las canalizaciones?
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Canalizaciones

## Operaciones en PowerShell
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Operaciones

### Ejercicio sobre operaciones: pedir al usuario los siguientes valores: valor para ordenar, qué proceso seleccionar, cómo vamos a agrupar
```PowerShell
Get-Process -Name (Read-Host "introduzca nombre de proceso") | group (Read-Host "introduzca tipo para agrupar") | sort (Read-Host "ordenar por qué") 
```

### Ejercicio sobre operaciones: leer de un fichero lo quiere el usuario ordenar, seleccionar y agrupar
```PowerShell
(Get-Content .\informacion.txt)[0]
(Get-Content .\informacion.txt)[1]
(Get-Content .\informacion.txt)[2]

Get-Process -Name (Get-Content .\informacion.txt)[0] | group (Get-Content .\informacion.txt)[0] 
```
