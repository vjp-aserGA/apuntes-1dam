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
###### Configurar router para comunicar VLANs
- `enable` - entrar a modo modo supervisor
- `vlan database` - configurar las VLANs (deprecado)
- `config t` - modo de configuracion
- `interface <ifX/Y.VLANid>` - crear sub-interfaz para la VLAN
- `encapsulation dot1q <vlan>` - asigna la VLAN a esta subinterfaz
- `ip address <ip_addr> <ip_mask>` - asignar IP para el puerto virtual
- `interface <ifX/Y>` - configurar la interzfaz "real"
- `no shut` - encender la interfaz fisica en la que está conectado el cable

###### Configurar router para comunicar redes
- Protocolo RIP:
	- `enable`
	- `config t`
	- `router rip` - configurar el protocolo rip
	- `network <network_ip>` - añadir las redes a las que este router está conectado 



# Subnetting
Las máscaras no son más que sequencias de bits, empiezan con unos y acaban con ceros: `xxxxxxxx.xxxxxxxx.xxxxxxxx.xxxxxxxx`

Las máscaras de red determinan la capacidad de una red, más específicamente, la cantidad de ceros determina la capacidad.

Las mascaras de red más comunes son:
- Tipo A: `255.0.0.0`
- Tipo B: `255.255.0.0`
- Tipo C: `255.255.255.0`

Esto está muy bien, pero en muchos casos no necesitamos "espacio" para tantas IP.

Ya que los ceros determinan la capacidad; podemos crear máscaras de red con la capacidad que necesitemos. El mínimo de "capacidad" permitida es `4`. Es decir, una máscara: `11111111.11111111.11111111.11111100` o `255.255.255.252`.

- `Binario` - `Decimal` - `Max Direcciones` - `Max Dispositivos`
- `00000000` - `0` - `256` - `254`
- `10000000` - `128` - `128` - ``
- `11000000` - `192` - `64`
- `11100000` - `224` - `32`
- `11110000` - `240` - `16`
- `11111000` - `248` - `8`
- `11111100` - `252` - `4`