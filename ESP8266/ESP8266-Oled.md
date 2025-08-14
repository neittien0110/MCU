# ESP8266 NodeMCU + OLED 0,96"


## Thông số

- Điện áp hoạt động: 3.3V
- Điện áp ngõ vào: 7-12V
- Chân I/O kỹ thuật số (DIO): 16
- Chân Analog (ADC): 1
- UART: 1
- SPI: 1
- I2C: 1
- Driver. CH340G
- Flash memory: 4 MB
- SRAM: 64 KB
- Clock speed: 80 MHZ
- Vi xử lý: Tensilica 32-bit RISC CPU Xtensa LX106
- Kích thước: 59mm * 31mm
- OLED:
  - 0.96 inch
  - Màu: Yellow Blue
  - Voltage: 3.3V-5V DC
 	- Perspective:>160 °
	- High resolution: 128x64
	- Driver lC: SSD1306

## Lập trình

### Với OLED
```C
// Khai báo các thư viện cần thiết cho màn hình OLED
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

// Định nghĩa màn hình OLED
#define SCREEN_WIDTH 128    // Chiều rộng màn hình OLED, tính bằng pixels
#define SCREEN_HEIGHT 64    // Chiều cao màn hình OLED, tính bằng pixels
#define OLED_RESET -1       // Chân Reset màn hình (thường là -1)

// Khởi tạo màn hình OLED. Địa chỉ I2C phổ biến cho ESP8266 là 0x3C
// Chân SDA và SCL được chỉ định là D6 và D5
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

void setup() {
  // Khởi tạo giao thức I2C với các chân mới
  Wire.begin(D5, D6);  // SCL là D5, SDA là D6

  // Khởi tạo màn hình OLED.
  if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    Serial.println(F("SSD1306 allocation failed"));
    for(;;); // Vòng lặp vô hạn nếu khởi tạo thất bại
  }
```

## Mua sắm
 - [Shopee](https://shopee.vn/M%C3%B4-%C4%91un-ESP8266-NodeMCU-v%E1%BB%9Bi-m%C3%A0n-h%C3%ACnh-OLED-0-96--i.52631548.24585286141)
 - [Shopee](https://shopee.vn/B%E1%BA%A3ng-RINABONSINY-ESP8266-B%E1%BA%A3ng-hi%E1%BB%83n-th%E1%BB%8B-OLED-NodeMCU-M%C3%B4-%C4%91un-hi%E1%BB%83n-th%E1%BB%8B-CH340-0-96-inch-%C4%90i%E1%BB%87n-t%E1%BB%AD-DIY-i.1263757561.43361725484?sp_atk=8fa2c983-f598-4d91-88f7-8ca516b8e330&xptdk=8fa2c983-f598-4d91-88f7-8ca516b8e330)
 - 
