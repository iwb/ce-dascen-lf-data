# Scenario 2: Workshop with HD Portfolio (4 Workstations)

**Date:** January 3, 2025
**Duration:** 09:25:00 - 10:05:16

## Summary
📊 **10 cars** | 🎯 **HD (100%)** | 🏭 **4 workstations** | 👷 **Manual processing** | ⏱️ **40.27 minutes** | ✅ **85% completion**

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

This scenario presents a 4-workstation workshop configuration processing 10 cars with a single quality type (HD).

### 1.1 Key Characteristics

Table 1.1 summarizes the key characteristics of this scenario. The configuration uses a workshop layout with manual processing for HD quality vehicles only.

**Table 1.1.** Key characteristics of Scenario 2

| Characteristic | Value |
|---------------|--------|
| **System design** | Workshop with 4 workstations (WS-01 to WS-04) |
| **Product portfolio** | 10 cars with HD quality type only |
| **Product mix** | HD (100%) |
| **Disassembly depths** | Fixed |
| **Total units** | 10 cars (PO-01 to PO-10) |
| **Processing type** | Manual (operator disassembles by hand) |
| **Flow pattern** | Single-station flow (each PO processed at one workstation) |

<br>

### 1.2 Material Flow

Figure 1.1 shows the material flow diagram, which illustrates how EOL products are routed through the disassembly system.

![Material Flow Diagram](figures/scenario_02_material_flow.svg)

**Figure 1.1:** Material flow for HD product portfolio with 4 active workstations (WS-01 to WS-04) in workshop configuration

<br>

### 1.3 Files & Resources

Table 1.2 lists all the data, documentation, and production order (PO) files for this disassembly scenario. For a more detailed description of the Excel spreadsheet, please refer to the [README.md](../../README.md) file.

**Table 1.2.** Complete file listing for Scenario 2

| **Category** | **File** | **Description** |
|--------------|----------|-----------------|
| **Data files** | [`scenario_02_data_raw.csv`](data/scenario_02_data_raw.csv) | Raw material flow data (723 recorded events) |
| | [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx) | Cleaned data with analysis sheets |
| **Material flow** | [`scenario_02_material_flow.svg`](figures/scenario_02_material_flow.svg) | System layout and material flow diagram |
| **Disassembly sequences** | [`scenario_02_sequence_HD.svg`](figures/scenario_02_sequence_HD.svg) | HD (Hail damage) disassembly sequence |
| **Work instructions** | [`scenario_02_WI_HD.pdf`](figures/scenario_02_WI_HD.pdf) | Work instructions for HD quality type |

<br>

<!-- ================================================== -->
<!-- SYSTEM CONFIGURATION -->
<!-- ================================================== -->
## 2. System Configuration

### 2.1 Workstation Layout

Table 2.1 shows the physical configuration of the workstations within the system. B-Transfer serves as the final output buffer for finished components.

**Table 2.1.** Workstation layout and buffer configuration (Source: [`scenario_02_material_flow.svg`](figures/scenario_02_material_flow.svg))

| Workstation | Position | Buffer before | Buffer after | Equipment type |
|---------|----------|---------------|--------------|----------------|
| WS-01 | Workshop workstation 1 | B-01 | B-Transfer | Manual |
| WS-02 | Workshop workstation 2 | B-02 | B-Transfer | Manual |
| WS-03 | Workshop workstation 3 | B-03 | B-Transfer | Manual |
| WS-04 | Workshop workstation 4 | B-04 | B-Transfer | Manual |

<br>

### 2.2 Workstation Distances

Table 2.2 shows the physical distances between workstations and key locations in the system. These distances are measured in meters and represent the shortest path between locations.

**Table 2.2.** Workstation distance matrix in meters (measured approximately)

