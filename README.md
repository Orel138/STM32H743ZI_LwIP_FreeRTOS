<a name="readme-top"></a>

<h1 align="center">
  <br> STM32H743ZI LwIP FreeRTOS Template <br>
</h1>

<div align="center">

[![Orel138 - STM32H743ZI_LwIP_FreeRTOS](https://img.shields.io/static/v1?label=Orel138&message=STM32H743ZI_LwIP_FreeRTOS&color=blue&logo=github)](https://github.com/Orel138/STM32H743ZI_LwIP_FreeRTOS "Go to GitHub repo")
[![license](https://custom-icon-badges.demolab.com/github/license/Orel138/STM32H743ZI_LwIP_FreeRTOS?logo=law&logoColor=white)](https://github.com/Orel138/STM32H743ZI_LwIP_FreeRTOS/blob/main/LICENSE "license MIT")

[![STM32](https://img.shields.io/badge/STM32-message?style=flat&logo=stmicroelectronics&color=%2303234B)](https://st.com "STM32")
[![FreeRTOS](https://img.shields.io/badge/FreeRTOS-message?style=flat&logo=freertos&color=%23000000)](https://freertos.org/ "FreeRTOS")
[![LwIP](https://img.shields.io/badge/LwIP-message?style=flat&color=%2300A1E0)](https://savannah.nongnu.org/projects/lwip/ "LwIP")

</div>

<div align="center">
  <h4>
    <a href="#about">About</a> |
    <a href="#key-goals">Key Goals</a> |
    <a href="#architecture-overview">Architecture</a> |
    <a href="#requirements">Requirements</a> |
    <a href="#installation">Installation</a> |
    <a href="#usage">Usage</a> |
    <a href="#references">References</a> |
    <a href="#license">License</a>
  </h4>
</div>

<div align="center">
  <sub>Built by
  <a href="https://orel138.github.io">Orel138</a> and
  <a href="https://github.com/orel138/STM32H743ZI_LwIP_FreeRTOS/graphs/contributors">contributors</a>
</div>
<br>

## About

**STM32H743ZI LwIP FreeRTOS Template** is a ready-to-use project template for the NUCLEO-H743ZI microcontroller board featuring integrated LwIP TCP/IP stack and FreeRTOS real-time kernel. This project is generated using STM32CubeMX and provides a solid foundation for developing networked embedded applications.

The template comes pre-configured with Ethernet connectivity using DHCP for automatic IP address assignment. By default, the system is fully functional and responsive to network requests such as PING, making it an ideal starting point for developing networked IoT and embedded systems applications.

## Table of Contents

- [About](#about)
- [Key Goals](#key-goals)
- [Architecture Overview](#architecture-overview)
- [Project Structure](#project-structure)
- [Design Principles](#design-principles)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [References](#references)
- [License](#license)

## Key Goals

- Provide a production-ready template for STM32H743ZI with Ethernet connectivity
- Integrate LwIP TCP/IP stack for robust network communication
- Demonstrate FreeRTOS task-based architecture for embedded systems
- Ensure compatibility with STM32CubeMX and STM32Cube HAL
- Offer a foundation for networked embedded applications and IoT devices

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## Architecture Overview

### High-Level Architecture

```
┌─────────────────────────────────────────┐
│        Ethernet Interface (LAN8742)     │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│      STM32H743ZI Ethernet MAC           │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│    LwIP TCP/IP Stack (DHCP Client)      │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│      FreeRTOS Real-Time Kernel          │
└─────────────────────────────────────────┘
```

### Project Structure

```
.
├── Core/
│   ├── Inc/                 # Core header files
│   │   ├── main.h          # Main application header
│   │   ├── FreeRTOSConfig.h # FreeRTOS configuration
│   │   └── stm32h7xx_*.h   # STM32 configuration headers
│   └── Src/
│       ├── main.c          # Main application
│       ├── freertos.c      # FreeRTOS initialization
│       ├── stm32h7xx_it.c  # Interrupt handlers
│       └── system_stm32h7xx.c # System initialization
│
├── Drivers/
│   ├── CMSIS/              # ARM Cortex-M CMSIS headers
│   ├── BSP/                # Board Support Package
│   └── STM32H7xx_HAL_Driver/ # STM32H7xx HAL drivers
│
├── Middlewares/
│   └── Third_Party/
│       ├── FreeRTOS/       # FreeRTOS kernel
│       └── LwIP/           # LwIP TCP/IP stack
│
├── LWIP/
│   ├── App/                # LwIP application layer
│   │   ├── lwip.c          # LwIP initialization
│   │   └── lwip.h
│   └── Target/
│       ├── ethernetif.c    # Ethernet interface driver
│       ├── lwipopts.h      # LwIP configuration options
│       └── ethernetif.h
│
├── STM32CubeIDE/           # STM32CubeIDE project files
│   ├── STM32H743ZITX_FLASH.ld # Linker script
│   └── Debug/              # Build outputs
│
└── README.md               # This file
```

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## Design Principles

- **HAL-based Initialization**: Uses STM32Cube HAL for peripheral configuration and initialization
- **FreeRTOS Integration**: Task-based architecture for concurrent operations
- **LwIP TCP/IP Stack**: Lightweight and efficient network stack for embedded systems
- **DHCP Client**: Automatic IP address assignment from the network
- **Interrupt-Driven Architecture**: Efficient use of interrupts for network and system events
- **STM32CubeMX Generated**: Easily modifiable through STM32CubeMX for hardware customization

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## Requirements

### Hardware

- **NUCLEO-H743ZI Development Board** featuring STM32H743ZI microcontroller
- **Ethernet Connection**: RJ45 network cable to connect to a network with DHCP server
- **Power Supply**: USB or external power (5V nominal)
- **Optional**: Serial interface for debugging and console output

### Software

- STM32CubeMX (for hardware configuration modifications)
- STM32CubeIDE or compatible ARM toolchain (GCC, Keil µVision, IAR, etc.)
- FreeRTOS kernel (included)
- STM32Cube HAL for H7 series (included)
- LwIP TCP/IP stack (included)

### Development Environment

- Git
- STM32CubeIDE (recommended) or VS Code with ARM tools support
- Serial terminal software (e.g., PuTTY, Minicom) for debugging output

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## Installation

### Clone the Repository

```bash
git clone https://github.com/Orel138/STM32H743ZI_LwIP_FreeRTOS.git
cd STM32H743ZI_LwIP_FreeRTOS
```

### Build and Flash

#### Using STM32CubeIDE

1. Open STM32CubeIDE
2. Import the project:
   - File → Import → Existing Projects into Workspace
   - Select the cloned directory
   - Click Finish
3. Select the project and build:
   - Project → Build Project (or Ctrl+B)
4. Connect the NUCLEO-H743ZI board via USB
5. Flash the firmware:
   - Run → Run (or F11)
   - Select STM32 MCU C/C++ Application
   - Click OK

#### Using Command Line (GCC)

```bash
cd STM32CubeIDE
make -f makefile
```

Flash using ST-Link:
```bash
st-flash write Debug/STM32H743ZI_LwIP_FreeRTOS.bin 0x08000000
```

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## Usage

### Running the Template

1. **Power on the board** via USB or external power supply
2. **Connect to Ethernet** using an RJ45 cable to a network with active DHCP server
3. **Wait for network initialization** (typically 2-3 seconds)
4. **Verify connectivity** by pinging the board from your host machine:
   ```bash
   ping <board-ip-address>
   ```

### Network Configuration

The board automatically obtains an IP address via DHCP. To determine the assigned IP address:

- **Option 1**: Connect a serial terminal to the USB interface and monitor the console output
- **Option 2**: Check your router's DHCP client list for "STM32" or similar device name
- **Option 3**: Use network scanning tools (e.g., `arp-scan`, Wireshark) to detect new devices

### Default Behavior

- Ethernet interface initializes automatically on startup
- DHCP client requests and obtains IP address from network
- System responds to ICMP PING requests
- FreeRTOS scheduler manages system tasks
- Ready for application development and extension

### Extending the Template

To add custom functionality:

1. **Add FreeRTOS Tasks**: Edit `Core/Src/freertos.c`
   ```c
   // Create custom task
   xTaskCreate(myTask, "MyTask", 256, NULL, tskIDLE_PRIORITY + 1, NULL);
   ```

2. **Add Network Functionality**: Edit `LWIP/App/lwip.c`
   - Implement HTTP server
   - Add TCP/UDP sockets
   - Create custom network applications

3. **Modify Hardware Configuration**: Use STM32CubeMX to:
   - Enable additional peripherals
   - Configure GPIO pins
   - Adjust clock settings
   - Modify interrupt priorities

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## References

- [STM32H743ZI Datasheet](https://www.st.com/resource/en/datasheet/stm32h743zi.pdf)
- [STM32H743/753 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0433-stm32h742-stm32h743-753-and-stm32h750-value-line-advanced-arm-based-32-bit-mcus-stmicroelectronics.pdf)
- [STM32Cube MCU Overall Offer](https://github.com/STMicroelectronics/STM32Cube_MCU_Overall_Offer)
- [FreeRTOS Kernel Documentation](https://www.freertos.org/Documentation/161204_Mastering_the_FreeRTOS_Real_Time_Kernel-A_Hands-On_Tutorial_Guide.pdf)
- [LwIP Documentation](https://savannah.nongnu.org/projects/lwip/)
- [NUCLEO-H743ZI Board User Manual](https://www.st.com/resource/en/user_manual/um2407-stm32h7-nucleo144-board-stmicroelectronics.pdf)

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

## License

This project is released under the [MIT License](LICENSE).

© [Orel138](https://github.com/Orel138)

<p align="right"><a href="#readme-top">~~~~~ back to top ~~~~~</a></p>

> [!TIP]
> If you find this project useful, consider giving it a ⭐.
> It is the simplest way to show support and helps the project grow.
