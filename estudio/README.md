# GESTIÓN DE USUARIOS Y GRUPOS

## **CMD**

### CREAR GRUPOS LOCALES
`net localgroup [nombre grupo] /add`

### CREAR USUARIO
`net user [nombre de usuario] [contraseña] /add`  
  
### DESHABILITAR USUARIO
`net user [nombre de usuario] /active:no` 

### CAMBIAR NOMBRE DE USUARIO
`net user [nombre de usuario] /fullname:["nombre de usuario"]`

### HABILITAR AL USUARIO
`net user [nombre de usuario] /active:yes`

  
## **WPS**

### CREAR GRUPOS LOCALES
`New-LocalGroup -Name ["nombre de grupo"]`

### CREAR USUARIO
`New-LocalUser -Name ["nombre de usuario"] -NoPassword`

### AÑADIR USUARIO A GRUPO
`Add-LocalGroupMember -Group ["nombre del grupo"] -Member ["nombre del usuario"]`

### LISTAR GRUPO Y USUARIOS
`Get-LocalGroupMember -Name ["nombre del grupo"]`

### DESHABILITAR USUARIO
`Disable-LocalUser -name ["nombre de usuario"]`

### CAMBIAR NOMBRE DE USUARIO
`Rename-LocalUser -Name ["nombre de usuario"] -NewName ["nuevo nombre"]`

### HABILITAR AL USUARIO
`Enable-LocalUser -Name ["nombre de usuario"]`

### ELIMINAR USUARIO
`Remove-LocalUser -Name ["nombre de usuario"]`

### ELIMINAR GRUPO
`Remove-LocalGroup -Name ["nombre del grupo"]`


# GESTIÓN DE PROCESOS

## **CMD**

### LISTAR PROCESOS DEL SISTEMA QUE OCUPEN MÁS DE 50KB DE MEMORIA
`tasklist /FI "MEMUSAGE gt 50"`

### EJECUTAR REINICIO AUTOMÁTICO A LAS 23:00 CON COMENTARIO
`shutdown /r /t 7200 /c "Reinicio programado`

### EJECUTAR EDGE, VER SU PID Y CERRARLO
`start microsoft-edge:`  

`tasklist /fi "imagename eq msedge.exe"`  

`taskkill /PID [PID] /f`


## **WPS**

### EJECUTAR EDGE CON VENTANA MAXIMIZADA
`Start-Process -filepath msedge.exe -WindowStyle maximized`

### EJECUTAR BLOC DE NOTAS ABRIENDO ARCHIVO RESOLUCIÓN DE NOMBRES
`Start-Process -FilePath notepad.exe -ArgumentList "C:\Windows\System32\drivers\etc\hosts"`


### PARAR UN PROGRAMA
`Stop-Process -Name [nombre de programa]`  

-Ejemplo: `Stop-Process -Name notepad`


# GESTIÓN DE SERVICIOS

## **CMD**
### DETENER Y DESHABILITAR LOS SIGUIENTES SERVICIOS:

#### AUDIO DE WINDOWS
`sc stop AudioSrv`  

`sc config AudioSrv start= disabled`
#### ARCHIVOS SIN CONEXIÓN
`sc stop CscService`  

`sc config CscService start= disabled`

### HABILITAR SERVICIO DE AUDIO DE WINDOWS
- Forma 1  
`sc config Audiosrv start-auto`  
- Forma 2  
`net start audiosrv`

### ARRANCAR EL SERVICIO DE AUDIO DE WINDOWS
`net start "AUDIO DE WINDOWS`

### HABILITAR EL SERVICIO ARCHIVOS SIN CONEXIÓN
`sc config "CsCService" start-=auto`

### ARRANCAR EL SERVICIO ARCHIVOS SIN CONEXIÓN
`net start "CsCService`

## **WPS**

### LISTAR LOS SERVICIOS QUE SE ENCUENTRAN DESHABILITADOS
`Get-Service | Where-Object -Property Status -eq stopped`

### LISTAR LOS SERVICIOS QUE SE ENCUENTRAN EN EJECUCCIÓN
` Get-Service | Where-Object -Property Status -eq running`

### Mostrar el servicio Administrador de usuarios junto con los servicios de los que depende
`Get-Service -name UserManager -DependentServices`

### Suspender el servicio Estación de trabajo
`Suspend-Service -name LanmanWorkstation`

### Reanudar el servicio Estación de trabajo
`Get-Service LanmanWorkstation`

### Parar  el  servicio  Instrumental  de Administración  de  Windows 
`Stop-Service -Name ["nombre de programa]`  

`Stop-Service -name Winmgmt -Force`

### Iniciar  el  servicio  Administrador  de  mapas  descargados  
`Start-Service MapsBroker`

### Reiniciar el servicio Administrador de cuentas Web
`Restart-Service TokenBroker`

### Establecer  arranque  automático  para  el  servicio  Agente  de  eventos  de tiempo
`Set-Service -name TimeBrokerSvc -StartupType Automatic`

### Deshabilitar el servicio Archivos sin conexión
`Set-Service -Name "CscServie" -Status Running -StartupType Disabled`  
