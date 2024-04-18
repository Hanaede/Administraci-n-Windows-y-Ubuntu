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
`new LocalUser -Name ["nombre de usuario"] -NoPassword`

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


## **WPS**

### EJECUTAR EDGE, VER SU PID Y CERRARLO
`start microsoft-edge:`  

`tasklist /fi "imagename eq msedge.exe"`  

`taskkill /PID [PID] /f`


### EJECUTAR EDGE CON VENTANA MAXIMIZADA
`Start-Process -filepath msedge.exe -WindowStyle maximized`

### EJECUTAR BLOC DE NOTAS ABRIENDO ARCHIVO RESOLUCIÓN DE NOMBRES
`Start-Process -FilePath notepad.exe -ArgumentList "C:\Windows\System32\drivers\etc\hosts"`


### PARAR UN PROGRAMA
`Stop-Service -Name ["nombre de programa]`  

-Ejemplo: `Stop-Service -Name "msedge.exe"`

