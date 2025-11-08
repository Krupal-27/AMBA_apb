# **AMBA APB Protocol Implementation**

This project implements a complete AMBA APB (Advanced Peripheral Bus) protocol system in Verilog, featuring master and slave components with proper bus protocol handling and memory-mapped I/O.

## 🏗️ Architecture
- **3-Component System**: Master controller with multiple slave devices
- **APB Protocol Compliance**: Implements ARM AMBA APB specification
- **Memory-Mapped I/O**: 512-byte address space across two slaves
- **State Machine Control**: IDLE → SETUP → ENABLE state transitions

## 📋 Protocol Features
- **APB Signal Support**: PSEL, PENABLE, PWRITE, PADDR, PWDATA, PRDATA
- **Dual Slave Configuration**: Two independent slave devices
- **Error Handling**: PSLVERR for invalid address access
- **Flow Control**: PREADY for transfer completion
- **Read/Write Operations**: Full read and write capability

## 🎯 Key Components

### APB Master Controller
- **3-State FSM**: IDLE, SETUP, ENABLE states
- **Slave Selection**: Address-based slave decoding
- **Transfer Control**: Manages read/write operations
- **Data Handling**: Captures read data and drives write data

### APB Slave Devices
- **Memory Storage**: 256-byte internal memory per slave
- **Address Validation**: Error generation for invalid addresses
- **Protocol Compliance**: Proper PSEL and PENABLE response
- **Synchronous Operation**: Clock-based data transfer

### APB Top Module
- **System Integration**: Connects master and slaves
- **Signal Routing**: Proper bus signal distribution
- **Slave Arbitration**: Ready signal multiplexing
- **Error Propagation**: System-level error handling

## 🔧 Signal Description

### Master Inputs
- **pclk**: APB clock
- **presetn**: Active-low reset
- **transfer**: Initiate APB transfer
- **read/write**: Operation type
- **apb_write_paddr**: Write address (9-bit)
- **apb_write_data**: Write data (8-bit)
- **apb_read_paddr**: Read address (9-bit)

### Slave Interfaces
- **psel1/psel2**: Slave select signals
- **penable**: Transfer enable
- **pwrite**: Read/write direction
- **paddr**: Transfer address
- **pwdata**: Write data bus
- **prdata**: Read data bus
- **pready**: Transfer ready
- **pslverr**: Slave error

## 📊 Address Mapping
- **Slave 1**: Addresses 0x000-0x0FF (paddr[8] = 0)
- **Slave 2**: Addresses 0x100-0x1FF (paddr[8] = 1)
- **Memory Size**: 256 bytes per slave
- **Error Detection**: Addresses above 0xFF generate PSLVERR


