# ESP32_Dev_Kit_V1

## Mô tả 

- Module CPU: ESP-WROOM-32
- Kích cỡ trùng khớp với câc loại NodeMCU phổ biến ở VN
- Lưu ý: có 2 loại cổng usb **Type C** và *Micro USB*

![image](https://github.com/neittien0110/MCU/assets/8079397/50128af6-1523-4dd5-851a-57714fe52314)

## Lập trình

- Hỗ trợ arduinoide mixly, Mind +, Python và các phần mềm lập trình khác
- LED_BUILDIN  được nối với chân D2 (đã đo bằng đồng hồ)\

  ```C
  #define LED_BUILDIN 2
  ```

- Với Arduino IDE:
  - Chọn board: DOIT esp32 devkit v1
- Với Visual Studio Code:
  - Chọn board: ![image](https://github.com/neittien0110/MCU/assets/8079397/5ee068bc-0274-446e-a262-9aab80e7654b)
  - Cấu hình PlatformIO\

    ```yaml
    [env:esp32doit-devkit-v1]
    build_type = release
    platform = espressif32
    board = esp32doit-devkit-v1
    framework = arduino
    monitor_speed = 9600
    ```

- Dùng esptool \

  ```dos
  >python esptool.py -p COM11 flash_id
  esptool.py v4.6-dev
  Serial port COM11
  Connecting....
  Detecting chip type... Unsupported detection protocol, switching and trying again...
  Connecting......
  Detecting chip type... ESP32
  Chip is ESP32-D0WD-V3 (revision v3.0)
  Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
  Crystal is 40MHz
  MAC: c8:f0:9e:51:f7:94
  Uploading stub...
  Running stub...
  Stub running...
  Manufacturer: 5e
  Device: 4016
  Detected flash size: 4MB
  Hard resetting via RTS pin...
  ```

## Thông số chi tiết

- Mô hình bảng phát triển: ESP32-DevKitC-32
- Mô hình mô-đun: ESP32-WROOM-32
- Chip điều khiển chính: ESP32-DOWDQ6-V3 lõi kép 32bit MCU Tích hợp Wifi, Bluetooth,
- Tích hợp 520-kbsram, 448-kbrom16-kbsraminrtc
- Bộ nhớ ngoài: 4Mb
- Chip điều khiển USB-Serial: ch340c
- Nguồn cấp:
  - Chân **Vin** cho phép dải điện áp **5-12V** (Phiên bản pin đầu vào tối đa 5.5V)
  - Cổng USB
  - Nguồn điện 3.3V trực tiếp vào các chân pin 3.3V (chú ý không được bảo vệ)
- Kích thước: 52*28mm
- Trọng lượng khoảng 9.5g

![image](https://github.com/neittien0110/MCU/assets/8079397/71912ac5-488c-45be-9af2-06452e94a2cd)

### Tra cứu bản đồ địa chỉ bộ nhớ

<https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf>
![image](https://github.com/neittien0110/MCU/assets/8079397/0de15693-f3c2-48f1-9a77-947fa26d5d95)

## Demo

Using RC522 NFC 13.56MHz with DOIT ESP32 DevKit.\
[![Youtube: Using RC522 NFC 13.56MHz with DOIT ESP32 DevKit](https://i9.ytimg.com/vi_webp/VQAy33XYFEY/mq2.webp?sqp=CJjApa0G-oaymwEmCMACELQB8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGGUgWChUMA8=&rs=AOn4CLAsOEsgZZ4WkLEqslLUiYXim1rbyQ)](https://www.youtube.com/watch?v=VQAy33XYFEY)
![image](https://github.com/neittien0110/MCU/assets/8079397/b65315be-fa72-4379-99aa-da04ed98eda6)

```C
#include <Arduino.h>
#include <SPI.h>
#include <MFRC522.h>
#define SS_PIN 21     //   SS/SDA
#define RST_PIN 0     //   Reset

MFRC522 rfid(SS_PIN, RST_PIN); // Instance of the class
MFRC522::MIFARE_Key key; 
// Init array that will store new NUID 
byte nuidPICC[4];

/**
	* Helper routine to dump a byte array as hex values to Serial. 
	*/
void printHex(byte *buffer, byte bufferSize) {
	for (byte i = 0; i < bufferSize; i++) {
	Serial.print(buffer[i] < 0x10 ? " 0" : " ");
	Serial.print(buffer[i], HEX);
	}
}
/**
	* Helper routine to dump a byte array as dec values to Serial.
	*/
void printDec(byte *buffer, byte bufferSize) {
	for (byte i = 0; i < bufferSize; i++) {
	Serial.print(buffer[i] < 0x10 ? " 0" : " ");
	Serial.print(buffer[i], DEC);
	}
}
void setup() { 
	Serial.begin(9600);
	SPI.begin(); // Init SPI bus
	rfid.PCD_Init(); // Init MFRC522 
	for (byte i = 0; i < 6; i++) {
	key.keyByte[i] = 0xFF;
	}
	Serial.println(F("This code scan the MIFARE Classsic NUID."));
	Serial.print(F("Using the following key:"));
	printHex(key.keyByte, MFRC522::MF_KEY_SIZE);
}
	
void loop() {
	// Reset the loop if no new card present on the sensor/reader. This saves the entire process when idle.
	if ( ! rfid.PICC_IsNewCardPresent())
	return;
	// Verify if the NUID has been readed
	if ( ! rfid.PICC_ReadCardSerial())
	return;
	Serial.print(F("PICC type: "));
	MFRC522::PICC_Type piccType = rfid.PICC_GetType(rfid.uid.sak);
	Serial.println(rfid.PICC_GetTypeName(piccType));
	// Check is the PICC of Classic MIFARE type
	if (piccType != MFRC522::PICC_TYPE_MIFARE_MINI && 
	piccType != MFRC522::PICC_TYPE_MIFARE_1K &&
	piccType != MFRC522::PICC_TYPE_MIFARE_4K) {
	Serial.println(F("Your tag is not of type MIFARE Classic."));
	return;
	}
	if (rfid.uid.uidByte[0] != nuidPICC[0] || 
	rfid.uid.uidByte[1] != nuidPICC[1] || 
	rfid.uid.uidByte[2] != nuidPICC[2] || 
	rfid.uid.uidByte[3] != nuidPICC[3] ) {
	Serial.println(F("A new card has been detected."));
	// Store NUID into nuidPICC array
	for (byte i = 0; i < 4; i++) {
		nuidPICC[i] = rfid.uid.uidByte[i];
	}
	
	Serial.println(F("The NUID tag is:"));
	Serial.print(F("In hex: "));
	printHex(rfid.uid.uidByte, rfid.uid.size);
	Serial.println();
	Serial.print(F("In dec: "));
	printDec(rfid.uid.uidByte, rfid.uid.size);
	Serial.println();
	}
	else Serial.println(F("Card read previously."));
	// Halt PICC
	rfid.PICC_HaltA();
	// Stop encryption on PCD
	rfid.PCD_StopCrypto1();
}
```

## Vỏ in 3D

- <https://www.thingiverse.com/thing:4125952>. Với loại Type C thì hơi kích ở 4 góc, hàng lỗ chân pin

## Mua

- Lazada: <https://www.lazada.vn/products/i1962797806-s9056915561.html?urlFlag=true&mp=1&spm=spm%3Da2o4n.order_details.item_title.1>
- <https://linhkienvietnam.vn/module-node-mcu-32s-esp32-devkitc-dung-module-esp-wroom-32>
