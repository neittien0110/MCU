# MCU

Mô tả về các loại vi điều khiển Master Control Unit

## Các chỉ thị biên dịch

Các chỉ thị giúp thay đổi code tùy theo loại Board được chọn trên giao diện. [Xem ở đây](./preprocessor.vi.md). Ví dụ

```C
#if defined(AVR_UNO)
    /// Áp dùng khi board là Arduino UNO
#elif defined(ESP32C3_DEV)
    /// Áp dụng khi board là ESP32C3 DevKit Module
#endif       
```

## Họ ESP32 kiến trúc RISC-V

>Hiểu hơn về kiến trúc RISC-V. [Xem ở đây](https://neittien0110.github.io/RISC-VFundamentalMaterials)

1. [ESP32-C3 Dual USB](ESP32/ESP32-C3_DevKitM_1_dual_usb.md)\
    ![ESP32-C3 Dual USB](./assets/esp32-c3.1.png)
2. [ESP32-C3 Super mini](ESP32/ESP32-C3_SuperMini.md)\
    ![ESP32-C3 Super mini](./assets/ESP32-C3_SuperMini.png)
3. [ESP32-C3 FH4 LedBoard](ESP32/ESP32-C3_FH4_LedBoard.md)\
    ![ESP32-C3 FH4 LedBoard](./assets/ESP32-C3_FH4_LedBoard.png)

## Họ ESP32 kiến trúc ARM

1. [ESP32 Dev Kit V1](ESP32/ESP32_Dev_Kit_V1.md) \
   ![ESP32 Dev Kit V1](https://github.com/neittien0110/MCU/assets/8079397/8a15155f-7191-4dea-92c6-5b0b96403807)
2. [ESP32 Lite V1.0](ESP32/ESP32_Lite_V1.0.md)\
   ![ESP32 Lite V1.0](https://github.com/neittien0110/MCU/assets/8079397/6234a674-fa97-4ba6-bf02-6be6ef4023d3)
3. [Wemos Lolin S2 mini](ESP32/Lolin_S2_mini.md)\
   ![Lolin S2 mini](https://github.com/neittien0110/MCU/assets/8079397/28776905-6750-4990-a436-22e171ad1bad)

## Họ ESP8266 ARM

1. [ESP8266 NodeMCU Ver 3](ESP8266/NodeMCU_V3.md)\
   ![image](https://github.com/neittien0110/MCU/assets/8079397/f32df356-5468-4375-ae79-c744f414449b)
2. [ESP8266 D1 R2 mini](ESP8266/Wemosd1r2mini.md)\
   ![ESP8266 Wemos D1 R2 mini](./assets/esp8266_wemosd1r2mini_thumbnail.png)
3. [ESP-01 và ESP-01s](ESP8266/ESP01.md)\
   ![ESP-01 và ESP-01s](assets/esp-01_top.png)

## Họ ATTINY kiến trúc AVR

1. [Digispark Kichstarter ATTiny85](ATTiny/Digispark_Kickstarter_ATTiny85.md)\
   ![image](https://github.com/neittien0110/MCU/assets/8079397/de27b818-f12e-478a-907c-27ee331f2706)

## Họ RASBERRY PI kiến trúc ARM

1. [RasberryPi Zero RP2040](RasberryPi/RasberryPi-Zero-RP2040.md)\
   ![RasberryPi Zero RP2040](./assets/rp2040_zero.png)
