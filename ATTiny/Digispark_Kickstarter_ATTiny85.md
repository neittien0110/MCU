

# Digispark Kickstarter ATTiny85

ModelA:\
![image](https://github.com/neittien0110/MCU/assets/8079397/9facb5b4-40ad-44d3-8f54-08399f50087e)
![image](https://github.com/neittien0110/MCU/assets/8079397/2becfdcb-ed08-4fd4-8da6-dd248c5e3f05)

Mini LilyPadATtiny85 CJMCU\
![Mini LilyPadATtiny85 CJMCU](../assets/lilypad_attiny85.png)

## Mô tả

- CPU: ATTiny85
- Tần số xung nhịp: 16 mHz
- Flash memory: 5.87KB
- RAM: 512B

![image](https://github.com/neittien0110/MCU/assets/8079397/f137aa71-9ee6-4d03-a251-3789a85d10f5)

## Lập trình

- LED_BUILDIN  được nối với chân PB1 (đã kiểm tra) và nằm ở vị trí gần chân PB3

```arduino
#define LED_BUILDIN 1
```

- Với Arduino IDE:
  - Thêm thông tin về board mới:
    > <http://digistump.com/package_digistump_index.json>
  - Chọn board: Digispark (Default - 16 mhz)\
    ![Digispark (Default - 16 mhz)](../assets/digispark_default_16mhz.png)
- Với Visual Studio Code + PlatformIO
  - Chọn board:
    ![PlatformIO](https://github.com/neittien0110/MCU/assets/8079397/600f32e7-d18c-4c1a-875e-0da0960e843d)
  - Cấu hình PlatformIO

    ```yaml
    [env:digispark-tiny]
    platform = atmelavr
    board = digispark-tiny
    ; change microcontroller
    board_build.mcu = attiny85
    ; change MCU frequency
    board_build.f_cpu = 16500000L
    ```

- Điều khiển servo không sử dụng lib mặc định *Servo.h*. Có thể sử dụng lib [SoftServo](https://github.com/GyverLibs/SoftServo)

## Thông số chi tiết
>
> CPU: ATTiny85
> Tần số xung nhịp: 16 mHz

- Flash memory: 5.87KB
- RAM: 512B
- Nguồn cấp:
  - USB
  - Vin với dải điện áp 5-7.35V
- **Các chân vào ra phải làm việc ở điện áp 3.3V**
- Nhà sản xuất: [Digistump](http://digistump.com/products/1?utm_source=platformio.org&utm_medium=docs)

![Schematic](https://github.com/neittien0110/MCU/assets/8079397/0c558468-39e4-4956-878b-cea119279545)

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
- <https://linhkienvietnam.vn/module-node-mcu-32s-esp32-devkitc-dung-module-esp-wroom-32>
