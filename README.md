# 🔍 Sobel Edge Detection using Verilog on FPGA

## 🧾 Introduction

This project implements the **Sobel Edge Detection** algorithm in Verilog HDL, targeting real-time image processing on FPGA platforms such as the **ZedBoard** and **Nexys-4**. The Sobel operator is used to detect edges by calculating the gradient magnitude of the image intensity in horizontal and vertical directions.
The design focuses on **hardware efficiency**, modularity, and scalability for embedded image processing applications. This setup is suitable for deployment in **FPGA-based vision systems**, with scope for expansion to live video streams using VDMA.

---
## 📁 File Descriptions

| File Name           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `conv1.v`           | Performs 3x3 convolution using Sobel kernels (Gx, Gy) to detect edges.      |
| `lineBuffer.v`      | Buffers incoming image rows to form a sliding 3x3 window.                   |
| `imageControl.v`    | Generates synchronization and valid signals for streaming data.             |
| `imageProcessTop.v` | Integrates convolution, buffering, and control modules.                     |
| `tb.v`              | Testbench to simulate the full design and validate functionality.           |

---
## 💻 Hardware & Tool Requirements

- **FPGA Development Board**: ZedBoard (Zynq-7000) or Nexys-4 DDR (Artix-7)
- **Vivado Design Suite 2019.2 or later**
  - Includes Verilog synthesis and simulation tools
  - Includes **Xilinx High-Level Synthesis (HLS)** for future enhancements
- **Optional**: AXI4-Stream interface for VDMA/camera input (for real-time applications)
- **Simulation Tool**: Vivado Simulator or ModelSim

---
## 🔄 Methodology

1. **Grayscale Image Input**: The image is assumed to be grayscale, streamed pixel by pixel.
2. **Line Buffering**: The `lineBuffer` module stores three rows of pixels at a time.
3. **3x3 Window Formation**: A 3x3 kernel is dynamically created for each pixel using line buffers.
4. **Sobel Convolution**: The `conv1` module applies Gx and Gy masks and computes the edge magnitude.
5. **Control Logic**: `imageControl.v` manages the streaming process and asserts valid outputs.
6. **Integration**: `imageProcessTop.v` connects all functional blocks and prepares output.
7. **Simulation**: Run `tb.v` to simulate and verify the logic before FPGA synthesis.

---

## ✅ Conclusion
This project successfully demonstrates the **hardware implementation of Sobel Edge Detection** using Verilog. It is structured for real-time processing and hardware acceleration, making it ideal for deployment in embedded vision applications. The modular design allows easy expansion to handle color images, live video feeds via VDMA, and integration with high-level systems using HLS.
Feel free to extend or adapt this project to fit your own image processing pipelines or FPGA platforms.
