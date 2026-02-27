# FPGA 3D GPU Architecture Showcase (UIUC ECE385)

This repository is a **portfolio showcase** of an FPGA-based 3D rendering pipeline implemented in SystemVerilog with embedded C firmware.

## 30-Second Overview
- **What this is:** A hardware/software co-design for real-time 3D cube rendering on FPGA.
- **Hardware side:** Custom RTL modules for triangle/scanline-oriented display logic and HDMI output path.
- **Software side:** Embedded C firmware that transforms 3D geometry and streams raster data through AXI-Lite.
- **Interface:** AXI-based control/data path between firmware and display IP.

## Key Highlights
- SystemVerilog IP centered around `hdmi_text_controller_v1_0` and supporting display modules.
- HDMI transmitter RTL (`encode`, `serdes_10_to_1`, `srldelay`, top wrapper).
- Firmware-side rasterization and frame update flow (`main.c`, `rasteriser.c`, `gpu_axi_lite.c`).
- Board pin constraints captured in XDC.

## Repository Layout
```text
rtl/
  gpu_core/        # Core display/GPU-related RTL modules
  hdmi_tx/         # HDMI transmit path RTL
  testbench/       # Focused testbench source
sw/
  firmware/        # Embedded C firmware (render + AXI interface + USB input)
constraints/
  mb_usb_hdmi_top.xdc
docs/
  UIUC ECE 385 Final Report.pdf
assets/            # Optional demo images/videos for portfolio presentation
```

## Start Here (Recruiter Path)
1. Read `docs/UIUC ECE 385 Final Report.pdf` for system context and results.
2. Open `rtl/gpu_core/hdmi_text_controller_v1_0.sv` for the top-level display IP shell.
3. Open `sw/firmware/main.c` for the end-to-end render/control loop.
4. Review `rtl/hdmi_tx/` for the HDMI serialization path.

## Notes
- This is intentionally curated as a **showcase repository** (not a full Vivado rebuild environment).
- Tool-generated build artifacts, caches, and project metadata were removed to maximize readability.

## License
See `LICENSE`.
