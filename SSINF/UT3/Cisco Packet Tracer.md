Nota: `Shift+Ctrl+6` cancelar comandos no existentes 
___

# Swtich
### Comandos basicos
- `enable` - entrar a modo supervisor
___

### Comandos en modo supervisor
- `show run` - ver configuracion del router
- `show interfacse` - ver configuracion de las interfaces
- `config t` - entrar a modo de configuración
___

### Comandos en modo configuración
- `hostname <nombre>` - cambiar nombre
- `enable password <contraseña>` - poner contraseña
- `enable secret <contraseña>` - poner contraseña cifrada
- `no enable password` - quitar la contraseña
- `no enable secret` - quitar la contraseña cifrada
- `interface <interfazX/Y>` - modo configuración interfaz 
- `interface range <interfazX/Y-Z>` - modo configuración interfazes
___

### Comandos en modo configuración interfaz
- `shut` - desactivar el puerto
- `no shut` - reactivar el puerto
- `end` - graba y sale del modo configuración
- `switchport mode access` - cambia a modo acceso (para dispositivos)
- `switchport port-security` - activa la seguridad
- `switchport port-security maximun X` - maximo de dispositivos
- `switchport port-security violation <accion>` - que hacer si es violada
	- `protect` - ignora las [[MAC Address|MAC]]s desconocidas
	- `restrict` - además manda una alerta de seguridad
	- `shutdown` - desactiva el puerto
- `switchport port-security mac-address sticky` - las primeras `maximun` [[MAC Address|MAC]]s  