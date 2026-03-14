**Kconfig Option Table**



menu "Example Configuration"



&#x20;   config ESP\_WIFI\_SSID

&#x20;       string "WiFi SSID"

&#x20;       default "myssid"

&#x20;       help

&#x20;           SSID (network name) for the example to connect to.



&#x20;   config ESP\_WIFI\_PASSWORD

&#x20;       string "WiFi Password"

&#x20;       default "mypassword"

&#x20;       help

&#x20;           WiFi password (WPA or WPA2) for the example to use.



&#x20;   choice ESP\_WIFI\_SAE\_MODE

&#x20;       prompt "WPA3 SAE mode selection"

&#x20;       default ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_BOTH

&#x20;       help

&#x20;           Select mode for SAE as Hunt and Peck, H2E or both.

&#x20;       config ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_HUNT\_AND\_PECK

&#x20;           bool "HUNT AND PECK"

&#x20;       config ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_HASH\_TO\_ELEMENT

&#x20;           bool "H2E"

&#x20;           depends on ESP\_WIFI\_ENABLE\_SAE\_H2E

&#x20;       config ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_BOTH

&#x20;           bool "BOTH"

&#x20;           depends on ESP\_WIFI\_ENABLE\_SAE\_H2E

&#x20;   endchoice



&#x20;   config ESP\_WIFI\_PW\_ID

&#x20;       string "PASSWORD IDENTIFIER"

&#x20;       depends on  ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_HASH\_TO\_ELEMENT|| ESP\_STATION\_EXAMPLE\_WPA3\_SAE\_PWE\_BOTH

&#x20;       default ""

&#x20;       help

&#x20;           password identifier for SAE H2E



&#x20;   config ESP\_MAXIMUM\_RETRY

&#x20;       int "Maximum retry"

&#x20;       default 5

&#x20;       help

&#x20;           Set the Maximum retry to avoid station reconnecting to the AP unlimited when the AP is really inexistent.



&#x20;   choice ESP\_WIFI\_SCAN\_AUTH\_MODE\_THRESHOLD

&#x20;       prompt "WiFi Scan auth mode threshold"

&#x20;       default ESP\_WIFI\_AUTH\_WPA2\_PSK

&#x20;       help

&#x20;           The weakest authmode to accept in the scan mode.

&#x20;           This value defaults to ESP\_WIFI\_AUTH\_WPA2\_PSK in case password is present and ESP\_WIFI\_AUTH\_OPEN is used.

&#x20;           Please select ESP\_WIFI\_AUTH\_WEP/ESP\_WIFI\_AUTH\_WPA\_PSK in case AP is operating in WEP/WPA mode.



&#x20;       config ESP\_WIFI\_AUTH\_OPEN

&#x20;           bool "OPEN"

&#x20;       config ESP\_WIFI\_AUTH\_WEP

&#x20;           bool "WEP"

&#x20;       config ESP\_WIFI\_AUTH\_WPA\_PSK

&#x20;           bool "WPA PSK"

&#x20;       config ESP\_WIFI\_AUTH\_WPA2\_PSK

&#x20;           bool "WPA2 PSK"

&#x20;       config ESP\_WIFI\_AUTH\_WPA\_WPA2\_PSK

&#x20;           bool "WPA/WPA2 PSK"

&#x20;       config ESP\_WIFI\_AUTH\_WPA3\_PSK

&#x20;           bool "WPA3 PSK"

&#x20;       config ESP\_WIFI\_AUTH\_WPA2\_WPA3\_PSK

&#x20;           bool "WPA2/WPA3 PSK"

&#x20;       config ESP\_WIFI\_AUTH\_WAPI\_PSK

&#x20;           bool "WAPI PSK"

&#x20;   endchoice



endmenu



MQTT Topic: chaji/charger/mcu1/status



Wokwi: https://wokwi.com/projects/458437642617944065



**Schematic**

Components
1. ESP32-WROOM-32
2. AMS117-3.3
3. CP2102
4. BC817 Transistor x3
5. Capacitors
6. Resistors



The circuit was designed around the ESP32‑WROOM‑32 microcontroller as the main controller. A AMS1117‑3.3 voltage regulator converts the input supply to a stable 3.3 V rail required by the ESP32 and other logic components, with capacitor values selected according to the regulator datasheet for stability. A CP2102 USB-to-UART converter provides USB programming and serial communication with the ESP32. Three BC817 transistors are used as switching drivers for external control signals. All resistor and capacitor values were selected based on the respective component datasheets to ensure proper biasing, signal integrity, and stable power regulation.

