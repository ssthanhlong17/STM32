# STM32F103C8T6 - GPIO LED Control (PC13)

## Giới thiệu

LED trên board được kết nối với chân **PC13** và hoạt động theo nguyên lý **active-low**:
- PC13 = LOW → LED sáng  
- PC13 = HIGH → LED tắt  

---

## Nguyên lý hoạt động

Để điều khiển LED, vi điều khiển thực hiện các bước:

1. Bật clock cho GPIOC
2. Cấu hình chân PC13 là ngõ ra (Output Push-Pull)
3. Ghi mức logic LOW/HIGH để bật/tắt LED

---

## Thanh ghi sử dụng

### 1. RCC_APB2ENR (mục 7.3.4 tài liệu[2])
- Chức năng: Cấp xung clock cho các ngoại vi trên bus APB2
- GPIOC thuộc APB2 nên cần bật clock
- Bit sử dụng:
  - Bit 4 (IOPCEN): Enable clock GPIOC 

---

### 2. GPIOC_CRH (mục 9.2.2 tài liệu[2])
- Chức năng: Cấu hình mode cho các chân PC8 → PC15
- PC13 nằm tại bit [23:20]
- Cấu hình sử dụng:
  - Output Push-Pull
  - Tốc độ 2 MHz

---

### 3. GPIOC_BSRR ((mục 9.2.5 tài liệu[2]))
- Chức năng: Set/Reset chân GPIO nhanh
- Cơ chế:
  - Bit 0–15: SET chân (HIGH)
  - Bit 16–31: RESET chân (LOW)

---


