# Repaso de todos los días

----------------------------

# WMI y CIM

## Conceptos
- CIM (Common Information Model) es un estándar abierto creado por la organización DMTF orientado a proveer una definición común para el intercambio de información entre sistemas, redes, aplicaciones y servicios.
  - https://github.com/jesusninoc/ClasesISO/blob/master/2021-04-31.md#get-ciminstance
- WMI (Windows Management Instrumentation) es la implementación de Microsoft de CIM, con la que se proveen métodos para consultar y modificar la configuración de una máquina Windows.
  - https://github.com/jesusninoc/ClasesISO/blob/master/2021-04-31.md#get-wmiobject
  - https://docs.microsoft.com/es-es/powershell/scripting/samples/getting-wmi-objects--get-ciminstance-?view=powershell-7.2
- CIM vs WMI
  - La respuesta simple es que puede usar los cmdlets de Instrumental de administración de Windows (WMI) o del Modelo de información común (CIM), pero existen algunas ventajas significativas al usar los cmdlets de CIM más nuevos.
  - CIM es un estándar abierto de Distributed Management Task Force (DMTF), con la última versión introducida en enero de 2016. CIM proporciona una definición común de información de gestión para sistemas, redes, aplicaciones y servicios, y permite extensiones de proveedores. WMI es la implementación de Microsoft de CIM para la plataforma Windows.
  - Get-WmiObject es uno de los cmdlets originales de PowerShell. (Como prueba rápida, ¿cuántos de los 137 cmdlets originales puede nombrar?). Se mejoró en PowerShell 2.0 cuando se introdujeron los otros cmdlets de WMI. En PowerShell 1.0, Get-WmiObject era el único cmdlet con la opción de acceder a otro sistema.
  - El gran inconveniente de los cmdlets de WMI es que utilizan DCOM para acceder a máquinas remotas. DCOM no es compatible con firewall, puede ser bloqueado por equipos de red y da algunos errores misteriosos cuando las cosas van mal.
  - Los cmdlets CIM aparecieron en PowerShell 3.0 como parte de la nueva API para trabajar con clases CIM, que se basa más en estándares.
  - La gran diferencia entre los cmdlets de WMI y los cmdlets de CIM es que los cmdlets de CIM usan WSMAN (WinRM) para conectarse a máquinas remotas.
  - Invoke-WmiMethod tiene la peculiaridad de que si proporciona los parámetros del método en el orden especificado por la documentación de WMI, a veces obtendrá un mensaje de error.
  - Invoke-CimMethod requiere una tabla hash de pares clave-valor donde Invoke-WmiMethod solo toma los valores de los parámetros. Invoke-CimMethod requiere escribir un poco más.

## Querys

### Procesos
* https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/#Arrancar_notepad_iniciando_una_instancia_mediante_WMI
* https://www.jesusninoc.com/04/27/arrancar-y-parar-un-proceso-con-cim-desde-powershell/

### Hardware
* https://www.jesusninoc.com/07/03/3-gestion-del-hardware-en-powershell/

#### Realizar un inventario utilizando CIM
```PowerShell
$ComputerSystem=Get-CimInstance Win32_ComputerSystem
$BaseBoard=Get-CimInstance Win32_BaseBoard
$BIOS=Get-CimInstance Win32_BIOS
$Processor=Get-CimInstance Win32_Processor
```

#### Realizar un inventario
* https://www.jesusninoc.com/03/22/obtener-informacion-sobre-el-hardware-de-un-equipo-creando-un-objeto-y-convertirlo-en-json-y-despues-lo-convierte-a-codigo-qr-por-ultimo-comprueba-y-lee-el-codigo-qr-generado/
