# Scenario 4: Workshop with HD Portfolio (5 Workstations)

**Date:** January 8, 2025
**Duration:** 09:27:30 - 10:08:01

## Summary
📊 **10 cars** | 🎯 **HD (100%)** | 🏭 **5 workstations** | 👷 **Manual processing** | ⏱️ **41.02 minutes** | ✅ **85% completion**

## Table of Contents
- [1. Scenario Overview](#1-scenario-overview)
  - [1.1 Key Characteristics](#11-key-characteristics)
  - [1.2 Material Flow](#12-material-flow)
  - [1.3 Files & Resources](#13-files--resources)
- [2. System Configuration](#2-system-configuration)
  - [2.1 Workstation Layout](#21-workstation-layout)
  - [2.2 Workstation Distances](#22-workstation-distances)
  - [2.3 Component Reference](#23-component-reference)
- [3. Disassembly Process](#3-disassembly-process)
  - [3.1 Quality-Based Routing](#31-quality-based-routing)
  - [3.2 Process Step Mapping](#32-process-step-mapping)
- [4. Production Schedule](#4-production-schedule)
- [5. Scenario Analysis](#5-scenario-analysis)
  - [5.1 System-Level Indicators](#51-system-level-indicators)
  - [5.2 Workstation Performance](#52-workstation-performance)
  - [5.3 Production Order Analysis](#53-production-order-analysis)
- [6. Data Quality Notes](#6-data-quality-notes)



<!-- ================================================== -->
<!-- SCENARIO OVERVIEW -->
<!-- ================================================== -->
## 1. Scenario Overview

This scenario presents a 5-workstation workshop configuration processing 10 cars with complete HD disassembly.

### 1.1 Key Characteristics

Table 1.1 summarizes the key characteristics of this scenario. The configuration uses a workshop layout with manual processing, allowing flexible routing between workstations for maximum component recovery.

**Table 1.1.** Key characteristics of Scenario 4

| Characteristic | Value |
|---------------|--------|
| **System design** | Workshop with 5 workstations (WS-01 to WS-05) |
| **Product portfolio** | 10 cars with HD quality type only |
| **Product mix** | HD (100%) |
| **Disassembly depths** | Fixed |
| **Total units** | 10 cars (PO-01 to PO-10) |
| **Processing type** | Manual (operator disassembles by hand) |
| **Flow pattern** | Mixed flow (multi-station for most, single-station for some) |

<br>



### 1.2 Material Flow
Figure 1.1 shows the material flow diagram, which illustrates how EOL products are routed through the disassembly system.

![Material Flow Diagram](figures/scenario_04_material_flow.svg)

**Figure 1.1:** Material flow for HD product portfolio with 5 workstations in workshop configuration

<br>


### 1.3 Files & Resources

Table 1.2 lists all the data, documentation, and production order (PO) files for this disassembly scenario. For a more detailed description of the Excel spreadsheet, please refer to the [README.md](../../README.md) file.

**Table 1.2.** Complete file listing for Scenario 4

| **Category** | **File** | **Description** |
|--------------|----------|-----------------|
| **Data files** | [`scenario_04_data_raw.csv`](data/scenario_04_data_raw.csv) | Raw material flow data (788 recorded events) |
| | [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx) | Cleaned data with analysis sheets |
| **Material flow** | [`scenario_04_material_flow.svg`](figures/scenario_04_material_flow.svg) | System layout and material flow diagram |
| **Disassembly sequences** | [`scenario_04_sequence_HD.svg`](figures/scenario_04_sequence_HD.svg) | HD disassembly sequence (variable depths) |
| **Work instructions** | [`scenario_04_WI_HD.pdf`](figures/scenario_04_WI_HD.pdf) | Work instructions for HD quality type |

<br>


<!-- ================================================== -->
<!-- SYSTEM CONFIGURATION -->
<!-- ================================================== -->
## 2. System Configuration

### 2.1 Workstation Layout

Table 2.1 shows the physical configuration of the workstations within the system. B-Transfer serves as the final output buffer for finished components.

**Table 2.1.** Workstation layout and buffer configuration (Source: [`scenario_04_material_flow.svg`](figures/scenario_04_material_flow.svg))

| Workstation | Position | Buffer before | Buffer after | Equipment type |
|---------|----------|---------------|--------------|----------------|
| WS-01 | Workshop workstation 1 | B-Goods-In | B-FIFO | Manual |
| WS-02 | Workshop workstation 2 | B-Goods-In | B-FIFO | Manual |
| WS-03 | Workshop workstation 3 | B-FIFO | B-Transfer | Manual |
| WS-04 | Workshop workstation 4 | B-FIFO | B-Transfer | Manual |
| WS-05 | Workshop workstation 5 | B-FIFO | B-Transfer | Manual |

<br>

### 2.2 Workstation Distances

Table 2.2 shows the physical distances between workstations and key locations in the system. These distances are measured in meters and represent the shortest path between locations.

**Table 2.2.** Workstation distance matrix in meters (measured approximately)

|            | Goods-in | WS-01 | WS-02 | WS-03 | WS-04 | WS-05 | B-FIFO | Warehouse |
|------------|----------|-------|-------|-------|-------|-------|--------|-----------|
| Goods-in   | 0        | 3.2   | 5.4   | 3.2   | 5.4   | 7.8   | 5.2    | 5.2       |
| WS-01      | 3.2      | 0     | 2.5   | 4.0   | 4.7   | 6.4   | 2.0    | 2.0       |
| WS-02      | 5.4      | 2.5   | 0     | 4.7   | 4.0   | 4.7   | 2.0    | 2.0       |
| WS-03      | 3.2      | 4.0   | 4.7   | 0     | 2.5   | 5.0   | 2.0    | 2.0       |
| WS-04      | 5.4      | 4.7   | 4.0   | 2.5   | 0     | 2.5   | 2.0    | 2.0       |
| WS-05      | 7.8      | 6.4   | 4.7   | 5.0   | 2.5   | 0     | 2.0    | 2.0       |
| B-FIFO     | 5.2      | 2.0   | 2.0   | 2.0   | 2.0   | 2.0   | 0      | 0         |
| Warehouse  | 5.2      | 2.0   | 2.0   | 2.0   | 2.0   | 2.0   | 0      | 0         |

<br>

### 2.3 Component Reference

Table 2.3 lists all the components that can be disassembled from the cars. Each component is assigned a recovery destination based on its condition and potential for reuse.

**Table 2.3.** Component codes and their recovery destinations (Source: Disassembly sequence diagrams, [figures/](figures/))

| Code | Component | Quantity | Destination |
|------|-----------|----------|-------------|
| BOSP | Body & spoiler | 1+1 | Recycle |
| BAT | Battery | 1 | Reuse |
| RT | Rear tires | 2 | Recycle/Reuse |
| FT | Front tires | 2 | Reuse |
| FAXS | Front axis with shock absorbers | 1 | None (intermediate assembly) |
| SSA | Small shock absorbers | 2 | Recycle |
| FAX | Front axis | 1 | Remanufacture |
| CHS | Chassis | 1 | Reuse |
| BSA | Big shock absorbers | 2 | Remanufacture |
| RAX (HD) | Rear axis | 1 | Recycle |

<br>


<!-- ================================================== -->
<!-- DISASSEMBLY PROCESS -->
<!-- ================================================== -->
## 3. Disassembly Process

### 3.1 Quality-Based Routing

Table 3.1 illustrates the routing patterns for each quality type through the disassembly system. Each vehicle follows a specific route based on operational decisions despite all being HD quality.

**Table 3.1.** Quality-dependent routing and target components (Source: [`scenario_04_material_flow.svg`](figures/scenario_04_material_flow.svg))

| Quality type | Count | Material flow | Target components | Remaining |
|--------------|-------|-------|-------------------|-----------|
| **HD** (Hail damage) | 10 | Variable (see production schedule) | BOSP, BAT, RT, FT, SSA*, FAX*, CHS*, BSA* | RAX (HD) |

<br>



### 3.2 Process Step Mapping

Table 3.2 maps which disassembly steps are performed for each quality type. Components marked with * vary by PO based on disassembly depth.

**Table 3.2.** Process steps by quality type (Source: [`scenario_04_material_flow.svg`](figures/scenario_04_material_flow.svg)) and workstation assignment

| Step | Operation | HD | Workstation(s) |
|------|-----------|------------|------------|
| S1 | Remove body & spoiler | ✓ | WS-01/WS-02 (Stage 1) |
| S2 | Remove battery | ✓ | WS-01/WS-02 (Stage 1) |
| S3 | Remove rear tires | ✓ | WS-01/WS-02 (Stage 1) |
| S4 | Remove front tires | ✓ | WS-01/WS-02 (Stage 1) |
| S5 | Remove small shock absorbers | ✓* | WS-03/WS-04/WS-05 (Stage 2) |
| S6 | Remove front axis | ✓* | WS-03/WS-04/WS-05 (Stage 2) |
| S7 | Remove chassis | ✓* | WS-03/WS-04/WS-05 (Stage 2) |
| S8 | Remove big shock absorbers | ✓* | WS-03/WS-04/WS-05 (Stage 2) |

<br>


<!-- ================================================== -->
<!-- PRODUCTION SCHEDULE -->
<!-- ================================================== -->
## 4. Production Schedule

Table 4.1 shows the arrival schedule and processing status of all production orders. Variable disassembly depths despite same quality type.

**Table 4.1.** Production order schedule and completion status (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheets "delivery_times" and "extraction")

| Order | Arrival time | Quality type | Material flow | Status |
|-------|--------------|--------------|------------------|--------|
| PO-01 | 09:27:30 | HD | WS-01,02,03,04,05 | Complete |
| PO-02 | 09:29:00 | HD | WS-02,03,04 | Complete |
| PO-03 | 09:30:30 | HD | WS-01,02,03,04,05 | Complete |
| PO-04 | 09:32:00 | HD | WS-02,05 | Complete |
| PO-05 | 09:33:30 | HD | WS-01,02,04,05 | Complete |
| PO-06 | 09:35:00 | HD | WS-01,02,03,05 | Complete |
| PO-07 | 09:37:30 | HD | WS-01,02,05 | Incomplete |
| PO-08 | 09:41:00 | HD | WS-02,04,05 | Incomplete |
| PO-09 | 09:43:00 | HD | WS-01 | Incomplete |
| PO-10 | 09:47:30 | HD | WS-02 | Incomplete |

<br>



<!-- ================================================== -->
<!-- SCENARIO ANALYSIS -->
<!-- ================================================== -->
## 5. Scenario Analysis

> 📊 **Note on Data Presentation:** The tables and metrics in this section provide a concise summary. For detailed analysis, refer to the Excel analysis file ([`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx)). This file contains the complete dataset and calculations.


### 5.1 System-Level Indicators

Table 5.1 presents the overall system throughput performance. Six of ten production orders had a completion rate of 100%.

**Table 5.1.** System-level performance indicators (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>Value</th></tr>
<tr><td>Total processing time (minutes)</td><td>41.02</td></tr>
<tr><td>POs processed (#)</td><td>10</td></tr>
<tr><td>System throughput rate (POs/hour)</td><td>12.4</td></tr>
<tr><td>Total components planned (#)<sup>[1]</sup></td><td>72</td></tr>
<tr><td>Total components completed (#)<sup>[1]</sup></td><td>63</td></tr>
<tr><td>Overall completion rate (%)</td><td>85</td></tr>
</table>

Notes:

<sup>[1]</sup> Component counts based on target components defined in Table 3 of the [README.md](../../README.md). Components are counted by their codes (e.g., BOSP, RT, BSA) as defined in Table 2.3, where each code represents one component unit regardless of quantity.

<br><br>

Table 5.2 summarizes the total number of components of each type that were disassembled. The summary reflects the HD disassembly scenario with variable depths.

**Table 5.2.** Component processing summary (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheet "analysis")

| Code | Component | Quantity | Instances | Total components disassembled |
|------|-----------|----------|-----------|-------------------------------|
| BOSP | Body & spoiler | 1+1 | 10 | 20 |
| BAT | Battery | 1 | 10 | 10 |
| RT | Rear tires | 2 | 9 | 18 |
| FT | Front tires | 2 | 8 | 16 |
| FAX | Front axis | 1 | 7 | 7 |
| SSA | Small shock absorbers | 2 | 7 | 14 |
| CHS | Chassis | 1 | 6 | 6 |
| BSA | Big shock absorbers | 2 | 6 | 12 |
| **Total** | **-** | **-** | **63** | **103** |

Note: Only target components shown. Intermediate assemblies (FAXS, CRAXS, CREW) and remaining components (RAX, CRE, CSEB-NABS) are excluded from this count.

<br>

### 5.2 Workstation Performance

Table 5.3 shows the utilization and workload distribution across workstations. The average utilization across all workstations is 70.8%.

**Table 5.3.** Workstation performance indicators (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheet "analysis")

| Indicator | WS-01 | WS-02 | WS-03 | WS-04 | WS-05 |
|--------|-------|-------|-------|-------|-------|
| POs processed | 5/10 | 5/10 | 2/10 | 2/10 | 3/10 |
| Components disassembled | 19 | 18 | 8 | 8 | 10 |
| Total busy time (seconds) | 2,293 | 2,190 | 1,246 | 1,620 | 1,364 |
| Total busy time (minutes) | 38.2 | 36.5 | 20.8 | 27.0 | 22.7 |
| Utilization rate (%) | 93.2 | 89.0 | 50.6 | 65.8 | 55.4 |
| Quality types handled | HD | HD | HD | HD | HD |

<br>


### 5.3 Production Order Analysis

Table 5.4 shows the handling time, in seconds, for each component across all production orders. The handling time includes both the disassembly time and the waiting time at a workstation.

**Table 5.4.** Component handling times per production order (seconds)
*Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx) - Process_calculation sheet*

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 120 | 50 | 120 | 105 | 89 | 255 | 105 | 91 | 90 | 135 | 90 | 120 |
| S2 | BAT | 89 | 33 | 106 | 120 | 135 | 105 | 90 | 89 | 45 | 105 | 45 | 45 |
| S3 | RT | 117 | 42 | 119 | 106 | 90 | 74 | 120 | 90 | 149 | 91 | 210 | - |
| S4 | FT | 157 | 58 | 165 | 180 | 187 | 195 | 105 | 121 | 240 | 59 | - | - |
| S5 | FAXS | 230 | 71 | 248 | 327 | 324 | 169 | 193 | 191 | 158 | - | - | - |
| S6 | SSA | 143 | 47 | 156 | 198 | 201 | 101 | 152 | 109 | 81 | - | - | - |
| S7 | CHS/CORE | 197 | 39 | 210 | 254 | 180 | 195 | 209 | 135 | - | - | - | - |
| S8 | BSA | 158 | 43 | 209 | 181 | 135 | 106 | 195 | 120 | - | - | - | - |

<br><br>

Table 5.5 shows the actual disassembly time, in seconds, for each component across all production orders. Disassembly time represents only active processing duration (excludes waiting time).

**Table 5.5.** Component disassembly times per production order (seconds) (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 89 | 51 | 90 | 75 | 60 | 225 | 90 | 60 | 45 | 75 | 60 | 105 |
| S2 | BAT | 45 | 23 | 30 | 60 | 90 | 60 | 45 | 60 | 15 | 45 | 30 | 15 |
| S3 | RT | 88 | 53 | 89 | 75 | 75 | 45 | 90 | 60 | 119 | 30 | 210 | - |
| S4 | FT | 103 | 59 | 119 | 135 | 133 | 120 | 15 | 76 | 195 | 30 | - | - |
| S5 | FAXS | 179 | 54 | 219 | 283 | 174 | 139 | 149 | 161 | 129 | - | - | - |
| S6 | SSA | 115 | 35 | 112 | 167 | 141 | 86 | 137 | 94 | 66 | - | - | - |
| S7 | CHS/CORE | 160 | 32 | 164 | 210 | 150 | 135 | 180 | 120 | - | - | - | - |
| S8 | BSA | 110 | 44 | 119 | 151 | 105 | 60 | 165 | 60 | - | - | - | - |

<br><br>

Table 5.6 summarizes the performance indicators for each production order. Variable disassembly depths lead to different completion rates.

**Table 5.6.** Production order performance indicators (Source: [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>PO-01</th><th>PO-02</th><th>PO-03</th><th>PO-04</th><th>PO-05</th><th>PO-06</th><th>PO-07</th><th>PO-08</th><th>PO-09</th><th>PO-10</th></tr>
<tr><td>Handling time (seconds)<sup>[1]</sup></td><td>1,333</td><td>1,471</td><td>1,341</td><td>1,200</td><td>1,169</td><td>946</td><td>763</td><td>390</td><td>345</td><td>165</td></tr>
<tr><td>Disassembly time (seconds)<sup>[2]</sup></td><td>942</td><td>1,156</td><td>928</td><td>870</td><td>871</td><td>691</td><td>569</td><td>180</td><td>300</td><td>120</td></tr>
<tr><td>Waiting time (seconds)<sup>[3]</sup></td><td>1</td><td>16</td><td>391</td><td>482</td><td>797</td><td>871</td><td>947</td><td>1,051</td><td>1,156</td><td>991</td></tr>
<tr><td>Lead time (seconds)<sup>[4]</sup></td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr>
<tr><td>Components planned (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>4</td><td>4</td></tr>
<tr><td>Components completed (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>6</td><td>4</td><td>3</td><td>2</td></tr>
<tr><td>Completion rate (%)</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>75</td><td>50</td><td>75</td><td>50</td></tr>
</table>

Notes:

<sup>[1]</sup> Handling time: Total duration from component entry to exit at workstation (includes disassembly + movement time).

<sup>[2]</sup> Disassembly time: Active processing duration (excludes waiting time).

<sup>[3]</sup> Waiting time: Duration spent in buffer before processing.

<sup>[4]</sup> Lead time: Total duration from production order arrival to completion.

<br>



<!-- ================================================== -->
<!-- DATA QUALITY NOTES -->
<!-- ================================================== -->

## 6. Data Quality Notes

Table 6.1 summarizes the data processing pipeline and event counts. A signal-to-noise ratio of 35% was achieved after filtering. For additional details, see the [`scenario_04_data_analyzed.xlsx`](data/scenario_04_data_analyzed.xlsx) file, specifically the "pre-process", "extraction", and "process_calculation" sheets.

**Table 6.1.** Data quality statistics showing processing stages

| Stage | Event count | Description |
|-------|-------------|-------------|
| **Raw events** | 780 | Original recorded events from IT system |
| **Preprocessed** | 797 | +17 events added during preprocessing |
| **Clean events** | 275 | Final usable events after cleaning |
| - OK (from raw) | 257 | Events validated from raw data |
| - Cleaned | 44 | Manually corrected events |
| - Calculated | 4 | Estimated from averages |
| - Start | 10 | Manually added start events |
| - Unfinished | 40 | Events marked as unfinished PO (excluded) |
| - Missing | 3 | Missing events (excluded) |
| **Filtered noise** | 522 | Events removed as noise (65%) |
| **Signal-to-noise ratio** | 35% | Percentage of usable data |
