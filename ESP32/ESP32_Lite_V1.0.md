# ESP32 Lite V1.0

![ESP32 Lite V1.0](https://github.com/neittien0110/MCU/assets/8079397/0dc51700-faed-4efe-8194-391021855b1a)

![image](https://github.com/neittien0110/MCU/assets/8079397/532ce8c9-54db-4f00-b264-fef491e2acd9)

## Mô tả 
- CPU: ESP32-DOWN 240MHz High Power Processor
- Kích cỡ: 50mm x 25mm  (50mm chưa bao gồm 2mm thò ra của USB Type C cái)
- SRAM: 520kB 
- Flash: 4MB
- Wireless connectivity:
  - Wi-Fi: 802.11 b/g/n
  - Bluetooth: v4.2 BR/EDR and BLE
- Power Supply: 2.2V to 3.6V
- Logic Level: 3.3V
- Integrated Lithium Charger Circuit max. 500mA

![pins and interfaces](https://github.com/neittien0110/MCU/assets/8079397/f591975d-b699-4d61-9bfb-38f6af7234f2)

## Lập trình
- LED_BUILDIN  được nối với chân 22 (đã đo bằng đồng hồ)

```arduino
#define LED_BUILDIN 22
```

- Với Arduino IDE:
  - Chọn board: WEMOS LOLIN32 \
  ![Chọn board trên Arduino IDE](https://github.com/neittien0110/MCU/assets/8079397/f079de11-0bf1-4948-bd4a-beb5568ead66)
- Với Visual Studio Code:
  - Chọn board: \
    ![lolin32_lite](https://github.com/neittien0110/MCU/assets/8079397/ceddc91b-fe56-49a3-8798-de8a22c5e2f4)
  - Cấu hình PlatformIO
```
[env:lolin32_lite]
platform = espressif32
board = lolin32_lite
```
![image](https://github.com/neittien0110/MCU/assets/8079397/71912ac5-488c-45be-9af2-06452e94a2cd)

### Schematic

![image](https://github.com/neittien0110/MCU/assets/8079397/310ba9c4-1f37-4ddd-8047-4a91b105d267)

![lolin32_lite schematic](https://github.com/neittien0110/MCU/assets/8079397/39cdc625-25e0-4ebe-bcfa-4c6b08aa3d52)


## Demo
See the pdf with guide on Adruino IDE <https://megma.ma/wp-content/uploads/2021/08/Wemos-ESP32-Lolin32-Board-BOOK-ENGLISH.pdf>

## Vỏ in 3D
 - <https://www.thingiverse.com/thing:2846772>

## Mua
- <https://www.thegioiic.com/esp32-lite-v1-0-0-module-thu-phat-wifi-bluetooth>
