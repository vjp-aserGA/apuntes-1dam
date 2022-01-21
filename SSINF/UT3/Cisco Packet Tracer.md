Nota: `Shift+Ctrl+6` cancelar comandos no existentes 
___

# Swtich
### Comandos basicos
- `enable` - entrar a modo supervisor
___

### Comandos en modo supervisor
- `show run` - ver configuracion del router
- `show interfaces` - ver configuracion de las interfaces
- `show port-security <interfaz>` - ver información de seguridad
- `show vlan` - ver información sobre las VLANs
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

###### Configurar Port-Security
- `interface <if>` - entrar a la configuración del puerto
- `switchport mode access` - cambia a modo acceso (para dispositivos)
- `switchport port-security` - activa la seguridad
- `switchport port-security maximun X` - maximo de dispositivos
- `switchport port-security violation <accion>` - que hacer si es violada
	- `protect` - ignora las [[MAC Address|MAC]]s desconocidas
	- `restrict` - además manda una alerta de seguridad
	- `shutdown` - desactiva el puerto
- `switchport port-security mac-address sticky` - las primeras `maximun` [[MAC Address|MAC]]s  
- `exit` - salir de la configuración

###### Configurar VLANs
- `vlan <numero>` - configurar la vlan `numero`
- `no vlan <numero>` - borrar la vlan `numero`
- `name <nombre>` - cambiar nombre a la vlan
- `exit` - salir de la configuración de vlan
- `interface <if/if-range>` - entrar a la configuración del puerto/s
- `switchport mode access` - poner el puerto en modo acceso
- `switchport access vlan <numero>` - asignar el puerto a la vlan `numero`
- `switchport mode trunk` - pone un puerto en modo troncal para pasar las VLANs

# Router
###### Cofigurar ROuter para comunicar VLANs
- `enable` - entrar a modo modo supervisor
- `vlan database` - configurar las VLANs (deprecado)
- `config t` - modo de configuracion
- `interface <ifX/Y.VLANid>` - crear sub-interfaz para la VLAN
- `encapsulation dot1q <vlan>` - asigna la VLAN a esta subinterfaz
- `ip address <ip_addr> <ip_mask>` - asignar IP para el puerto virtual
- `interface <ifX/Y>` - configurar la interzfaz "real"
- `no shut` - encender la interfaz fisica en la que está conectado el cable