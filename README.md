<img width="1920" height="1200" alt="Screenshot (3473)" src="https://github.com/user-attachments/assets/5eced7dd-7ed7-4e8c-9e21-cb1e532c744b" /># LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="Screenshot (3472)" src="https://github.com/user-attachments/assets/9baf56bc-8e62-4e48-a5d1-3b53a23f32c9" />

2. Click **File → New STM32 Project**.
   <img width="1920" height="1200" alt="Screenshot (3473)" src="https://github.com/user-attachments/assets/862c8d0a-8d10-4cab-ac35-9451683cacd9" />
   <img width="1920" height="1200" alt="Screenshot (3474)" src="https://github.com/user-attachments/assets/793b2dc9-d913-49e6-9313-d8545e4cd132" />


3. Select the **target microcontroller** or board and click **Next**.
   <img width="1920" height="1200" alt="Screenshot (3476)" src="https://github.com/user-attachments/assets/440d6d52-f65c-4cb6-a4f9-7bf38d368e73" />



4. Name the project.
   
5. The corresponding `.ioc` file will be generated automatically.
  <img width="1920" height="1200" alt="Screenshot (3479)" src="https://github.com/user-attachments/assets/1ae98ef3-4133-499a-91d8-fc8044753b75" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1200" alt="Screenshot (3479)" src="https://github.com/user-attachments/assets/29c362e4-1ee0-4899-96ef-1bb80953527b" />
   <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/c023ad4f-3c87-4d1f-854a-4b3a94d53d27" />



7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1920" height="1200" alt="Screenshot (3479)" src="https://github.com/user-attachments/assets/8ccd8303-e27e-4bc2-a682-76a44a96e3cd" />

 
8. Edit the generated main program as required.
   <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/ab1ae5da-3223-441a-a396-368e4cbe14e8" />



9. Click **Project → Build All**.
    <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/7e700737-373e-404a-9698-7925d651449f" />

10. Link the **HEX file** using the post-build process.
    <img width="1433" height="639" alt="image" src="https://github.com/user-attachments/assets/1c9f0b08-bb42-440c-a592-6520a13de82b" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/7e700737-373e-404a-9698-7925d651449f" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="1056" height="792" alt="image" src="https://github.com/user-attachments/assets/0002aa0d-edee-42cb-96a1-b34544ed441b" />

CASE 2: LED OFF
<img width="1056" height="792" alt="image" src="https://github.com/user-attachments/assets/9e9b03c0-dea1-4e59-9ffd-4d31e113865f" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
