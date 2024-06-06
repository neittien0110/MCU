# ESP32-C3 SUPER MINI

![ESP32-C3 Super mini](../assets/ESP32-C3_SuperMini.png)

## Mô tả

## Lập trình

- Ngôn ngữ lập trình:
- Công cụ lập trình: Arduino IDE, Visual Studio Code + PlatformIO
- LED_BUILDIN  được nối với chân .....\
  
  ```C
  #define LED_BUILDIN 8
  ```

- Với Arduino IDE:
  - Chọn board: **ESP32C3 Dev Module**
  - Cấu hình: **USB CDC On Boat: "Enabled"**\
    ![image](https://github.com/neittien0110/MCU/assets/8079397/f7cd5deb-49fc-4d84-b80d-479d8028c8c4)

- Với Visual Studio Code:
  - Chọn board: .........................
  - Cấu hình PlatformIO\

  ```env
  ```

## Thông số chi tiết

- Cpu: ESP32-C3, bộ xử lý lõi đơn RISC-V 32 bit
- Tần số hoạt động: 160 MHz
- Tần số chính: 160M
- Sram: 400KB
- Rom: 374KB
- Adc: 2 * 12-bit SARADC, 6 kênh
- Wifi: Giao thức 802.11b / g / n, 2.4GhHz, hỗ trợ chế độ Trạm, Chế độ SoftAP, Chế độ SoftAP + Trạm, chế độ kết hợp
- Bluetooth: BT 5.0
- Công suất tiêu thụ: Tiêu thụ điện năng khi ngủ sâu khoảng 43 μ A
- Giàu tài nguyên chip: 400KB SRAM, 384KB ROM
- Giao diện phong phú: 1xI2C, 1xSPI, 2xUART, 11xGPIO (PWM), 4xADC
- Các thành phần một mặt, thiết kế gắn trên bề mặt
- Vẻ ngoài cổ điển, thích hợp cho các thiết bị đeo và các dự án nhỏ
- Các tính năng bảo mật đáng tin cậy: Trình tăng tốc phần cứng mã hóa hỗ trợ AES-128 / 256, băm, RSA, HMAC, chữ ký kỹ thuật số và khởi động an toàn
- Đèn LED xanh trên bo mạch, chân GPIO8
- Kích thước: 22,52x18mm

![Mặt trước](https://github.com/neittien0110/MCU/assets/8079397/4652a092-a04b-4c0d-b42b-579035a3d77d)
![Mặt sau](https://github.com/neittien0110/MCU/assets/8079397/5c3f065d-b669-4e43-a7e0-8004af4285d9)


### Schematic

![ESP32 C3 Supermini Schematic](https://github.com/neittien0110/MCU/assets/8079397/fde37cb3-ab8d-448a-babf-54226d073937)

## Demo

```C
#define LED_BUILTIN 8
void setup() {
  // put your setup code here, to run once:
  pinMode(LED_BUILTIN, OUTPUT);    
  pinMode(GPIO_NUM_10, INPUT_PULLUP);
}
void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(LED_BUILTIN, digitalRead(GPIO_NUM_10));
  delay(1);
}
```
![image](https://github.com/neittien0110/MCU/assets/8079397/77a3498e-b15c-41f3-9015-f3805dc30e27)
![image](https://github.com/neittien0110/MCU/assets/8079397/d172e777-00df-47dd-b28b-cd855fca43e5)
![image](https://github.com/neittien0110/MCU/assets/8079397/44c03571-aa02-4551-87e8-0c83f9b59a22)





## Vỏ in 3D

## Mua

- [Shopee 1](https://shopee.vn/-M%C3%A3-CLS2404A-gi%E1%BA%A3m-30k-%C4%91%C6%A1n-150k-B%E1%BA%A3ng-M%E1%BA%A1ch-Ph%C3%A1t-Tri%E1%BB%83n-ESP32-C3-MINI-ESP32-ESP32-Chuy%C3%AAn-D%E1%BB%A5ng-i.812409307.23349728339)
- [Shopee 2](https://shopee.vn/B%E1%BA%A3ng-M%E1%BA%A1ch-Ph%C3%A1t-Tri%E1%BB%83n-esp32-c3-esp32-esp32-wifi-bluetooth-i.578443443.24400570619)
