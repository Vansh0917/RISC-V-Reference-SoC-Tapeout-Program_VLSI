# RISC-V Reference SoC Tapeout Program

## Week 0: Getting Started with Digital VLSI SoC Design and Planning

*Date: September 20, 2025*

## Table of Contents
1. [Program Overview](#program-overview)
2. [SoC Design Flow](#soc-design-flow)
3. [Tool Installation & Verification](#tool-installation--verification)
4. [Application Domains](#application-domains)
5. [Week 0 Accomplishments](#week-0-accomplishments)

## Program Overview

The RISC-V Reference SoC Tapeout Program is a comprehensive 20-week initiative designed to provide hands-on experience in complete chip development - from RTL design to actual silicon fabrication. This program demonstrates an end-to-end tapeout cycle for a RISC-V Reference SoC using industry-standard EDA tools and open-source PDKs.

### Week 0 Objectives
- Understand the complete SoC design flow from RTL to GDSII
- Set up and verify the EDA tool environment using OpenLane VDI
- Successfully install and verify essential EDA tools
- Explore application domains for RISC-V SoCs

## SoC Design Flow

The design methodology follows a structured approach with four main stages, each representing different abstraction levels from high-level modeling to physical implementation.

### Design Flow Architecture

<img width="1919" height="1079" alt="Screenshot 2025-09-20 122053" src="https://github.com/user-attachments/assets/0f510601-94b3-4720-9fe6-8cbed9aed676" />

The complete flow consists of four stages operating at **100MHz to 130MHz** frequency range:

#### Stage O1 = O2: Chip Modeling and RTL Development
- **O1 (GCC)**: Cross-compilation support and software development environment
- **O2 (Specs - C Model)**: High-level behavioral modeling using C language for verification
- **Testbench Development**: Comprehensive verification environment in C language

#### Stage O3: SoC Integration
- **Gate Level Netlist**: Post-synthesis netlist (synth P1)  
- **Macros (synth RTL)**: Synthesized RTL macro blocks
- **Analog IPs (func RTL)**: Functional RTL models for analog components
- **GPIOs**: General Purpose Input/Output interfaces
- **SoC Integration**: Complete system assembly and verification

#### Stage O4: Physical Implementation
- **Floorplanning**: Chip area planning and block placement
- **Placement**: Component positioning optimization  
- **CTS (Clock Tree Synthesis)**: Clock distribution network
- **Routing**: Physical interconnection implementation
- **GDSII Generation**: Final layout database for fabrication

### RTL to Silicon Implementation

<img width="1919" height="1034" alt="Screenshot 2025-09-20 121911" src="https://github.com/user-attachments/assets/6a22521c-4897-4899-9931-505477e48d15" />

The complete RTL2GDS flow encompasses front-end design, physical design, back-end verification, and tapeout processes.

## Tool Installation & Verification

This section documents the successful installation and verification of essential EDA tools in the OpenLane VDI environment.

### Tool Usage Commands

#### Basic Tool Verification
```bash
# Tool version checks
yosys --version
iverilog -V  
gtkwave --version
magic --version
ngspice --version

# System information
uname -a
lsb_release -a
```

#### Daily Development Commands
```bash
# Basic Verilog simulation flow
iverilog -o design design.v testbench.v
./design
gtkwave waveform.vcd

# Yosys synthesis check
yosys -p "read_verilog design.v; synth; show"

# OpenLane flow
cd $HOME/OpenLane && make mount

# Magic VLSI layout
magic -T sky130A
```

### 1. Yosys - RTL Synthesis Tool

<img width="1277" height="851" alt="Screenshot 2025-09-20 135240" src="https://github.com/user-attachments/assets/9a519861-361d-4d1c-bbeb-e78b2a05f20a" />

**Installation Process Completed:**
The screenshot shows the successful compilation of Yosys from source code with the following key stages:
- Building passes, commands, and technology libraries (52%-64% completion shown)
- Compilation of various synthesis passes including:
  - `passes/cmds/connect.o`
  - `passes/cmds/scatter.o` 
  - `passes/cmds/setundo.o`
  - `passes/cmds/splitnets.o`
  - `passes/cmds/stat.o`
  - And many more synthesis optimization passes

**Build Status**: Successfully reaching 64% completion with all compilation processes proceeding without errors.

<img width="1281" height="847" alt="Screenshot 2025-09-20 141459" src="https://github.com/user-attachments/assets/c0e623ef-f8b0-437e-9731-dac1cdba2f31" />

**Final Installation Steps:**
The completion screenshot shows:
- Technology library compilation (80%-100%)
- Building various backend synthesis libraries
- Successful build completion with "Build successful" message
- Installation commands executed: `sudo make install`
- Final installation copying binaries to `/usr/local/bin`

**Verification Commands:**
```bash
yosys --version
```

### 2. Icarus Verilog - Verilog Simulator

<img width="1277" height="857" alt="Screenshot 2025-09-20 141620" src="https://github.com/user-attachments/assets/ecdbdc13-8f64-44ba-8ab9-3afbc431867d" />

**Installation Process:**
The screenshot demonstrates the installation of Icarus Verilog using Ubuntu package manager:

```bash
sudo apt-get update
sudo apt-get install iverilog
```

**Installation Details:**
- Package fetching from Ubuntu repositories
- Dependency resolution and installation
- Successful installation of iverilog version 10.1-0.1build1
- Automatic configuration and setup completion

**Verification Result:**
```bash
iverilog -V
```

### 3. GTKWave - Waveform Viewer

<img width="1313" height="868" alt="Screenshot 2025-09-20 141726" src="https://github.com/user-attachments/assets/8f6b32bb-225c-4432-b45b-1b295e0e5b82" />

**Installation and Verification:**
The screenshot shows successful GTKWave installation and launch:

**Installation Command:**
```bash
sudo apt-get install gtkwave
```

**Successful Launch:**
- GTKWave application launched successfully
- Interface showing "GTKWave - [no file loaded]" 
- All menus and toolbars properly displayed
- Ready for waveform analysis and debugging

**Interface Components:**
- File menu for loading VCD/FST waveform files
- Signal hierarchy browser panel
- Waveform display area
- Time scale and measurement tools
- Search and filtering capabilities

**Usage Verification:**
```bash
gtkwave --version
gtkwave &
```

### 4. Additional Tools (Pre-installed in VDI)

Since you're using the OpenLane VDI, the following tools are already installed and configured:

#### Magic VLSI Layout Tool
```bash
magic --version
magic -T sky130A
```

#### OpenLane Flow
```bash
cd $HOME/OpenLane
make --version
docker --version
python3 --version
```

#### ngspice Circuit Simulator
```bash
ngspice --version
```

#### Other Essential Tools
```bash
git --version
python3 -m pip --version
make --version
```

## Application Domains

The RISC-V Reference SoC demonstrates versatility across multiple application domains with the same core architecture (O1=O2=O3=O4):

### Consumer Electronics Applications
1. **iWatch**: Wearable computing with power optimization
2. **Arduino Boards**: Embedded development platforms for prototyping  
3. **TV Panels**: Smart television controllers and media processing
4. **AC Applications**: Home appliance control and automation systems

### Key Design Benefits
- **Unified Architecture**: Single design supports multiple applications
- **Scalable Performance**: 100-130MHz operation range
- **Power Efficiency**: Optimized for battery-powered applications
- **Cost Effectiveness**: Reduced development time and verification effort

## Week 0 Accomplishments

### Tool Installation Verified
- **Yosys**: Successfully compiled from source and installed
- **Icarus Verilog**: Installed via apt package manager
- **GTKWave**: Installed and GUI verified working
- **Magic**: Pre-installed in VDI environment  
- **OpenLane**: Complete flow ready and operational
- **Docker**: Container support configured

### Knowledge Acquisition
- **SoC Design Flow**: Complete understanding of O1→O2→O3→O4 stages
- **RTL to GDSII**: Physical design flow comprehension
- **Tool Ecosystem**: EDA tool interoperability and usage
- **Application Domains**: Real-world SoC deployment scenarios

### Technical Skills Developed
- **Linux Command Line**: Package installation and system management
- **Tool Compilation**: Building EDA tools from source code
- **Version Control**: Git repository management
- **Virtualization**: VirtualBox environment configuration

## Tool Verification Summary

| Tool | Status | Version | Installation Method | Verification |
|------|--------|---------|-------------------|--------------|
| Yosys | Installed | Latest | Source compilation | `yosys --version` |
| Icarus Verilog | Installed | 10.1-0.1build1 | apt package | `iverilog -V` |
| GTKWave | Installed | Latest | apt package | GUI launch verified |
| Magic | Pre-installed | Latest | VDI included | Ready to use |
| OpenLane | Pre-installed | Latest | VDI included | Flow operational |
| Docker | Pre-installed | Latest | VDI included | Container ready |

## Conclusion

Week 0 has been successfully completed with all essential EDA tools installed and verified in the OpenLane VDI environment. The comprehensive tool ecosystem including Yosys, Icarus Verilog, GTKWave, Magic, and the complete OpenLane flow provides a robust foundation for the 20-week RISC-V Reference SoC Tapeout Program.

The demonstrated installation process showcases:
- **Professional EDA Environment**: Industry-standard tool configuration
- **Complete Verification**: All tools tested and operational
- **Ready for Development**: Environment prepared for complex RTL design
- **Real Tapeout Capability**: Complete flow from RTL to GDSII available

**Week 0 Status: COMPLETE** - Ready to proceed to Week 1 RTL Architecture Design

---

*This documentation provides comprehensive verification of the EDA tool environment setup for the RISC-V Reference SoC Tapeout Program. All screenshots demonstrate successful installation and operational verification.*
