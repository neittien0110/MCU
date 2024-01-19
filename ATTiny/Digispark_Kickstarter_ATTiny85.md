# Digispark Kickstarter ATTiny85

## Mô tả 
- Module CPU: ESP-WROOM-32
- Kích cỡ trùng khớp với câc loại NodeMCU phổ biến ở VN
- Lưu ý: có 2 loại cổng usb **Type C** và *Micro USB*

![image](https://github.com/neittien0110/MCU/assets/8079397/50128af6-1523-4dd5-851a-57714fe52314)

## Lập trình
- Hỗ trợ arduinoide mixly, Mind +, Python và các phần mềm lập trình khác
- LED_BUILDIN  được nối với chân D2 (đã đo bằng đồng hồ)

```arduino
#define LED_BUILDIN 2
```

- Với Arduino IDE:
  - Thêm thông tin về board mới:
    ```
    http://digistump.com/package_digistump_index.json
    ```
  - Chọn board: Digispakr (Default - 16 mhz)
- Với Visual Studio Code:
  - Chọn board: ![image](https://github.com/neittien0110/MCU/assets/8079397/5ee068bc-0274-446e-a262-9aab80e7654b)
  - Cấu hình PlatformIO
```
[env:digispark-tiny]
platform = atmelavr
board = digispark-tiny
; change microcontroller
board_build.mcu = attiny85
; change MCU frequency
board_build.f_cpu = 16500000L
```


## Thông số chi tiết
- CPU: ATTiny85
- Tần số xung nhịp: 
- Flash memory: 5.87KB
- RAM: 512B
- Nhà sản xuất: [Digistump](http://digistump.com/products/1?utm_source=platformio.org&utm_medium=docs)
Tham khảo: <https://docs.platformio.org/en/latest/boards/atmelavr/digispark-tiny.html?utm_source=platformio&utm_medium=piohome>

### Tra cứu bản đồ địa chỉ bộ nhớ

![image](https://github.com/neittien0110/MCU/assets/8079397/5576eae4-c1cc-43d6-a84a-4d05dc312027)
![image](https://github.com/neittien0110/MCU/assets/8079397/5534cc33-0604-4df2-8517-119a8abd7b6c)


## Demo
  [Video](https://youtu.be/Xo8rYATKyDA?si=4_hPLh-KgOdXgbzL)
  
## Vỏ in 3D
 - Dạng đầu USB đực: <https://www.thingiverse.com/thing:3303209>
 - Dạng đầu USB đực: <https://www.thingiverse.com/thing:3494815>

## Mua
- Shopee: <https://shopee.vn/product/578443443/16168780247?gad_source=1&gclid=EAIaIQobChMI37nak8HpgwMV49AWBR1BYg8UEAQYASABEgLB5vD_BwE>
- https://linhkienvietnam.vn/module-node-mcu-32s-esp32-devkitc-dung-module-esp-wroom-32
