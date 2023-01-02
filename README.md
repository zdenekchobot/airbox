# AirBox
Senzor pro měření stavu ovzduší. Pomocí dvou pokročilých senzorů měří koncentraci pevných částic PM (senzor Sensirion SPS30) a teplotu, realtivní vlkosti a tlak vzduch (senzor Bosch BME280). Jedná se variantou odvozenou ze senzorů doporučených komunitním projektem [sensor.community](https://sensor.community/cz/). Airbox používá stejné zapojení jako komunitní senzory a je tak plně kompatibilní s jejich firmware.
## Hardware
Elektronika senzoru využívá běžný modul WeMos D1 Mini s WiFi mikrokontrolerem ESP8266. Ten tvoří srdce senzoru - po sběrnici i2c komunikuje s SPS30 a BME280 a získaná data odesílá prostřednictvním internetu ke zpracování a publikaci komunitním webům, popřípadě i jinam podle vaší volby. Kvůli umístění ve venkovním prostředí je elektronika umístněna v běžné vodotěsné elektrikářské krabičce. Jednotlivé elektronické komponenty jsou upevněny na jednoduché 3D vytištěné konstrukci, která také zajišťuje vhodné proudění vzduchu. [Schéma zapojení](/Schéma/Schematic_Airbox.pdf) je jednoduché.
### Seznam komponent
- krabička [SCAME SCABOX 120x80x50mm IP56](https://www.elfetex.cz/10-078-693-scame-krabice-scabox-120x80x50mm-ip56)
- 2x [nerez sítko ke zpětné klapce DN15 - 1/2"](https://www.obchod-vtp.cz/nerez-sitko-ke-zpetne-klapce-dn15-1-2)
- [WeMos D1 Mini ESP8266 WiFi](https://dratek.cz/arduino/121932-wemos-d1-mini-esp8266-wifi-modul-v2.0.html), originál či klon
- senzor kvality ovzduší [Sensirion SPS30](https://www.soselectronic.cz/products/sensirion/sps30-2-304234)
- senzor teploty, vlhkosti a tlaku [BME280](https://dratek.cz/arduino/1361-bme280-modul-mereni-teploty-vlhkosti-a-barometrickeho-tlaku-precizni.html)
- [3D tištěné díly](/STL)
- gumová průchodka napájecího kablíku, např. [FIX-GR-98](https://www.tme.eu/cz/details/fix-gr-98/pruchodky/fix-fasten/)
- propojovací vodiče, napájecí kablík
- samosmršťovací bužírka
- kousek pěnové gumy pro fixaci a utěsnění SPS30 (samolepící je výhodou)
- samořezné šroubky
### Sestavení
Představu o sestavení senzoru poskytují [fotografie](/Obrázky) z výroby "prototypu". Poněkud nestandardní je upevnění modulu Wemos. Přiložené standardní "hřebínky" jsou **delšímí** piny nasunuty se strany ESP8266 a zapájeny. Na delší piny jsou připájeny propojovací vodče. Kratší piny jsou zasunuty do základny a dostatečně upevňují modul. Pokud potřebujete modul více fixovat, přilepte na ESP8266 oboustranně lepící (teplovodivou) pásku. Po zasunutí pinů do základny druhá strany pásky přilne k základně.      
## Software
Jako zákadní software, resp. firmware lze použít standardní, neupravený komunitní firmware. Pro jeho nahrání a konfiguraci je vhodné postupovat podle [návodu na komunitním webu](https://sensor.community/cz/sensors/airrohr/).
### Home Assistant
Do AirBoxu lze nahrát i firmware ESPHome, získaná data využít v HA a odtud je odesílat na web [sensor.community](https://sensor.community/cz/). Konfigurační soubory yaml pro ESPHome, služeb odesílání dat včetně automatizace jsou k dispozici ve [složce YAML](/YAML). 
Konfigurace služeb a automatizace je z větší části práce šikuly [hmmboba](https://github.com/hmmbob/HomeAssistantConfig) - děkuji!
## Tipy
1. Místo Wemos D1 mini doporučuji spíše modul [WeMos D1 Mini Pro 16MB](https://www.laskakit.cz/wemos-d1-mini-pro--esp8266-wifi-modul/) kvůli možnosti připojení externí antény, např. [WiFi 42x12mm anténa 2.4G 5dB](https://www.laskakit.cz/wifi-42x12mm-antena-2-4g--5db-u-fl--ipex1--konektor/) nebo [NiceRF snténa 3.0dBi 2.4G](https://www.laskakit.cz/antena-10cm-2-4g/) s příslušným pigtailem.
2. Na vrtání velkých děr do krabičky se skvěle osvědčily [stromečkové/stupňovité vrtáky](https://www.lidl.cz/p/parkside-sada-specialnich-vrtaku-psb-6-a1/p100341714004). Velké poděkování [Jiri Janovec](https://twitter.com/jjiik) a [Josef Zvolanek #ePap](https://twitter.com/JosefZvolanek) za radu!  
