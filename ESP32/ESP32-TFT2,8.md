# ESP32 màn hình vàng TFT 2.8"

## Mô tả

- Tên chính thức: ESP32-2432S028R
- MCU Module: ESP32-WROOM
- Màn hình: TFT 2.8" 240x320, cảm ứng điện trở
- SDCard, LED RGB (tích cực mức thấp), 

## Lập trình

- Ngôn ngữ lập trình:
- Công cụ lập trình: Arduino IDE, Visual Studio Code + PlatformIO
- LED_BUILDIN  được nối với chân .....\

> Các khai báo về màn hinh TFT được trích và đặt tên giống hệt các khai báo từ file [User_Setup.h](https://raw.githubusercontent.com/RuiSantosdotme/ESP32-TFT-Touchscreen/main/configs/User_Setup.h) trong bài viết [Getting Started with ESP32 Cheap Yellow Display Board – CYD (ESP32-2432S028R)](https://randomnerdtutorials.com/cheap-yellow-display-esp32-2432s028r/#config-file-windows-pc)

  ```C
   // PORTING đèn LED 3 màu, tích cực mức thấp
   #define LED_RGB_RDIN   04  // The Red   led is connected to GPIO4
   #define LED_RGB_GDIN   16  // The Green led is connected to GPIO16. Note: shared with TFT_MISO
   #define LED_RGB_BDIN   17  // The Blue  led is connected to GPIO17

  // PORTING màn hình hiển thị TFT thông qua giao thức SPI (HSPI)
   #define TFT_MISO       16  // lưu ý: dùng chung với led rgb
   #define TFT_MOSI       13  
   #define TFT_SCLK       14
   #define TFT_CS         15
   #define TFT_DC         02
   #define TFT_RST        12

   // PORTING chức năng chạm của màn hình TFT thông qua giao thức SPI (VSPI)
   #define XPT2046_MISO       39
   #define XPT2046_MOSI       32
   #define XPT2046_CLK        25
   #define XPT2046_CS         33
   #define XPT2046_IRQ        36

   // PORTING thẻ nhớ SDCard  thông qua giao thức SPI (VSPI). Tham khảo https://randomnerdtutorials.com/esp32-microsd-card-arduino/
   #define SDCARD_MISO        19
   #define SDCARD_MOSI        23
   #define SDCARD_SCK         18
   #define SDCARD_CS          05
   #define SDCARD_BACKLIGHT   21

   // PORTING quang trở LDR ở mặt trước, bên phải màn hình
   #define LDR                34

   // PORTING loa speaker, kết nối với loa/amplifier qua chân XH**1.25**mm
   #define SPEAKER            26

   // PORTING nút bấm BOOT
   #define BUTTON_BOOT        00

   // PORTING giao tiếp Serial ở jack P1
   #define TX_PIN            01
   #define RX_PIN            03

   // PORTING phần GPIO mở rộng, là các jack nối có tên P3, CN1 trên board. Lưu ý chân 22 chung nhau
  //                   ________________                           _______________________
   //    P3 gồm 3 pin  | 35 | 22 | 21 |     và  CN1 gồm 4 pin là  | GND | 22 | 27 | 3V3 |
   //                  ----------------                           ----------------------- 
   #define EX_GPIO          35
   #define EX_GPIO          22
   #define EX_GPIO          21
   #define EX_GPIO27        27

  ```


- Với Arduino IDE:
  - Chọn board: .................
- Với Visual Studio Code:
  - Chọn board: .........................
  - Cấu hình PlatformIO ([Nguồn tham khảo](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/Examples/Basics/2-TouchTest/platformio.ini))
  ```env
  [platformio]
  src_dir = .
  default_envs = cyd
  
  [env]
  platform = espressif32
  board = esp32dev
  framework = arduino
  lib_deps = 
  	bodmer/TFT_eSPI@^2.5.33
  	https://github.com/PaulStoffregen/XPT2046_Touchscreen.git#v1.4
  monitor_speed = 115200
  monitor_filters = esp32_exception_decoder
  upload_speed = 921600
  board_build.partitions=min_spiffs.csv
  build_flags =
  	-DUSER_SETUP_LOADED
  	-DUSE_HSPI_PORT
  	-DTFT_MISO=12
  	-DTFT_MOSI=13
  	-DTFT_SCLK=14
  	-DTFT_CS=15
  	-DTFT_DC=2
  	-DTFT_RST=-1
  	-DTFT_BL=21
  	-DTFT_BACKLIGHT_ON=HIGH
  	-DSPI_FREQUENCY=55000000
  	-DSPI_READ_FREQUENCY=20000000
  	-DSPI_TOUCH_FREQUENCY=2500000
  	-DLOAD_GLCD
  	-DLOAD_FONT2
  	-DLOAD_FONT4
  	-DLOAD_FONT6
  	-DLOAD_FONT7
  	-DLOAD_FONT8
  	-DLOAD_GFXFF
  
  [env:cyd]
  build_flags =
  	${env.build_flags}
  	-DILI9341_2_DRIVER
  
  [env:cyd2usb]
  build_flags =
  	${env.build_flags}
  	-DST7789_DRIVER
  	-DTFT_RGB_ORDER=TFT_BGR
  	-DTFT_INVERSION_OFF
  ```

## Thông số chi tiết
  
![Mặt trước](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2024/03/ESP32-Cheap-Yellow-Display-CYD-Board-ESP32-2432S028R-front.jpg?w=750&quality=100&strip=all&ssl=1)
![Ảnh](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2024/03/ESP32-Cheap-Yellow-Display-CYD-Board-ESP32-2432S028R-back-labeled.jpg?resize=768%2C390&quality=100&strip=all&ssl=1)

 - Nguồn tham khảo: <https://randomnerdtutorials.com/esp32-cheap-yellow-display-cyd-pinout-esp32-2432s028r>
 - 
### Tra cứu bản đồ địa chỉ bộ nhớ

## Demo

- [GitHub: WitnessMeNow/ESP32-Cheap-Yellow-Display với nhiều Examples trên PlatformIO](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display)
Cụm các bài tiếp làm quen dần 
- [Hướng dẫn với ArduinoIDE](https://randomnerdtutorials.com/cheap-yellow-display-esp32-2432s028r)
- [Hiển thị 1 nút bấm Toogle ON/OFF trên màn hình](https://randomnerdtutorials.com/touchscreen-on-off-button-cheap-yellow-display-esp32-2432s028r)\
  ![Hiển thị 1 nút bấm Toogle ON/OFF trên màn hình](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2024/03/Touchscreen-Press-On-Off-Button-Cheap-Yellow-Display-ESP32-2432S028R.jpg?w=750&quality=100&strip=all&ssl=1)
- [Sử dụng LVGL](https://randomnerdtutorials.com/lvgl-cheap-yellow-display-esp32-2432s028r/)
- [Kết nối với SDCard (cùng chân pin)](https://randomnerdtutorials.com/esp32-microsd-card-arduino/)

## Vỏ in 3D

## Mua

- [Shopee](https://shopee.vn/B%E1%BA%A3ng-M%E1%BA%A1ch-Ph%C3%A1t-Tri%E1%BB%83n-esp32-arduino-lvgl-wifi-bluetooth-2.8-240-*-320-M%C3%A0n-H%C3%ACnh-C%E1%BA%A3m-%E1%BB%A8ng-Th%C3%B4ng-Minh-2.8inch-lcd-tft-i.578443443.24202758643)
