# ESP32-WROOM-32
- Là module MCU, 4MB Flash, 
- Kích thước vật lý: 18 mm × 25.5 mm × 3.10 mm
  ![image](https://github.com/user-attachments/assets/745d9d40-e525-4205-a697-75329b0204da)
  - Khoảng cách pin: 1.27 mm
- Thiết kế board chuyển đổi từ pin 1.27 mm sang pin 2.54mm. Chỉ cần 2 thao tác
  - Cấp nguồn qua các pin 3v3, GND
  - Các chân EN, IO0 phải có 2 trạng thái logic rõ ràng. Đơn giản nhất là thiết kế pin nối với nút bấm và điện trở kéo ngoài.
    - Logic 1: hoạt động bình thường
    - Logic 0: nạp chương trình.
    > Đã thử nghiệm EN ở trạng thái HiZ thì ESP32 không hoạt động.
    ![20241105_192521](https://github.com/user-attachments/assets/3d98d2af-d117-4591-b34d-d05f2cd93765)
  - [Thiết kế Wrapper](https://easyeda.com/editor#id=508dd84037644c9a8733925a4745d4fd)\
    ![Schematic](https://github.com/user-attachments/assets/a43bae9d-c3d9-4c7c-9b48-3df8627f54f9)
    ![PCB](https://github.com/user-attachments/assets/2df9883e-cfdd-42e8-b1e1-58b86c6bd898)
    ![3D](https://github.com/user-attachments/assets/0868797f-6cb5-46a8-adf7-0a51f226e525)
 
  

- [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32_datasheet_en.pdf)
