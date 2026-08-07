# CÁC CHỈ THỊ BIÊN DỊCH

## Hướng dẫn thay đổi code khi chuyển board env với PlatformIO

Hướng dẫn sau hướng dẫn thay đổi code tự động dựa việc chọn [env] trong platformio.ini
![image](https://github.com/user-attachments/assets/df41f110-fdca-4a75-b7c2-53608d97335f)

1. Mở file **platformio.ini**
2. Trong các cấu hình board khác nhau [env] bổ sung thêm flag biên dịch. Ví dụ
    ```dosini
    [env:esp32-c3-devkitm-1]
    ; something
    build_flags = 
    	-D ADRUINO_BOARD_ESP32_C3_SUPERMINI    ; đặt thêm define bất kì
    
    [env:esp32-wroom-32]
    ; something
    build_flags = 
    	-D ADRUINO_BOARD_ESP32_DEV_KIT        ; đặt thêm define bất kì
    ```
3. Trong mã nguồn, bổ sung các chỉ thị biên dịch
   ```dosini
    #if defined(ADRUINO_BOARD_ESP32_C3_SUPERMINI)
        // TODO: something
    #elif defined(ADRUINO_BOARD_ESP32_DEV_KIT)
        // TODO: something
    #endif   
   ```
Vậy là xong. Các chỉ thị sẽ làm thay đổi mã nguồn cần biên dịch mỗi khi thay đổi [env] trên giao diện ![change platformio env](https://github.com/user-attachments/assets/8d23e73d-abed-4873-93c0-df2b9e4b602c)



## Các chỉ thị sử dụng với ArduinoIDE

Các chỉ thị giúp thay đổi code tùy theo loại Board được chọn trên giao diện. Vi dụ

```C
#if defined(AVR_UNO)
    /// Áp dùng khi board là Arduino UNO
#elif defined(ESP32C3_DEV)
    /// Áp dụng khi board là ESP32C3 DevKit Module
#endif       
```

### Chỉ thị xác định kiến trúc của MCU

Mặc dù có nhiều loại board khác nhau, chúng có thể dùng chung một MCU, hoặc một loại MCU của kiến trúc nào đó. Cách sử dụng chỉ thị để xác định kiến trúc của MCU như sau

```C
#if defined(ARDUINO_ARCH_ESP32)
    /// Áp dụng khi MCU thuộc họ ESP32
#elif defined(ARDUINO_ARCH_ESP8266)
    /// Áp dụng khi CPU thuộc họ ESP8266
#elif defined(ARDUINO_ARCH_AVR)
    /// Áp dụng khi CPU thuộc họ AVR như Arduino Uno, Mega, Lilypad
#endif       
```

### Shorcut

1. [Danh sách Board sử dụng kiến trúc AVR - ATmega](#đối-với-các-bộ-xử-lý-thuộc-kiến-trúc-avr-như-uno-nano)
2. [Danh sách Board sử dụng kiến trúc AVR - ATTiny](#đối-với-các-bộ-xử-lý-thuộc-kiến-trúc-avr---dòng-chip-attiny)
3. [Danh sách Board sử dụng mcu ESP32](#đối-với-các-bộ-xử-lý-thuộc-họ-esp32)
4. [Danh sách Board sử dụng mcu ESP8266](#đối-với-các-bộ-xử-lý-thuộc-họ-esp8266)

### Đối với các bộ xử lý thuộc kiến trúc AVR như Uno, Nano

- Tổng quát, hãy tìm từ khóa **build.board** và lấy ra mã định danh ở file **boards.txt** này <https://github.com/arduino/ArduinoCore-avr/blob/master/boards.txt>

- Ví dụ một số loại board phổ biến:
  |Tên board | Mã chỉ thị biên dịch |
  |--|--|
  |Arduino Uno | AVR_UNO |
  |Arduino Nano |AVR_NANO|
  |Arduino Mega, hoặc Arduino Mega 2560 | AVR_MEGA2560 |
  |Arduino Mega 1280 | AVR_MEGA |
  |Arduino Micro | AVR_MICRO|
  |Arduino Mini | AVR_MINI|
  |LilyPad Arduino USB | AVR_LILYPAD_USB|
  |LilyPad Arduino | AVR_LILYPAD |
  |Arduino Pro or Pro Mini|AVR_PRO|
  |Arduino UNO WiFi|AVR_UNO_WIFI_DEV_ED|

### Đối với các bộ xử lý thuộc kiến trúc AVR - dòng chip ATTINY

- Tổng quát, hãy tìm từ khóa **build.board** và lấy ra mã định danh ở file **boards.txt** này <https://github.com/digistump/DigistumpArduino/blob/master/digistump-avr/boards.txt>
- Ví dụ chỉ có 2 board là:
  |Tên board | Mã chỉ thị biên dịch |
  |--|--|  
  |ATtiny25/45/85|attiny|
  |ATtiny24/44/84|attiny|

### Đối với các bộ xử lý thuộc họ ESP32

- Tổng quát, hãy tìm từ khóa **build.board** và lấy ra mã định danh ở file **boards.txt** này <https://github.com/espressif/arduino-esp32/blob/master/boards.txt>
- Ví dụ một số loại board phổ biến:
  |Tên board | Mã chỉ thị biên dịch |
  |--|--|
  |ESP32C2 Dev Module|ESP32C2_DEV|
  |ESP32H2 Dev Module|ESP32H2_DEV|
  |ESP32C6 Dev Module|ESP32C6_DEV|
  |ESP32S3 Dev Module|ESP32S3_DEV|
  |ESP32C3 Dev Module|ESP32C3_DEV|
  |ESP32S2 Dev Module|ESP32S2_DEV|
  |ESP32 Dev Module|ESP32_DEV|
  |ESP32-WROOM-DA Module|ESP32_WROOM_DA|
  |ESP32 Wrover Module|ESP32_DEV|
  |ESP32 PICO-D4|ESP32_PICO|
  |ESP32S3 Dev Module Octal (WROOM2)|ESP32S3_DEV|
  |ESP32-S3-Box|ESP32_S3_BOX|
  |ESP32-S3-USB-OTG|ESP32_S3_USB_OTG|
  |ESP32S3 CAM LCD|ESP32S3_CAM_LCD|
  |ESP32S2 Native USB|ESP32S2_USB|
  |ESP32 Wrover Kit (all versions)|ESP32_WROVER_KIT|
  |Aventen S3 Sync|AVENTEN_S3_SYNC|
  |UM BLING|BLING|
  |UM FeatherS2|FEATHERS2|
  |UM FeatherS2 Neo|FEATHERS2NEO|
  |UM FeatherS3|FEATHERS3|
  |UM NanoS3|NANOS3|
  |UM PROS3|PROS3|
  |UM RMP|RMP|
  |UM TinyPICO|TINYPICO|
  |UM TinyC6|TINYC6|
  |UM TinyS2|TINYS2|
  |UM TinyS3|TINYS3|
  |S.ODI Ultra v1|ESP32_DEV|
  |LilyGo T-Display|LILYGO_T_DISPLAY|
  |LilyGo T-Display-S3|LILYGO_T_DISPLAY_S3|
  |microS2|MICROS2|
  |MagicBit|ESP32_DEV|
  |Turta IoT Node|ESP32_PICO|
  |XinaBox CW02|ESP32_DEV|
  |SparkFun ESP32 Thing|ESP32_THING|
  |SparkFun ESP32 Thing Plus|ESP32_THING_PLUS|
  |SparkFun ESP32 Thing Plus C|ESP32_THING_PLUS_C|
  |SparkFun ESP32-S2 Thing Plus|ESP32S2_THING_PLUS|
  |SparkFun ESP32-C6 Thing Plus|ESP32C6_THING_PLUS|
  |SparkFun ESP32 MicroMod|ESP32_MICROMOD|
  |SparkFun LoRa Gateway 1-Channel|ESP32_DEV|
  |SparkFun ESP32 IoT RedBoard|ESP32_IOT_REDBOARD|
  |SparkFun ESP32-C6 Qwiic Pocket|ESP32C6_QWIIC_POCKET|
  |SparkFun Pro Micro - ESP32C3|SPARKFUN_PRO_MICRO_ESP32C3|
  |u-blox NINA-W10 series (ESP32)|UBLOX_NINA_W10|
  |u-blox NORA-W10 series (ESP32-S3)|UBLOX_NORA_W10|
  |Widora AIR|WIDORA_AIR|
  |Electronic SweetPeas - ESP320|ESP320|
  |Nano32|NANO32|
  |LOLIN D32|LOLIN_D32|
  |LOLIN D32 PRO|LOLIN_D32_PRO|
  |LOLIN C3 Mini|LOLIN_C3_MINI|
  |LOLIN S2 Mini|LOLIN_S2_MINI|
  |LOLIN S2 PICO|LOLIN_S2_PICO|
  |LOLIN S3|LOLIN_S3|
  |LOLIN S3 Mini|LOLIN_S3_MINI|
  |LOLIN S3 Pro|LOLIN_S3_PRO|
  |WEMOS LOLIN32|LOLIN32|
  |WEMOS LOLIN32 Lite|LOLIN32_LITE|
  |Dongsen Tech Pocket 32|Pocket32|
  |WeMos WiFi&Bluetooth Battery|Pocket32|
  |ESPea32|ESPea32|
  |Noduino Quantum|QUANTUM|
  |Node32s|Node32s|
  |Hornbill ESP32 Dev|HORNBILL_ESP32_DEV|
  |Hornbill ESP32 Minima|HORNBILL_ESP32_MINIMA|
  |DFRobot Beetle ESP32-C3|ESP32C3_DEV|
  |DFRobot Beetle ESP32-C6|DFROBOT_BEETLE_ESP32C6|
  |FireBeetle 2 ESP32-E|DFROBOT_FIREBEETLE_2_ESP32E|
  |DFRobot Firebeetle 2 ESP32-S3|ESP32S3_DEV|
  |DFRobot FireBeetle 2 ESP32-C6|DFROBOT_FIREBEETLE_2_ESP32S3|
  |DFRobot Romeo ESP32-S3|DFROBOT_ROMEO_ESP32S3|
  |FireBeetle-ESP32|DFROBOT_FIREBEETLE_ESP32|
  |IntoRobot Fig|INTOROBOT_ESP32_DEV|
  |Onehorse ESP32 Dev Module|ONEHORSE_ESP32_DEV|
  |Adafruit Metro ESP32-S2|METRO_ESP32S2|
  |Adafruit Metro ESP32-S3|METRO_ESP32S3|
  |Adafruit MagTag 2.9"|MAGTAG29_ESP32S2|
  |Adafruit FunHouse|FUNHOUSE_ESP32S2|
  |Adafruit ESP32 Feather|FEATHER_ESP32|
  |Adafruit Feather ESP32 V2|ADAFRUIT_FEATHER_ESP32_V2|
  |Adafruit Feather ESP32-S2|ADAFRUIT_FEATHER_ESP32S2|
  |Adafruit Feather ESP32-S2 TFT|ADAFRUIT_FEATHER_ESP32S2_TFT|
  |Adafruit Feather ESP32-S2 Reverse TFT|ADAFRUIT_FEATHER_ESP32S2_REVTFT|
  |Adafruit Feather ESP32-S3 2MB PSRAM|ADAFRUIT_FEATHER_ESP32S3|
  |Adafruit Feather ESP32-S3 No PSRAM|ADAFRUIT_FEATHER_ESP32S3_NOPSRAM|
  |Adafruit Feather ESP32-S3 TFT|ADAFRUIT_FEATHER_ESP32S3_TFT|
  |Adafruit Feather ESP32-S3 Reverse TFT|ADAFRUIT_FEATHER_ESP32S3_REVTFT|
  |Adafruit QT Py ESP32|ADAFRUIT_QTPY_ESP32_PICO|
  |Adafruit QT Py ESP32-C3|ADAFRUIT_QTPY_ESP32C3|
  |Adafruit QT Py ESP32-S2|ADAFRUIT_QTPY_ESP32S2|
  |Adafruit QT Py ESP32-S3 No PSRAM|ADAFRUIT_QTPY_ESP32S3_NOPSRAM|
  |Adafruit QT Py ESP32-S3 (4M Flash 2M PSRAM)|ADAFRUIT_QTPY_ESP32S3_N4R2|
  |Adafruit ItsyBitsy ESP32|ADAFRUIT_ITSYBITSY_ESP32|
  |Adafruit MatrixPortal ESP32-S3|ADAFRUIT_MATRIXPORTAL_ESP32S3|
  |Adafruit pyCamera S3|ADAFRUIT_CAMERA_ESP32S3|
  |Adafruit Qualia ESP32-S3 RGB666|QUALIA_S3_RGB666|
  |NodeMCU-32S|NodeMCU_32S|
  |Nologo ESP32C3 Super Mini|NOLOGO_ESP32C3_SUPER_MINI|
  |Nologo ESP32S3 Pico|NOLOGO_ESP32S3_PICO|
  |MH ET LIVE ESP32DevKIT|MH_ET_LIVE_ESP32DEVKIT|
  |MH ET LIVE ESP32MiniKit|MH_ET_LIVE_ESP32MINIKIT|
  |ESP32vn IoT Uno|esp32vn_iot_uno|
  |DOIT ESP32 DEVKIT V1|ESP32_DEV|
  |DOIT ESPduino32|ESP32_DEV|
  |OLIMEX ESP32-EVB|ESP32_EVB|
  |OLIMEX ESP32-POE|ESP32_POE|
  |OLIMEX ESP32-POE-ISO|ESP32_POE_ISO|
  |OLIMEX ESP32-DevKit-LiPo|ESP32_DEVKIT_LIPO|
  |OLIMEX ESP32-S2-DevKit-Lipo|ESP32S2_DEVKIT_LIPO|
  |OLIMEX ESP32-S2-DevKit-Lipo-USB|ESP32S2_DEVKIT_LIPO_USB|
  |OLIMEX ESP32-S3-DevKit-Lipo|ESP32S3_DEVKIT_LIPO|
  |OLIMEX ESP32-C3-DevKit-Lipo|ESP32C3_DEVKIT_LIPO|
  |OLIMEX ESP32-C6-EVB|ESP32C6_EVB|
  |OLIMEX ESP32-H2-DevKit-LiPo|ESP32H2_DEVKIT_LIPO|
  |OLIMEX ESP32-SBC-FABGL|ESP32_SBC_FABGL|
  |ThaiEasyElec's ESPino32|ESPino32|
  |M5Core|M5STACK_CORE|
  |M5Fire|M5STACK_FIRE|
  |M5Core2|M5STACK_CORE2|
  |M5Tough|M5STACK_TOUGH|
  |M5Station|M5STACK_STATION|
  |M5StickC|M5STACK_STICKC|
  |M5StickCPlus|M5STACK_STICKC_PLUS|
  |M5StickCPlus2|M5STACK_STICKC_PLUS2|
  |M5Atom|M5STACK_ATOM|
  |M5AtomS3|M5STACK_ATOMS3|
  |M5CoreS3|M5STACK_CORES3|
  |M5TimerCAM|M5STACK_TIMER_CAM|
  |M5UnitCAM|M5STACK_UNIT_CAM|
  |M5UnitCAMS3|M5STACK_UNIT_CAMS3|
  |M5PoECAM|M5STACK_POE_CAM|
  |M5Paper|M5STACK_PAPER|
  |M5CoreInk|M5STACK_COREINK|
  |M5StampPico|M5STACK_STAMP_PICO|
  |M5StampC3|M5STACK_STAMP_C3|
  |M5StampS3|M5STACK_STAMP_S3|
  |M5Capsule|M5STACK_CAPSULE|
  |M5Cardputer|M5STACK_CARDPUTER|
  |M5Dial|M5STACK_DIAL|
  |ODROID ESP32|ODROID_ESP32|
  |Heltec WiFi Kit 32|HELTEC_WIFI_KIT_32|
  |Heltec WiFi Kit 32(V3)|HELTEC_WIFI_KIT_32_V3|
  |Heltec WiFi LoRa 32|HELTEC_WIFI_LORA_32|
  |Heltec WiFi LoRa 32(V2)|HELTEC_WIFI_LORA_32_V2|
  |Heltec WiFi LoRa 32(V3)|HELTEC_WIFI_LORA_32_V3|
  |Heltec Wireless Stick(V3)|HELTEC_WIRELESS_STICK_V3|
  |Heltec Wireless Stick Lite(V3)|HELTEC_WIRELESS_STICK_LITE_V3|
  |Heltec Wireless Shell (V3)|HELTEC_WIRELESS_SHELL_V3|
  |Heltec Capsule Sensor (V3)|HELTEC_CAPSULE_SENSOR_V3|
  |Heltec Wireless Paper|HELTEC_WIRELESS_PAPER|
  |Heltec Wireless Tracker|HELTEC_WIRELESS_TRACKER|
  |Heltec Wireless Mini Shell|HELTEC_WIRELESS_MINI_SHELL|
  |Heltec Wireless Stick|HELTEC_WIRELESS_STICK|
  |Heltec Wireless Stick Lite / Wireless Shell|HELTEC_WIRELESS_STICK_LITE|
  |Heltec Wireless Bridge|HELTEC_WIRELESS_BRIDGE|
  |Heltec E-Ink Driver|HT_DE01|
  |ESPectro32|ESPECTRO32|
  |Microduino-CoreESP32|CoreESP32|
  |ALKS ESP32|ALKS|
  |WiPy 3.0|WIPY3|
  |WT32-ETH01 Ethernet Module|WT32_ETH01|
  |WT32-SC01 PLUS|WT32_SC01_PLUS|
  |BPI-BIT|BPI_BIT|
  |BPI-Leaf-S3|BPI_LEAF_S3|
  |Silicognition wESP32|WESP32|
  |D-duino-32|D_Duino_32|
  |LoPy|LoPy|
  |LoPy4|LoPy4|
  |OROCA EduBot|OROCA_EDUBOT|
  |ESP32 FM DevKit|fm_devkit|
  |Frog Board ESP32|FROG_ESP32|
  |AI Thinker ESP32-CAM|ESP32_DEV|
  |WEMOS D1 MINI ESP32|D1_MINI32|
  |WEMOS D1 R32|D1_UNO32|
  |Pycom GPy|PYCOM_GPY|
  |VintLabs ESP32 Devkit|ESP32_DEV|
  |HONEYLemon|HONEYLEMON|
  |MGBOT IOTIK 32A|MGBOT_IOTIK32A|
  |MGBOT IOTIK 32B|MGBOT_IOTIK32B|
  |Piranha ESP-32|Piranha|
  |Metro ESP-32|Metro|
  |Senses's WEIZEN|sensesiot_weizen|
  |KITS ESP32 EDU|ESP32_PICO|
  |Labplus mPython|ESP32_DEV|
  |INEX OpenKB|openkb|
  |WiFiduino32|Wifiduino32|
  |WiFiduinoV2|WiFiduinoV2|
  |WiFiduino32S3|WiFiduino32S3|
  |IMBRIOS LOGSENS_V1P1|IMBRIOS_LOGSENS_V1P1|
  |ProtoCentral HealthyPi 4|HEALTHYPI_4|
  |ET-Board|Board|
  |Denky|DENKY|
  |uPesy ESP32 Wrover DevKit|UPESY_WROVER|
  |uPesy ESP32 Wroom DevKit|UPESY_WROOM|
  |uPesy EDU ESP32|UPESY_EDU_ESP32|
  |uPesy ESP32C3 Basic|UPESY_ESP32C3_BASIC|
  |uPesy ESP32C3 Mini|UPESY_ESP32C3_MINI|
  |uPesy ESP32S3 Basic|UPESY_ESP32S3_BASIC|
  |KB32-FT|ESP32_DEV|
  |Deneyap Kart|DYDK|
  |Deneyap Kart 1A|DYDK1A|
  |Deneyap Kart 1A v2|DYDK1Av2|
  |Deneyap Mini|DYM|
  |Deneyap Mini v2|DYMv2|
  |Deneyap Kart G|DYG|
  |Trueverit ESP32 Universal IoT Driver|Trueverit_ESP32_Universal_IoT_Driver|
  |Trueverit ESP32 Universal IoT Driver MK II|Trueverit_ESP32_Universal_IoT_Driver_MK_II|
  |ATMegaZero ESP32-S2|atmegazero_esp32s2|
  |Franzininho WiFi|FRANZININHO_WIFI|
  |Franzininho WiFi MSC|FRANZININHO_WIFI_MSC|
  |TAMC Termod S3|TAMC_TERMOD_S3|
  |DPU ESP32|DPU_ESP32|
  |Sonoff DUALR3|SONOFF_DUALR3|
  |Lion:Bit Dev Board|Bit_Dev_Board|
  |Watchy|WATCHY|
  |AirM2M_CORE_ESP32C3|AirM2M_CORE_ESP32C3|
  |XIAO_ESP32C3|XIAO_ESP32C3|
  |XIAO_ESP32C6|XIAO_ESP32C3|
  |XIAO_ESP32S3|XIAO_ESP32S3|
  |Connaxio's Espoir|connaxio_espoir|
  |CNRS AW2ETH|ESP32_PICO|
  |Department of Alchemy MiniMain ESP32-S2|DEPARTMENT_OF_ALCHEMY_MINIMAIN_ESP32S2|
  |Bee Data Logger|BEE_DATA_LOGGER|
  |Bee Motion S3|BeeMotionS3|
  |Bee Motion|Bee_Motion|
  |Bee Motion Mini|Bee_Motion_Mini|
  |Bee S3|Bee_S3|
  |unPhone 7|FEATHER_ESP32|
  |unPhone 8|unphone8|
  |unPhone 9|unphone9|
  |Cytron Maker Feather AIoT S3|CYTRON_MAKER_FEATHER_AIOT_S3|
  |RedPill(+) ESP32-S3|REDPILL_ESP32S3|
  |ESP-C3-M1-I-Kit|ESP32C3_M1_I_KIT|
  |RoboHeart Hercules|roboheart_hercules|
  |VALTRACK_V4_VTS_ESP32_C3|VALTRACK_V4_VTS_ESP32_C3|
  |VALTRACK_V4_MFW_ESP32_C3|VALTRACK_V4_MFW_ESP32_C3|
  |Edgebox-ESP-100|Edgebox-ESP-100|
  |Crabik Slot ESP32-S3|CRABIK_SLOT_ESP32_S3|
  |Nebula S3|NEBULAS3|
  |Lion:Bit S3 STEM Dev Board|LIONBITS3_DEV|
  |4D Systems gen4-ESP32 16MB Modules (ESP32-S3R8n16)|ESP32_S3R8N16|
  |Namino Rosso|NAMINO_ROSSO|
  |Namino Arancio|NAMINO_ARANCIO|
  |Namino Bianco|NAMINO_BIANCO|
  |IOXESP32|IOXESP32|
  |IOXESP32PS|IOXESP32PS|
  |ATD1.47-S3|ATD143_S3|
  |ESP32-S3 PowerFeather|ESP32S3_POWERFEATHER|
  |senseBox MCU-S2 ESP32-S2|SENSEBOX_MCU_ESP32S2|
  |Arduino Nano ESP32|NANO_ESP32|
  |MakerGO ESP32 C3 SuperMini|MAKERGO_C3_SUPERMINI|
  |ThingPulse ePulse Feather|THINGPULSE_EPULSE_FEATHER|
  |ThingPulse ePulse Feather C6|THINGPULSE_EPULSE_FEATHER_C6|
  |Geekble ESP32-C3|GEEKBLE_ESP32C3|

### Đối với các bộ xử lý thuộc họ ESP8266

- Tổng quát, hãy tìm từ khóa **build.board** và lấy ra mã định danh ở file **boards.txt** này <https://github.com/esp8266/Arduino/blob/master/boards.txt>
- Ví dụ một số loại board phổ biến:
  |Tên board | Mã chỉ thị biên dịch |--|
  |--|--|--:|
  |Generic ESP8266 Module|ESP8266_GENERIC|View|
  |Generic ESP8285 Module|ESP8266_ESP01|View|
  |4D Systems gen4 IoD Range|GEN4_IOD|View|
  |Adafruit Feather HUZZAH ESP8266|ESP8266_ADAFRUIT_HUZZAH|View|
  |Amperka WiFi Slot|AMPERKA_WIFI_SLOT|View|
  |Arduino|ESP8266_ARDUINO|View|
  |DOIT ESP-Mx DevKit (ESP8285)|ESP8266_ESP01|View|
  |Digistump Oak|ESP8266_OAK|View|
  |ESPDuino (ESP-13 Module)|ESP8266_ESP13|View|
  |ESPectro Core|ESP8266_ESPECTRO_CORE|View|
  |ESPino (ESP-12 Module)|ESP8266_ESPINO_ESP12|View|
  |ESPresso Lite 1.0|ESP8266_ESPRESSO_LITE_V1|View|
  |ESPresso Lite 2.0|ESP8266_ESPRESSO_LITE_V2|View|
  |ITEAD Sonoff|ESP8266_SONOFF_SV|View|
  |Invent One|ESP8266_INVENT_ONE|View|
  |LOLIN(WEMOS) D1 ESP-WROOM-02|ESP8266_WEMOS_D1WROOM02|View|
  |LOLIN(WEMOS) D1 R2 & mini|ESP8266_WEMOS_D1MINI|[Module MCU](https://iotappstory.com/hardware/ESP8266/boards/lolinwemos-d1-r2-mini)|
  |LOLIN(WEMOS) D1 mini (clone)|ESP8266_WEMOS_D1MINI|View|
  |LOLIN(WEMOS) D1 mini Lite|ESP8266_WEMOS_D1MINILITE|[View](https://www.wemos.cc/en/latest/d1/d1_mini_lite.html)|
  |LOLIN(WEMOS) D1 mini Pro|ESP8266_WEMOS_D1MINIPRO|[Sạc lithium](https://www.wemos.cc/en/latest/d1/d1_mini_pro.html)  |
  |LOLIN(WeMos) D1 R1|ESP8266_WEMOS_D1R1|[Dạng Uno](https://iotappstory.com/hardware/ESP8266/boards/lolinwemos-d1-r1)|
  |Lifely Agrumino Lemon v4|ESP8266_AGRUMINO_LEMON_V4|View|
  |NodeMCU 0.9 (ESP-12 Module)|ESP8266_NODEMCU_ESP12|View|
  |NodeMCU 1.0 (ESP-12E Module)|ESP8266_NODEMCU_ESP12E|View|
  |Olimex MOD-WIFI-ESP8266(-DEV)|MOD_WIFI_ESP8266|View|
  |Phoenix 1.0|ESP8266_PHOENIX_V1|View|
  |Phoenix 2.0|ESP8266_PHOENIX_V2|View|
  |Schirmilabs Eduino WiFi|ESP8266_SCHIRMILABS_EDUINO_WIFI|View|
  |Seeed Wio Link|ESP8266_WIO_LINK|View|
  |SparkFun Blynk Board|ESP8266_THING|View|
  |SparkFun ESP8266 Thing|ESP8266_THING|View|
  |SparkFun ESP8266 Thing Dev|ESP8266_THING_DEV|View|
  |SweetPea ESP-210|ESP8266_ESP210|View|
  |ThaiEasyElec's ESPino|ESP8266_ESPINO_ESP13|View|
  |WiFi Kit 8|wifi_kit_8|View|
  |WiFiduino|WIFIDUINO_ESP8266|View|
  |WifInfo|WIFINFO|View|
  |XinaBox CW01|ESP8266_XINABOX_CW01|View|
  