|            | Goods-in | WS-01 | WS-02 | WS-03 | WS-04 | Warehouse |
|------------|----------|-------|-------|-------|-------|-----------|
| Goods-in   | 0        | 3.2   | 5.4   | 3.2   | 5.4   | 5.2       |
| WS-01      | 3.2      | 0     | 2.5   | 4.0   | 4.7   | 2.0       |
| WS-02      | 5.4      | 2.5   | 0     | 4.7   | 4.0   | 2.0       |
| WS-03      | 3.2      | 4.0   | 4.7   | 0     | 2.5   | 2.0       |
| WS-04      | 5.4      | 4.7   | 4.0   | 2.5   | 0     | 2.0       |
| Warehouse  | 5.2      | 2.0   | 2.0   | 2.0   | 2.0   | 0         |

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

Table 3.1 illustrates the routing patterns for each quality type through the disassembly system. All vehicles are HD quality but are distributed across different workstations based on operational decisions.

**Table 3.1.** Quality-dependent routing and target components (Source: [`scenario_02_material_flow.svg`](figures/scenario_02_material_flow.svg))

| Quality type | Count | Material flow | Target components | Remaining |
|--------------|-------|-------|-------------------|-----------|
| **HD** (Hail damage) | 10 | Single workstation (WS-01, WS-02, WS-03, or WS-04) | BOSP, BAT, RT*, FT*, FAXS, SSA*, FAX*, CHS*, BSA* | RAX (HD) |

<br>

### 3.2 Process Step Mapping

Table 3.2 maps which disassembly steps are performed for each quality type. Components marked with * were not removed for PO-09 and PO-10 (incomplete PO).

**Table 3.2.** Process steps by quality type and workstation assignment (Source: [`scenario_02_material_flow.svg`](figures/scenario_02_material_flow.svg))

| Step | Operation | HD | Workstation(s) |
|------|-----------|------------|------------|
| S1 | Remove body & spoiler | ✓ | All workstations |
| S2 | Remove battery | ✓ | All workstations |
| S3 | Remove rear tires | ✓* | All workstations |
| S4 | Remove front tires | ✓* | All workstations |
| S5 | Remove front axis with shock absorbers | ✓* | All workstations |
| S6 | Remove small shock absorbers | ✓* | All workstations |
| S7 | Remove chassis | ✓* | All workstations |
| S8 | Remove big shock absorbers | ✓* | All workstations |

<br>

<!-- ================================================== -->
<!-- PRODUCTION SCHEDULE -->
<!-- ================================================== -->
## 4. Production Schedule

Table 4.1 shows the arrival schedule and processing status of all production orders. PO-09 and PO-10 had incomplete disassembly (only BOSP and BAT removed).

**Table 4.1.** Production order schedule and completion status (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheets "delivery_times" and "extraction")

| Order | Arrival time | Quality type | Material flow | Status |
|-------|--------------|--------------|------------------|--------|
| PO-01 | 09:25:00 | HD | WS-04 | Complete |
| PO-02 | 09:26:00 | HD | WS-01 | Complete |
| PO-03 | 09:27:00 | HD | WS-02 | Complete |
| PO-04 | 09:28:00 | HD | WS-03 | Complete |
| PO-05 | 09:29:00 | HD | WS-01 | Complete |
| PO-06 | 09:30:00 | HD | WS-03 | Complete |
| PO-07 | 09:31:30 | HD | WS-04 | Complete |
| PO-08 | 09:32:15 | HD | WS-02 | Complete |
| PO-09 | 09:33:00 | HD | WS-03 | Incomplete |
| PO-10 | 09:34:00 | HD | WS-02 | Incomplete |

<br>

<!-- ================================================== -->
<!-- SCENARIO ANALYSIS -->
<!-- ================================================== -->

## 5. Scenario Analysis

