
# RISC-V Reference SoC Tapeout Program - Week 0: 
Getting Started with Digital VLSI SoC Design and Planning

## Table of Contents
1. [Program Overview](#program-overview)
2. [SoC Design Flow](#soc-design-flow)
3. [OpenLane VDI Environment Setup](#openlane-vdi-environment-setup)
4. [Tool Installation & Verification](#tool-installation--verification)
5. [Application Domains](#application-domains)
6. [Week 0 Accomplishments](#week-0-accomplishments)

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

![Chip Modeling Stages](images/chip_modeling.png)

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

![RTL to GDSII Flow](images/rtl_to_gdsii.png)

The complete RTL2GDS flow encompasses front-end design, physical design, back-end verification, and tapeout processes.

## OpenLane VDI Environment Setup

### System Configuration
- **VDI Environment**: Pre-configured OpenLane Virtual Disk Image
- **Host System**: Oracle VirtualBox on Windows/Linux
- **Guest OS**: Ubuntu 20.04 LTS
- **User**: vsduser@vsdsquadron
- **All EDA Tools**: Pre-installed and configured

### Environment Advantages
Since you're using the pre-installed OpenLane VDI from previous VSD course enrollment:
- ✅ All tools are pre-compiled and configured
- ✅ No dependency conflicts or version mismatches  
- ✅ Optimized environment for VLSI design flow
- ✅ Ready-to-use PDK libraries and design kits

## Tool Installation & Verification

This section documents the successful installation and verification of essential EDA tools in the OpenLane VDI environment.

### 1. Yosys - RTL Synthesis Tool

![Yosys Installation Process](Screenshot-2025-09-20-140921.jpg)

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

![Yosys Installation Completion](Screenshot-2025-09-20-141426.jpg)

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
# Expected: Yosys version information and successful tool launch
```

### 2. Icarus Verilog - Verilog Simulator

![Icarus Verilog Installation](Screenshot-2025-09-20-141620.jpg)

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
# Shows successful installation and version information
```

### 3. GTKWave - Waveform Viewer

![GTKWave Installation and Launch](Screenshot-2025-09-20-141726.jpg)

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
gtkwave &  # Launch GUI application
```

### 4. Additional Tools (Pre-installed in VDI)

Since you're using the OpenLane VDI, the following tools are already installed and configured:

#### Magic VLSI Layout Tool
```bash
magic --version
magic -T sky130A  # Launch with Sky130 technology
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

![Application Examples](images/applications.png)

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

### ✅ Environment Setup Completed
- **OpenLane VDI**: Successfully imported and running in Oracle VirtualBox
- **Ubuntu 20.04**: Desktop environment fully operational
- **User Account**: vsduser@vsdsquadron configured and accessible
- **Network**: Internet connectivity verified for package installations

### ✅ Tool Installation Verified
- **Yosys**: ✅ Successfully compiled from source and installed
- **Icarus Verilog**: ✅ Installed via apt package manager
- **GTKWave**: ✅ Installed and GUI verified working
- **Magic**: ✅ Pre-installed in VDI environment  
- **OpenLane**: ✅ Complete flow ready and operational
- **Docker**: ✅ Container support configured

### ✅ Knowledge Acquisition
- **SoC Design Flow**: Complete understanding of O1→O2→O3→O4 stages
- **RTL to GDSII**: Physical design flow comprehension
- **Tool Ecosystem**: EDA tool interoperability and usage
- **Application Domains**: Real-world SoC deployment scenarios

### ✅ Technical Skills Developed
- **Linux Command Line**: Package installation and system management
- **Tool Compilation**: Building EDA tools from source code
- **Version Control**: Git repository management
- **Virtualization**: VirtualBox environment configuration

## Tool Verification Summary

| Tool | Status | Version | Installation Method | Verification |
|------|--------|---------|-------------------|--------------|
| Yosys | ✅ Installed | Latest | Source compilation | `yosys --version` |
| Icarus Verilog | ✅ Installed | 10.1-0.1build1 | apt package | `iverilog -V` |
| GTKWave | ✅ Installed | Latest | apt package | GUI launch verified |
| Magic | ✅ Pre-installed | Latest | VDI included | Ready to use |
| OpenLane | ✅ Pre-installed | Latest | VDI included | Flow operational |
| Docker | ✅ Pre-installed | Latest | VDI included | Container ready |

## Repository Structure

```
RISC-V-Reference-SoC-Tapeout-Program_Week-0/
├── README.md                    # This documentation
├── images/                      # Design flow diagrams
│   ├── chip_modeling.png        # O1=O2=O3=O4 flow diagram
│   ├── rtl_to_gdsii.png        # Complete RTL2GDS process
│   └── applications.png         # Application domain examples
├── screenshots/                 # Tool installation screenshots  
│   ├── yosys_build.jpg         # Yosys compilation process
│   ├── yosys_install.jpg       # Yosys installation completion
│   ├── iverilog_install.jpg    # Icarus Verilog installation
│   └── gtkwave_launch.jpg      # GTKWave GUI verification
├── docs/                        # Additional documentation
├── scripts/                     # Tool verification scripts
└── logs/                        # Installation and build logs
```

## Quick Reference Commands

### Daily Tool Usage
```bash
# Tool version checks
yosys --version
iverilog -V  
gtkwave --version

# Basic Verilog simulation flow
iverilog -o design design.v testbench.v
./design
gtkwave waveform.vcd

# Yosys synthesis check
yosys -p "read_verilog design.v; synth; show"

# OpenLane flow
cd $HOME/OpenLane && make mount
```

### Environment Management
```bash
# VDI system info
uname -a
lsb_release -a

# Resource usage
free -h
df -h
htop
```

## Next Steps - Week 1 Preparation

### Immediate Actions
1. **Explore OpenLane Flow**: Run sample designs through complete RTL2GDS
2. **Verilog Practice**: Create simple RTL designs and testbenches
3. **Tool Familiarization**: Practice with Yosys synthesis and GTKWave analysis
4. **Repository Setup**: Organize project structure for upcoming weeks

### Learning Objectives for Week 1
1. **RTL Design**: Implement RISC-V processor components
2. **Verification**: Develop comprehensive testbenches
3. **Synthesis**: Use Yosys for RTL synthesis and optimization
4. **Analysis**: Waveform debugging with GTKWave

## Conclusion

Week 0 has been successfully completed with all essential EDA tools installed and verified in the OpenLane VDI environment. The comprehensive tool ecosystem including Yosys, Icarus Verilog, GTKWave, Magic, and the complete OpenLane flow provides a robust foundation for the 20-week RISC-V Reference SoC Tapeout Program.

The demonstrated installation process showcases:
- **Professional EDA Environment**: Industry-standard tool configuration
- **Complete Verification**: All tools tested and operational
- **Ready for Development**: Environment prepared for complex RTL design
- **Real Tapeout Capability**: Complete flow from RTL to GDSII available

**🎯 Week 0 Status: COMPLETE** - Ready to proceed to Week 1 RTL Architecture Design

---

*This documentation provides comprehensive verification of the EDA tool environment setup for the RISC-V Reference SoC Tapeout Program. All screenshots demonstrate successful installation and operational verification.*
