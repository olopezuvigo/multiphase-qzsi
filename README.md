# Quasi-Impedance-Source Inverter Boards for Multiphase Motor Drive Applications

A set of KiCad projects for designing and documenting a multiphase **Quasi-Z-Source Inverter (QZSI)** for multiphase motor drive applications.

This work was supported by [MCIN/AEI/10.13039/501100011033/FEDER, UE](https://www.aei.gob.es/en) under Project [PID2021-124136OB-I00](http://olopez.webs.uvigo.es/pgc2021.html).

## Overview

This repository contains the complete KiCad design files for a multiphase QZSI, intended for a multiphase QZSI motor drive.
The multiphase QZSI is comprised of **two** types of boards:
- **Z-source board**: documented in the KiCad project [`Modular_qZSI_Z_board`](https://github.com/olopezuvigo/multiphase-qzsi/tree/main/Modular_qZSI_Z_board)
- **Half-bridge boards**: documented in the KiCad project [`Modular_qZSI_leg_board`](https://github.com/olopezuvigo/multiphase-qzsi/tree/main/Modular_qZSI_leg_board)

An $n$-phase QZSI can be built with $n$ **Half-Bridge Leg Boards** and at least one **Z-Source Board**.

### Z-Source Board

This board is the core impedance network of the qZSI. Its main job is to provide buck-boost voltage conversion. It contains two large banks of capacitors (`C1 Capacitor Bank` and `C2 Capacitor Bank`) and provides connection points for two external inductors (`L1` and `L2`). Together, these components create a variable DC bus that powers the inverter legs.

### Half-Bridge Leg Board

This board is a single half-bridge, representing one phase of the inverter. It's an interface board that connects to an external power stage module (`EVAL-ADUM4146WHB1Z`) where the actual MOSFETs and drivers are located.

### System Operation & Modularity

The system functions by using the Z-source network to allow controlled **shoot-through** states in the inverter legs. This unique feature boosts the DC bus voltage without causing damage. The inverter legs then use this boosted DC voltage to create the final AC output.

The key feature is **modularity**. By connecting multiple leg boards to the central Z-source board, the system can be configured as a single-phase, three-phase, or other multiphase inverters.

## Project Structure

| File/Folder         | Description                                      |
|---------------------|--------------------------------------------------|
| `*/*.kicad_pro`     | KiCad project file                               |
| `*/*.sch`           | Schematic file(s)                                |
| `*/*.kicad_pcb`     | PCB layout                                       |
| `*/*.lib` / `*.dcm` | Custom symbol libraries (if any)                 |
| `*/*.pretty`        | Custom footprint libraries (if any)              |
| `*/*.packages3D`    | 3D models                                        |
| `*/Documentation`   | Documentation (PDFs, images, datasheets, etc.)   |

## Getting Started

### Prerequisites

- [KiCad](https://www.kicad.org/download/) (version 8.03 or newer)

### Opening the Project

1. Clone this repository:
   ```sh
   git clone https://github.com/olopezuvigo/multiphase-qzsi.git