> 📊 **Note on Data Presentation:** The tables and metrics in this section provide a concise summary. For detailed analysis, refer to the Excel analysis file ([`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx)). This file contains the complete dataset and calculations.


### 5.1 System-Level Indicators

Table 5.1 presents the overall system throughput performance. Eight of ten production orders had a completion rate of 100%.

**Table 5.1.** System-level performance indicators (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>Value</th></tr>
<tr><td>Total processing time (minutes)</td><td>40.27</td></tr>
<tr><td>POs processed (#)</td><td>10</td></tr>
<tr><td>System throughput rate (POs/hour)</td><td>12.7</td></tr>
<tr><td>Total components planned (#)<sup>[1]</sup></td><td>80</td></tr>
<tr><td>Total components completed (#)<sup>[1]</sup></td><td>68</td></tr>
<tr><td>Overall completion rate (%)</td><td>85</td></tr>
</table>

Notes:

<sup>[1]</sup> Component counts based on target components defined in Table 3 of the [README.md](../../README.md). Components are counted by their codes (e.g., BOSP, RT, BSA) as defined in Table 2.3, where each code represents one component unit regardless of quantity.

<br><br>

Table 5.2 summarizes the total number of components of each type that were disassembled. The summary reflects the HD disassembly scenario.

**Table 5.2.** Component processing summary (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

| Code | Component | Quantity | Instances | Total components disassembled |
|------|-----------|----------|-----------|-------------------------------|
| BOSP | Body & spoiler | 1+1 | 10 | 20 |
| BAT | Battery | 1 | 10 | 10 |
| RT | Rear tires | 2 | 8 | 16 |
| FT | Front tires | 2 | 8 | 16 |
| FAX | Front axis | 1 | 8 | 8 |
| SSA | Small shock absorbers | 2 | 8 | 16 |
| CHS | Chassis | 1 | 8 | 8 |
| BSA | Big shock absorbers | 2 | 8 | 16 |
| **Total** | **-** | **-** | **68** | **110** |

Note: Only target components shown. Intermediate assemblies (FAXS, CRAXS, CREW) and remaining components (RAX, CRE, CSEB-NABS) are excluded from this count.

<br>

### 5.2 Workstation Performance

Table 5.3 shows the utilization and workload distribution across workstations. The average utilization across all workstations is 90.5%.

**Table 5.3.** Workstation performance indicators (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

| Indicator | WS-01 | WS-02 | WS-03 | WS-04 |
|--------|-------|-------|-------|-------|
| POs processed | 2/10 | 3/10 | 3/10 | 2/10 |
| Components disassembled | 16 | 18 | 18 | 16 |
| Total busy time (seconds) | 1,906 | 2,221 | 2,248 | 2,371 |
| Total busy time (minutes) | 31.8 | 37.0 | 37.5 | 39.5 |
| Utilization rate (%) | 78.9 | 91.9 | 93.0 | 98.1 |
| Quality types handled | HD | HD | HD | HD |

<br>

### 5.3 Production Order Analysis

Table 5.4 shows the handling time, in seconds, for each component across all production orders. The handling time includes both the disassembly time and the waiting time at a workstation.

**Table 5.4.** Component handling times per production order (seconds) (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 97 | 42 | 120 | 60 | 181 | 59 | 75 | 60 | 150 | 105 | 89 | 75 |
| S2 | BAT | 97 | 37 | 135 | 161 | 104 | 90 | 45 | 56 | 120 | 105 | 60 | 90 |
| S3 | RT | 97 | 20 | 105 | 90 | 105 | 90 | 60 | 83 | 120 | 120 | - | - |
| S4 | FT | 97 | 30 | 106 | 150 | 60 | 90 | 60 | 101 | 120 | 90 | - | - |
| S5 | FAXS | 177 | 46 | 208 | 109 | 226 | 177 | 234 | 187 | 149 | 124 | - | - |
| S6 | SSA | 224 | 93 | 211 | 431 | 180 | 213 | 181 | 128 | 271 | 176 | - | - |
| S7 | CHS | 139 | 47 | 121 | 151 | 149 | 135 | 120 | 238 | 75 | 120 | - | - |
| S8 | BSA | 161 | 57 | 149 | 173 | 135 | 105 | 168 | 272 | 195 | 90 | - | - |

<br><br>

Table 5.5 shows the actual disassembly time, in seconds, for each component across all production orders. Disassembly time represents only active processing duration (excludes waiting time).

**Table 5.5.** Component disassembly times per production order (seconds) (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 52 | 40 | 15 | 45 | 150 | 14 | 30 | 45 | 60 | 75 | 60 | 30 |
| S2 | BAT | 56 | 34 | 76 | 120 | 44 | 75 | 15 | 15 | 90 | 30 | 46 | 45 |
| S3 | RT | 51 | 16 | 45 | 45 | 45 | 77 | 30 | 49 | 45 | 75 | - | - |
| S4 | FT | 51 | 19 | 46 | 45 | 30 | 62 | 45 | 87 | 30 | 60 | - | - |
| S5 | FAXS | 138 | 44 | 148 | 94 | 195 | 162 | 179 | 158 | 89 | 79 | - | - |
| S6 | SSA | 153 | 45 | 181 | 191 | 150 | 153 | 122 | 67 | 211 | 147 | - | - |
| S7 | CHS | 111 | 49 | 90 | 135 | 119 | 120 | 93 | 210 | 45 | 75 | - | - |
| S8 | BSA | 117 | 59 | 134 | 123 | 90 | 75 | 93 | 242 | 135 | 45 | - | - |

<br><br>

Table 5.6 summarizes the performance indicators for each production order. PO-09 and PO-10 were incomplete with only 2 of 8 planned components disassembled.

**Table 5.6.** Production order performance indicators (Source: [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>PO-01</th><th>PO-02</th><th>PO-03</th><th>PO-04</th><th>PO-05</th><th>PO-06</th><th>PO-07</th><th>PO-08</th><th>PO-09</th><th>PO-10</th></tr>
<tr><td>Handling time (seconds)<sup>[1]</sup></td><td>1,155</td><td>1,325</td><td>1,140</td><td>959</td><td>943</td><td>1,125</td><td>1,200</td><td>930</td><td>149</td><td>165</td></tr>
<tr><td>Disassembly time (seconds)<sup>[2]</sup></td><td>735</td><td>798</td><td>823</td><td>738</td><td>606</td><td>873</td><td>705</td><td>586</td><td>106</td><td>75</td></tr>
<tr><td>Waiting time (seconds)<sup>[3]</sup></td><td>16</td><td>16</td><td>1</td><td>31</td><td>1,006</td><td>916</td><td>841</td><td>901</td><td>1,742</td><td>1,711</td></tr>
<tr><td>Lead time (seconds)<sup>[4]</sup></td><td>1,231</td><td>1,051</td><td>1,171</td><td>1,006</td><td>1,877</td><td>2,041</td><td>1,997</td><td>1,786</td><td>-</td><td>-</td></tr>
<tr><td>Components planned (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td></tr>
<tr><td>Components completed (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>2</td><td>2</td></tr>
<tr><td>Completion rate (%)</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>25</td><td>25</td></tr>
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

Table 6.1 summarizes the data processing pipeline and event counts. A signal-to-noise ratio of 36% was achieved after filtering. For additional details, see the [`scenario_02_data_analyzed.xlsx`](data/scenario_02_data_analyzed.xlsx) file, specifically the "pre-process", "extraction", and "process_calculation" sheets.

**Table 6.1.** Data quality statistics showing processing stages

| Stage | Event count | Description |
|-------|-------------|-------------|
| **Raw events** | 723 | Original recorded events from IT system |
| **Preprocessed** | 733 | +10 events added during preprocessing |
| **Clean events** | 265 | Final usable events after cleaning |
| - OK (from raw) | 243 | Events validated from raw data (includes sequence errors) |
| - Cleaned | 45 | Manually corrected events |
| - Calculated | 10 | Estimated from averages |
| - Start | 10 | Manually added start events |
| - Unfinished | 43 | Events marked as unfinished PO (excluded) |
| - Missing | 2 | Missing events (excluded) |
| **Filtered noise** | 468 | Events removed as noise (64%) |
| **Signal-to-noise ratio** | 36% | Percentage of usable data |

