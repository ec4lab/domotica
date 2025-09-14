# ESPhome
[ESPHome](https://esphome.io/), es una plataforma que te permite crear tus dispositivos domóticos de manera simple a partir de dispositivos ESP32 y ESP8266.


>Toda la documentación que ves aqui es una recopilación de recursos de internet y experiencias propias puramente con fines didácticos, si encuentras algún error o conoces una mejor forma de realizar los proyectos no dudes en contactarnos. El uso de estos recursos y su implementación en ambitos por fuera de lo educativo queda bajo tu responsabilidad.


## Instalar el complemento

## Flashear dispositivos
Si bien es posible flasher dispositivos directamente conectados a la raspberry pi que contiene home assistant [ESPHome](https://esphome.io/), tiene una plataforma online [WEB ESPHome](https://web.esphome.io/) que permite no solo flashear un dispositivo cuando no tenemos acceso físico a nuestro servidor sino que ni siquiera es necesario tener acceso a home assistant para grabarlo o utilizarlo.

> web esphome
[![web.esphome.io](imagenes/WebEspHome.png "Plataforma ESPHome web")](https://web.esphome.io/)

Tener en cuenta que ESPHome web no funciona con todos los exploradores, hasta ahora solo nos ha funcionado chrome.

### ESP8266 - Wemos D1 Mini
![WemosD1Mini](imagenes/WemosD1Mini.png "Placa de Desarrollo Wemos D1 Mini")
Es uno de los más sencillos, normalmente no trae problemas.

Primero debemos conectar la placa al usb de nuestra pc.
Luego click en CONNECT y seleccionamos el puerto.  

![WebESPHome](imagenes/web_conectar.png "Seleccionar Puerto")

**💡tip**: si aparecen muchos puedes conectar y desconectar la placa y ver cual aparece y desaparece

Luego clich en **PREPARE FOR FIRST USE** y luego en la ventana emergente: **INSTAL**  

![WebESPHome](imagenes/web_first.png "Instalar Firmware")

Esperamos que termine de instalar

![WebESPHome](imagenes/web_instalar.png "Instalar Firmware")

![WebESPHome](imagenes/web_wifi1.png "Instalar Firmware")

![WebESPHome](imagenes/web_wifi2.png "Instalar Firmware")

![WebESPHome](imagenes/web_wifi3.png "Instalar Firmware")

![WebESPHome](imagenes/web_wifi4.png "Instalar Firmware")

Listo!

Luego en el complemento ESPHOME en Home Assistant:
![ESPHome](imagenes/esp_discovered.png "Instalar Firmware")
![ESPHome](imagenes/esp_discovered2.png "Instalar Firmware")
![ESPHome](imagenes/esp_discovered3.png "Instalar Firmware")
![ESPHome](imagenes/esp_discovered4.png "Instalar Firmware")


SKIP!

![ESPHome](imagenes/yaml_01.png "Instalar Firmware")  

agregamos en el apartado wifi:

```yaml
wifi:
  use_address: esphome-web-df6d2a
  networks:
  # Red Principal
  - ssid: !secret wifi1_ssid
    password: !secret wifi1_password
  
  # Red Secundaria
  - ssid: !secret wifi2_ssid
    password: !secret wifi2_password
  
  # SSID y Pass del captive portal
  ap:
    ssid: "Fallback NuevoWemos"
    #password: "123456789" #Opcional
```

es muy importante **use_address**

![ESPHome](imagenes/yaml_02.png "Instalar Firmware") 

![ESPHome](imagenes/yaml_03.png "Instalar Firmware") 

instalar wiresly

una vez compilado y cargado no va a lograr conectarse, porque está buscando el nombre antigüo, asi que cerramos, pero en el tablero ya lo vamos a ver online, debemos volver a editar el yaml y comentar la línea de `use_address`, solo la volveremos a usar si cambiamos el nombre del dispositivo.

![ESPHome](imagenes/yaml_04.png "Instalar Firmware") 


![ESPHome](imagenes/yaml_05.png "Instalar Firmware") 

```yaml
...
# Información de las redes WIFI a las que se puede conectar
wifi:
  #use_address: esphome-web-df6d2a
  networks:
  # Red Principal
  - ssid: !secret... 
```
Listo, ya hemos cambiado el `nombre` y el `nombre amistoso`, también podemos editar el nombre del archivo, para esto usamos file editor.

![ESPHome](imagenes/fileeditor_01.png "Instalar Firmware")

![ESPHome](imagenes/fileeditor_02.png "Instalar Firmware") 

![ESPHome](imagenes/fileeditor_03.png "Instalar Firmware") 

![ESPHome](imagenes/fileeditor_04.png "Instalar Firmware") 

Será necesario reinstalar luego de cambiar el nombre del archivo.

listo!

![ESPHome](imagenes/yaml_06.png "Instalar Firmware") 

## 📫 Contacto

**EC4lab**  
[GitHub: ec4lab](https://github.com/ec4lab)  
[email: ec4lab@gmail.com](ec4lab@gmail.com)

---
