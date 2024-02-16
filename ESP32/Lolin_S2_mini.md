![image](https://github.com/neittien0110/MCU/assets/8079397/7433a485-2b2f-4c4f-be65-aca73ecece0a)# Lolin S2 Mini
 ![front](https://www.wemos.cc/en/latest/_static/boards/s2_mini_v1.0.0_1_16x16.jpg)
 ![rear](https://www.wemos.cc/en/latest/_images/s2_mini_v1.0.0_2_16x16.jpg)
 
## Mô tả 
- Module CPU: ESP32-S2F
- Kích thước: 34.3 x 25.4 mm
- Cổng nạp và nguồn cấp: USB Type C

![image](https://www.wemos.cc/en/latest/_images/s2_mini_v1.0.0_4_16x9.jpg)

## Lập trình
- Hỗ trợ MicroPython, CircuitPython 
- LED_BUILDIN  màu xanh dương được nối với chân 15 

```C
#define LED_BUILDIN 15
```

- Với Arduino IDE:
  - Chọn board: LOLIN S2 Mini \
 ![LOLIN S2 Mini](https://github.com/neittien0110/MCU/assets/8079397/4b1d4ec0-1c73-496e-97b4-28ca0eaae8c3)

- Với Visual Studio Code:
  - Chọn board: ![image](![image](https://github.com/neittien0110/MCU/assets/8079397/f3888ef4-1e7d-43d8-9db7-f72375b806c1)
  - Cấu hình PlatformIO

```env
[env:lolin_s2_mini]
platform = espressif32
board = lolin_s2_mini
```

> **LƯU Ý KHI NẠP CODE** \
Cổng COM để napcode chỉ xuất hiện khi S2-mini rơi vào trạng thái nạp code lúc khởi động.  
Trong cửa số Device Management ban đầu sẽ không có cổng COM nạp code.\
![image](https://github.com/neittien0110/MCU/assets/8079397/7173f279-b22e-41ca-b5da-b7482cb5949e)
1. Kết nối S2 mini với máy tính bằng dây USB Type-C
2. Bấm và giữ phím Boot và phím Reset đồng thời.
3. Nhả tay khỏi phím Reset, nhưng vẫn giữ phím Boot.
   Cổng COM nạp code sẽ xuất hiện
5. Nạp code như thông thường
6. Kết thúc việc nạp code trên Arduino IDE có thể sẽ có thông báo sau. Không sao cả, phải bấm nút reset cứng trên bảng mạch là xong.
```dos
Writing at 0x0004b470... (97 %)
Writing at 0x0004bf14... (98 %)
Writing at 0x0004cae9... (100 %)
Wrote 249632 bytes (144079 compressed) at 0x00010000 in 1.9 seconds (effective 1051.3 kbit/s)...
Hash of data verified.
```

## Thông số chi tiết
- Mô hình bảng phát triển: LOLIN D1 mini shields
- Module CPU: ESP32-S2F
- Kích thước: 34.3 x 25.4 mm
- Cổng nạp và nguồn cấp: USB Type C
- Tích hợp 2MB PSRAM
- Bộ nhớ ngoài: 4MB
- Nặng 2.4g
- Chip điều khiển USB-Serial: ch340c
- Nguồn cấp:
  - Chân **Vin** cho phép dải điện áp 5-12V (Phiên bản pin đầu vào tối đa 5.5V)
  - Cổng USB
  - Nguồn điện 3.3V trực tiếp vào các chân pin 3.3V (chú ý không được bảo vệ)
- Kích thước: 52*28mm
- Trọng lượng khoảng 9.5g

![image](![image](https://github.com/neittien0110/MCU/assets/8079397/86295369-7803-4ea9-89ad-a823bc3dba39)

### Tra cứu bản đồ địa chỉ bộ nhớ

<https://www.espressif.com/sites/default/files/documentation/esp32-s2_datasheet_en.pdf>


## Demo

## Tham khảo
 - <https://www.wemos.cc/en/latest/s2/s2_mini.html>
  
## Mua
- Lazada: <https://www.lazada.vn/products/i1962797806-s9056915561.html?urlFlag=true&mp=1&spm=spm%3Da2o4n.order_details.item_title.1>
- https://linhkienvietnam.vn/module-node-mcu-32s-esp32-devkitc-dung-module-esp-wroom-32
