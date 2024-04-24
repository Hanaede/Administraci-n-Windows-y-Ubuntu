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

### VER USUARIO
`Get-Localuser -Name ["nombre de usuario"]`

### MODIFICAR USUARIO
`Set-LocalUser -Name ["nombre de usuario"] {parámetros}`


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
`Resume-Service LanmanWorkstation`

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




# LINUX

## GESTIÓN USUARIOS

### USUARIO ESTANDAR
#### Escribir el comando para crear el usuario estándar usuario33 con nombre completo “Usuario 33”, creando su directorio personal con el mismo nombre de usuario y asignándole la shell bash.

`sudo useradd -d /home/usuario33 -m -s /bin/bash -c "Usuario 33" usuario33`  

`sudo passwd usuario33`  

### USUARIO SISTEMA

#### Crear el usuario de sistema sistema55 con nombre completo “Usuario de sistema 55”, con id de usuario correspondiente a las cuentas del sistema, sin directorio personal y con la shell sh.
`sudo useradd -r -M -s /bin/sh -c "Sistema 55" sistema55`  

`sudo passwd sistema55`

### DESBLOQUEAR USUARIO

#### Desbloquear al usuario usuario33 asignándole una clave
`sudo passwd -u usuario33`

#### Modificar  el  usuario  usuario33  y  ponerle  como  nombre  completo  “Juan  Gómez Rodríguez”
`sudo usermod -c "Juan Gómez Rodríguez usuario33`

#### Modificar el usuario usuario33 y añadirlo a los grupos sudo y adm
`sudo usermod -G sudo,adm usuario33`  
`groups usuario33`

#### Escribir el comando para bloquear al usuario usuario33. Comprobar que después no puede abrir sesión
`sudo passwd -l usuario33`  

`su usuario33`

#### Escribir el comando para desbloquear al usuario usuario33. Comprobar que después puede abrir sesión
`sudo passwd -u usuario33`

`su usuario33`

### ELIMINAR USUARIO

#### Escribir el comando para borrar el usuario usuario44 y su directorio personal.
`sudo deluser --remove-home usuario44`

## GRUPOS

#### Escribir el comando para crear el grupo usuarios_estandar con el GID 1500.
`sudo groupadd -g 1500 usuarios_estandar`

#### Escribir el comando para añadir al usuario usuario33 y usuario44 al grupo usuarios_estandar.
`sudo usermod -aG usuarios_estandar usuario33`  

`sudo usermod -aG usuarios_estandar usuario44`

#### Escribir el comando para convertir al usuario44 en administrador.
`sudo usermod -aG sudo usuario44`

#### Escribir el comando para forzar a que el usuario usuario33 cambie su contraseña en el siguiente inicio de sesión. Probarlo abriendo sesión con este usuario
`sudo passwd -e usuario33`

#### Escribir el comando para eliminar el grupo usuario_estandar.
`sudo groupdel usuarios_estandar`

## DIRECTIVAS CONTRASEÑAS

#### Cambiar cosas directivas contraseñas
`sudo nano /etc/pam.d/common-password`

#### Cambiar cosas directivas cuentas
`sudo nano /etc/pam.d/common-auth`

#### Usuarios cambian sus contraseñas
`sudo nano /etc/login.defs`

#### Superar el número máximo de abrir sesión del usuario22 para bloquear su cuenta y escribir el comando para mostrar el número de intentos fallidos de abrir sesión del usuario usuario22

`sudo pam_tally2 --user usuario22`

#### Resetear el número de intentos del abrir sesión del usuario usuario22.

`sudo pam_tally2 --user usuario22 --reset`

#### Resetear el número de intentos del abrir sesión del usuario usuario22. 22. Establecer losparámetros de vigencia de la contraseña siguientes para el usuario usuario22:  

1.  Vigencia máxima de contraseña: 200 días.
2.  Vigencia mínima de contraseña: 5 días.
3.  Avisos de cambio de contraseña: 20 días.
4.  Bloqueo de la cuenta inactiva: 10 días
   
`sudo change -M 100 -m 5 -W 20 -I 10 usuario33`
