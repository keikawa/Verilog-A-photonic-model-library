# Verilog-A-photonic_model_library

## Overview

This repository contains photonic device model libraries and sample testbenches for electronics and photonics co-design. This model library is designed to capture key device behaviors including optical loss, back reflection, nonlinearity, high-frequency response, and noise characteristics. The models are based on the interoperable Verilog-A language and can be imported into standard electronic circuit simulators. The sample testbenches are currently provided as a Keysight Advanced Design System (ADS) workspace, with potential support for other simulators in future releases.

![Screenshot 2024-05-02 194656](https://github.com/user-attachments/assets/c8fd176f-89b7-4f70-880e-da73becff145)
![Screenshot 2024-04-10 121612](https://github.com/user-attachments/assets/f2a64d39-c975-4a06-94f1-7b426718e6af)
![Screenshot 2024-04-09 1819592](https://github.com/user-attachments/assets/2e759798-76fa-4bcd-8742-ffe7b61a3af5)


This work builds on our recent study (K.Kawahara and T.Baba, [arXiv:2410.02282](https://arxiv.org/abs/2410.02282)), which has been accepted for publication in IEEE Journal of Microwaves.

---

## System Requirements

### Supported Platforms

The model library can be used with most electronic circuit simulators that support Verilog-A import.
The execution requirements for the sample testbench comply with those of Keysight ADS 2025.

- https://docs.keysight.com/display/engdocads/ADS+2025+System+Requirements

### Software Dependencies

No dependencies. The models can be used in any simulator that supports Verilog-A.

### Tested Environments

The sample testbench has been verified on the following environments:

#### Environment 1
- **OS**: Microsoft Windows 11 Home
- **Simulator**: Keysight ADS 2025 Update 0_1.
- **Processor**: 10th Gen Intel Core i7-10510U  
- **Memory**: 32 GB RAM  

#### Environment 2
- **OS**: CentOS Stream 8
- **Simulator**: Keysight ADS 2022 Update 2.
- **Processor**: 12th Gen Intel Core i7-12700
- **Memory**: 64 GB RAM  

**Note:**  
Some testbenches **did not run properly on ADS 2019 Update1**, and **2022 Update2 or later** is recommended.

---

## Installation Guide

The import procedure for Verilog-A models follows the standard method of each simulator.  
This section explains how to set up the sample testbench in Keysight ADS.

Start by unarchiving the ADS workspace. Open ADS and navigate to **File → Unarchive...**.  
Select the provided archive file **`opt_model_demo_wrk.7zads`** and specify the directory where the workspace should be created.

<img src="https://github.com/user-attachments/assets/c3613995-467e-42b5-a4c6-305994b2cbdd" width="60%">

When prompted in the **Select Items to Unarchive** window, ensure all items are checked.

<img src="https://github.com/user-attachments/assets/2f1f54a4-232e-405a-89a4-e94d772b155b" width="60%">

Next, in the **Unarchiving Workspace Options** window, select **`opt_model_demo_wrk`**.

<img src="https://github.com/user-attachments/assets/84df9aec-72de-41dd-8953-95e1ab5f3a3b" width="60%">

Click **Finish** to complete the unarchiving process.

Copy the **`veriloga`** directory from the provided distribution into the unarchived workspace directory (`opt_model_demo_wrk`).
The Verilog-A models are not included in the ADS archive, so they must be copied manually into the workspace directory for the simulations to work correctly.

<img src="https://github.com/user-attachments/assets/8f9bd1cc-3471-4f77-bcc9-ee345fc15a40" width="60%">

---

## Workspace Structure

The workspace contains the following files and directories:

📂 **opt_model_demo_wrk/**
├── aist_mzm_pcw_aist6_no21  
├── aist_mzm_rib  
├── aist_one_by_two_combiner  
├── aist_one_by_two_splitter  
├── aist_rfpad  
├── aist_transition_pcw_to_thin  
├── aist_transition_thin_to_pcw  
├── cpw_w8_d6  
├── cpw_w10_d9_100um  
├── cpw_w10_d9_200um  
├── pcw_phase_modulator_80um  
├── pcw_phase_modulator_segment  
├── rib_phase_modulator_2000um  
├── rib_phase_modulator_segment  
├── symbols  
├── tb_att  
├── tb_edfa  
├── tb_fabry-perot  
├── tb_filter  
├── tb_isolator  
├── tb_laser  
├── tb_mirror  
├── tb_mzi  
├── tb_mzm_pcw  
├── tb_mzm_rib  
├── tb_phase_modulator  
├── tb_photodetector  
├── tb_ssh  
└── tb_waveguide  

The `tb_` prefixed items represent testbenches, while the other components are sub-circuit models.

`opt_model_demo_wrk` includes a Verilog-A model library named `opt_model_lib`.  
`opt_model_lib` is loaded as a **Read-Only Library** in ADS and contains the following Verilog-A models:

- **Attenuator**
- **Cartesian2Polar**
- **CartesianMultiplier**
- **CwLaser**
- **DirectionalCoupler**
- **Isolator**
- **NoisyEDFA**
- **NonlinearCapacitor**
- **OneTwoLoopback**
- **OneTwoSplitter**
- **Pcw**
- **PcwPhaseModulator**
- **PhaseModulator**
- **PhaseShifter**
- **PhotoDetector**
- **Polar2Cartesian**
- **ReflectionInterface**
- **Terminator**
- **TunableFilter**
- **TwoOneCombiner**
- **Waveguide**

## Demo Guide

This demo runs a modulation simulation of a silicon photonic crystal waveguide (PCW) optical modulator.

1. **Open the schematic view of the testbench  (`tb_mzm_pcw`)**  

<img src="https://github.com/user-attachments/assets/f39d3c9e-26d5-4831-b9fa-26db68254f87" width="60%">

2. **Run the transient simulation**  (Click **Simulate (F7)**)

3. **View the results in Data Display (`.dds` file)**  

The expected result is as follows:

<img src="https://github.com/user-attachments/assets/5fa95abc-05a7-475c-a227-065839e4e1e3" width="60%">

The expected run time of the simulation is approximately several minutes on a normal desktop computer. 

---

## Instructions for Use

1. Create a new schematic by selecting **File -> New -> Schematic**.  
2. Open **Component Library**, and place the required models onto the schematic.  

<img src="https://github.com/user-attachments/assets/4f9434c1-5d4e-4606-a61d-2beb6e6713ed" width="60%">

3. Adjust the parameters of each component by double-clicking them and modifying values as needed.  

<img src="https://github.com/user-attachments/assets/64c2c70c-5976-4ec2-a009-9caa4d89c162" width="60%">

4. Add necessary simulation controllers.  
5. Once the schematic is complete, click **Simulate** to run the analysis and observe the results.  

## License

GNU General Public License v3.0 (GPL-3.0).

---

## Contact Information

- **Author**: Keisuke Kawahara, Corresponding Author
- **Affiliation**: Yokohama National University (now with Institute of Science Tokyo)
- **Email**: keisuke [at] ieee.org

This work was conducted at the [Baba Laboratory](https://baba-lab.ynu.ac.jp/babalabe.htm), Yokohama National University.

## Acknowledgment

This work was supported by JSPS KAKENHI Grant Number JP23KJ0988.
