# Repaso módulos 1 y 2
- Terminar con
    - https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/#Operaciones
- Introducir datos y leer
    - https://www.jesusninoc.com/02/05/read-and-write-host/ 
- Concepto de variable
    - https://www.jesusninoc.com/07/02/2-programacion-en-powershell/#Asignar_un_valor_a_una_variable_y_mostrar_el_valor_por_pantalla
- CSV
    - https://www.jesusninoc.com/11/12/read-comma-separated-values-file/
- Partir datos
    - https://www.jesusninoc.com/12/17/partir-una-cadena-en-partes-utilizando-split-en-powershell/
- Foreach ficheros
    - https://www.jesusninoc.com/06/03/como-funciona-el-bucle-foreach-en-powershell-paso-a-paso/

### Ejercicios:
#### Importar CSV
```PowerShell
$todoslosusuarios = Import-Csv .\usuarioscsv.txt

foreach($usuario in $todoslosusuarios)
{
    $usuario.Name
}
```

--------------------

# Cmdlets para la administración

## Usuarios
* https://www.jesusninoc.com/07/08/8-gestion-de-usuarios-en-powershell/

### Ejecutar PowerShell como administrador
* https://www.jesusninoc.com/04/28/ejecutar-powershell-como-administrador/

### Ejercicio de usuarios: crear usuarios leyendo del fichero usuarios.txt
* https://www.jesusninoc.com/04/28/ejercicios-de-powershell-crear-usuarios-leyendo-del-fichero-usuarios-txt/

### Ejercicio de usuarios: dependiendo de un valor (0 o 1) que hay en cada línea de un fichero que tiene usuarios, realizar la operación: 0 crear el usuario y 1 borrar el usuario
* https://www.jesusninoc.com/04/28/ejercicios-de-powershell-ejercicio-de-usuarios-sobre-usuarios-dependiendo-de-un-valor-0-o-1-que-hay-en-cada-linea-de-un-fichero-que-tiene-usuarios-realizar-la-operacion-0-crear-el-usuario-y-1-bo/

## Exchange
* https://www.jesusninoc.com/11/12/last-longon-time-display-name-exchange-online/

## Red
* https://www.jesusninoc.com/07/09/9-gestion-de-la-red-en-powershell/

#### Ejercicio de monitorización: obtener los identificadores de proceso de cada conexión TCP e indicar el nombre del proceso para cada identificador
* https://www.jesusninoc.com/04/28/ejercicios-de-powershell-obtener-los-identificadores-de-proceso-de-cada-conexion-tcp-e-indicar-el-nombre-del-proceso-para-cada-identificador/

#### Ejercicio de cliente-servidor UDP
* https://www.jesusninoc.com/02/12/enviar-una-ventana-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/

#### Enviar un script remotamente que reconoce palabras activando el micrófono del equipo mediante el protocolo UDP de un ordenador a otro desde PowerShell (hacerlo de forma simple y sencilla)
* https://www.jesusninoc.com/03/23/enviar-un-script-remotamente-que-reconoce-palabras-activando-el-microfono-del-equipo-mediante-el-protocolo-udp-de-un-ordenador-a-otro-desde-powershell-hacerlo-de-forma-simple-y-sencilla/
