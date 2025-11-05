# Scenario 3: Line with HD Portfolio (5 Workstations)

**Date:** January 13, 2025
**Duration:** 09:30:00 - 10:09:47

## Summary
📊 **10 cars** | 🎯 **HD (100%)** | 🏭 **5 workstations** | 👷 **Automated processing** | ⏱️ **39.78 minutes** | ✅ **92.5% completion**

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

This scenario presents a 5-workstation line configuration processing 10 cars with a single quality type (HD). The line layout uses buffers B-01 through B-05 as transfer points between workstations, with a special routing for FAXS components from WS-03 to WS-05 for further processing.

### 1.1 Key Characteristics

Table 1.1 summarizes the key characteristics of this scenario. The configuration uses a line layout with automated processing and sequential material flow through intermediate buffers.

**Table 1.1.** Key characteristics of Scenario 3

| Characteristic | Value |
|---------------|--------|
| **System design** | Line with 5 workstations (WS-01 to WS-05) |
| **Product portfolio** | 10 cars with HD quality type only |
| **Product mix** | HD (100%) |
| **Disassembly depths** | Fixed |
| **Total units** | 10 cars (PO-01 to PO-10) |
| **Processing type** | Automated (operator uses cordless screwdriver) |
| **Flow pattern** | Multi-station flow (sequential processing through WS-01 to WS-05) |

<br>

### 1.2 Material Flow
Figure 1.1 shows the material flow diagram, which illustrates how EOL products are routed through the disassembly system.

![Material Flow Diagram](figures/scenario_03_material_flow.svg)

**Figure 1.1:** Material flow for HD product portfolio with 5 workstations (WS-01 to WS-05) in line configuration

<br>

### 1.3 Files & Resources

Table 1.2 lists all the data, documentation, and production order (PO) files for this disassembly scenario. For a more detailed description of the Excel spreadsheet, please refer to the [README.md](../../README.md) file.

**Table 1.2.** Complete file listing for Scenario 3

| **Category** | **File** | **Description** |
|--------------|----------|-----------------|
| **Data files** | [`scenario_03_data_raw.csv`](data/scenario_03_data_raw.csv) | Raw material flow data (1,235 recorded events) |
| | [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx) | Cleaned data with analysis sheets |
| **Material flow** | [`scenario_03_material_flow.svg`](figures/scenario_03_material_flow.svg) | System layout and material flow diagram |
| **Disassembly sequences** | [`scenario_03_sequence_HD.svg`](figures/scenario_03_sequence_HD.svg) | HD (Hail damage) disassembly sequence |
| **Work instructions** | [`scenario_03_WI_HD.pdf`](figures/scenario_03_WI_HD.pdf) | Work instructions for HD quality type |

<br>

<!-- ================================================== -->
<!-- SYSTEM CONFIGURATION -->
<!-- ================================================== -->
## 2. System Configuration

### 2.1 Workstation Layout

Table 2.1 shows the physical configuration of the workstations within the system. B-Transfer serves as the final output buffer for finished components.

**Table 2.1.** Workstation layout and buffer configuration (Source: [`scenario_03_material_flow.svg`](figures/scenario_03_material_flow.svg))

| Workstation | Position | Buffer before | Buffer after | Equipment type |
|---------|----------|---------------|--------------|----------------|
| WS-01 | Line workstation 1 | B-Goods-In | B-01 | Automated |
| WS-02 | Line workstation 2 | B-01 | B-02 | Automated |
| WS-03 | Line workstation 3 | B-02 | B-03 | Automated |
| WS-04 | Line workstation 4 | B-03 | B-04 | Automated |
| WS-05 | Line workstation 5 | B-04 | B-Transfer | Automated |

<br>

### 2.2 Workstation Distances

Table 2.2 shows the physical distances between workstations and key locations in the system. These distances are measured in meters and represent the shortest path between locations.

**Table 2.2.** Workstation distance matrix in meters (measured approximately)

|            | Goods-in | WS-01 | WS-02 | WS-03 | WS-04 | WS-05 | Warehouse |
|------------|----------|-------|-------|-------|-------|-------|-----------|
| Goods-in   | 0        | 3.2   | 5.4   | 3.2   | 5.4   | 7.8   | 5.2       |
| WS-01      | 3.2      | 0     | 2.5   | 4.0   | 4.7   | 6.4   | 2.0       |
| WS-02      | 5.4      | 2.5   | 0     | 4.7   | 4.0   | 4.7   | 2.0       |
| WS-03      | 3.2      | 4.0   | 4.7   | 0     | 2.5   | 5.0   | 2.0       |
| WS-04      | 5.4      | 4.7   | 4.0   | 2.5   | 0     | 2.5   | 2.0       |
| WS-05      | 7.8      | 6.4   | 4.7   | 5.0   | 2.5   | 0     | 2.0       |
| Warehouse  | 5.2      | 2.0   | 2.0   | 2.0   | 2.0   | 2.0   | 0         |

<br>

### 2.3 Component Reference

Table 2.3 lists all the components that can be disassembled from the cars. FAXS removed at WS-03, sent to WS-05 for SSA and FAX separation.

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

Table 3.1 illustrates the routing patterns for each quality type through the disassembly system. FAXS component routing: WS-03→B-05→WS-05. Component completion varies by PO.

**Table 3.1.** Quality-dependent routing and target components (Source: [`scenario_03_material_flow.svg`](figures/scenario_03_material_flow.svg))

| Quality type | Count | Material flow | Target components | Remaining |
|--------------|-------|-------|-------------------|-----------|
| **HD** (Hail damage) | 10 | WS-01→WS-02→WS-03→WS-04→WS-05 | BOSP, BAT, RT, FT, FAXS*, SSA, FAX, CHS, BSA** | RAX (HD) |

<br>

### 3.2 Process Step Mapping

Table 3.2 maps which disassembly steps are performed for each quality type at each workstation.

**Table 3.2.** Process steps by quality type (Source: [`scenario_03_material_flow.svg`](figures/scenario_03_material_flow.svg)) and workstation assignment

| Step | Operation | HD Quality | Workstation(s) |
|------|-----------|------------|------------|
| S1 | Remove body & spoiler | ✓ | WS-01 |
| S2 | Remove battery | ✓ | WS-02 |
| S3 | Remove rear tires | ✓ | WS-02 |
| S4 | Remove front tires | ✓ | WS-02 |
| S5 | Remove FAXS | ✓ | WS-03 |
| S6 | Remove small shock absorbers (from FAXS) | ✓ | WS-05 |
| S7 | Separate front axis (from FAXS) | ✓ | WS-05 |
| S8 | Remove chassis | ✓ | WS-04 |
| S9 | Remove big shock absorbers | ✓ | WS-05 |

<br>

<!-- ================================================== -->
<!-- PRODUCTION SCHEDULE -->
<!-- ================================================== -->
## 4. Production Schedule

Table 4.1 shows the arrival schedule and processing status of all production orders. PO-06 to PO-10 had incomplete disassembly with missing components.

**Table 4.1.** Production order schedule and completion status (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheets "delivery_times" and "extraction")

| Order | Arrival time | Quality type | Material flow | Status |
|-------|--------------|--------------|----------------|--------|
| PO-01 | 09:30:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-02 | 09:31:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-03 | 09:33:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-04 | 09:34:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-05 | 09:36:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-06 | 09:37:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |
| PO-07 | 09:40:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |
| PO-08 | 09:40:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |
| PO-09 | 09:43:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |
| PO-10 | 09:44:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |

<br>

<!-- ================================================== -->
<!-- SCENARIO ANALYSIS -->
<!-- ================================================== -->
## 5. Scenario Analysis

> 📊 **Note on Data Presentation:** The tables and metrics in this section provide a concise summary. For detailed analysis, refer to the Excel analysis file ([`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx)). This file contains the complete dataset and calculations.

### 5.1 System-Level Indicators

Table 5.1 presents the overall system throughput performance. Five of ten production orders had a completion rate of 100%.

**Table 5.1.** System-level performance indicators (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>Value</th></tr>
<tr><td>Total processing time (minutes)</td><td>39.78</td></tr>
<tr><td>POs processed (#)</td><td>10</td></tr>
<tr><td>System throughput rate (POs/hour)</td><td>14.0</td></tr>
<tr><td>Total components planned (#)<sup>[1]</sup></td><td>80</td></tr>
<tr><td>Total components completed (#)<sup>[1]</sup></td><td>74</td></tr>
<tr><td>Overall completion rate (%)</td><td>92.5</td></tr>
</table>

Notes:

<sup>[1]</sup> Component counts based on target components defined in Table 3 of the [README.md](../../README.md). Components are counted by their codes (e.g., BOSP, RT, BSA) as defined in Table 2.3, where each code represents one component unit regardless of quantity.

<br><br>

Table 5.2 summarizes the total number of components of each type that were disassembled. SSA and FAX separated from FAXS at WS-05. BSA only completed for PO-01 to PO-05.

**Table 5.2.** Component processing summary (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheet "analysis")

| Code | Component | Quantity | Instances | Total components disassembled |
|------|-----------|----------|-----------|-------------------------------|
| BOSP | Body & spoiler | 1+1 | 10 | 20 |
| BAT | Battery | 1 | 10 | 10 |
| RT | Rear tires | 2 | 10 | 20 |
| FT | Front tires | 2 | 10 | 20 |
| FAXS | Front axis with shock absorbers | 1 | 1 | 1 |
| SSA | Small shock absorbers | 2 | 9 | 18 |
| FAX | Front axis | 1 | 9 | 9 |
| CHS | Chassis | 1 | 10 | 10 |
| BSA | Big shock absorbers | 2 | 5 | 10 |
| **Total** | **-** | **-** | **74** | **118** |

Note: Only target components shown. Remaining components (RAX, CRE, CSEB-NABS) and intermediate assemblies (CRAXS, CREW) are excluded from this count. FAXS appears once as it was removed but not separated into SSA and FAX (incomplete order). Of the 10 FAXS removed at WS-03, 9 were separated into SSA and FAX at WS-05.

<br>

### 5.2 Workstation Performance

Table 5.3 shows the utilization and workload distribution across workstations. The average utilization across all workstations is 60.3%. WS-05 processes SSA/FAX separation from FAXS and BSA components.

**Table 5.3.** Workstation performance indicators (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheet "analysis")

| Indicator | WS-01 | WS-02 | WS-03 | WS-04 | WS-05 |
|--------|-------|-------|-------|-------|-------|
| POs processed | 10/10 | 10/10 | 10/10 | 10/10 | 9/10 |
| Components disassembled | 20 | 20 | 10 | 10 | 14 |
| Total busy time (seconds) | 1,171 | 1,875 | 1,173 | 1,379 | 1,600 |
| Total busy time (minutes) | 19.5 | 31.3 | 19.6 | 23.0 | 26.7 |
| Utilization rate (%) | 49.1 | 78.6 | 49.1 | 57.8 | 67.0 |
| Quality types handled | HD | HD | HD | HD | HD |

<br>

### 5.3 Production Order Analysis

Table 5.4 shows the handling time, in seconds, for each component across all production orders. The handling time includes both the disassembly time and the waiting time at a workstation.

**Table 5.4.** Component handling times per production order (seconds)
*Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx) - Process_calculation sheet*

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 55 | 10 | 60 | 56 | 45 | 45 | 59 | 45 | 75 | 45 | 60 | 63 |
| S2 | BAT | 54 | 16 | 59 | 37 | 45 | 69 | 45 | 90 | 60 | 45 | 44 | 41 |
| S3 | RT | 117 | 68 | 150 | 74 | 60 | 241 | 61 | 120 | 44 | 60 | 165 | 195 |
| S4 | FT | 71 | 33 | 60 | 105 | 106 | 45 | 90 | 105 | 45 | 15 | 46 | 92 |
| S5 | FAXS | 170 | 135 | 135 | 135 | 45 | 121 | 90 | 120 | 421 | 419 | 119 | 91 |
| S6 | SSA | 124 | 24 | 149 | 120 | 124 | 136 | 90 | 106 | 119 | 169 | 105 | - |
| S7 | CHS | 123 | 22 | 162 | 135 | 136 | 105 | 90 | 121 | 145 | 105 | 106 | 123 |
| S8 | BSA | 109 | 36 | 135 | 90 | 159 | 86 | 75 | - | - | - | - | - |

<br><br>

Table 5.5 shows the actual disassembly time, in seconds, for each component across all production orders. Disassembly time represents only active processing duration (excludes waiting time).

**Table 5.5.** Component disassembly times per production order (seconds) (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 33 | 12 | 29 | 34 | 30 | 30 | 44 | 30 | 60 | 30 | 16 | 30 |
| S2 | BAT | 33 | 12 | 44 | 7 | 30 | 44 | 30 | 30 | 44 | 30 | 44 | 26 |
| S3 | RT | 72 | 52 | 106 | 60 | 46 | 180 | 30 | 90 | 15 | 15 | 61 | 120 |
| S4 | FT | 33 | 18 | 29 | 45 | 75 | 15 | 31 | 30 | 15 | 29 | 16 | 45 |
| S5 | FAXS | 76 | 39 | 120 | 104 | 45 | 62 | 30 | 44 | 150 | 89 | 74 | 45 |
| S6 | SSA | 79 | 35 | 135 | 30 | 79 | 61 | 45 | 89 | 89 | 124 | 60 | - |
| S7 | CHS | 82 | 21 | 121 | 90 | 90 | 60 | 60 | 90 | 104 | 60 | 60 | 82 |
| S8 | BSA | 71 | 34 | 91 | 45 | 121 | 41 | 59 | - | - | - | - | - |

<br><br>

Table 5.6 summarizes the performance indicators for each production order. PO-06 to PO-10 had incomplete disassembly with PO-10 missing SSA and BSA components.

**Table 5.6.** Production order performance indicators (Source: [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>PO-01</th><th>PO-02</th><th>PO-03</th><th>PO-04</th><th>PO-05</th><th>PO-06</th><th>PO-07</th><th>PO-08</th><th>PO-09</th><th>PO-10</th></tr>
<tr><td>Handling time (seconds)<sup>[1]</sup></td><td>910</td><td>752</td><td>720</td><td>848</td><td>600</td><td>707</td><td>909</td><td>858</td><td>645</td><td>605</td></tr>
<tr><td>Disassembly time (seconds)<sup>[2]</sup></td><td>675</td><td>415</td><td>516</td><td>493</td><td>329</td><td>403</td><td>477</td><td>377</td><td>331</td><td>348</td></tr>
<tr><td>Waiting time (seconds)<sup>[3]</sup></td><td>152</td><td>958</td><td>533</td><td>1,221</td><td>1,435</td><td>862</td><td>992</td><td>751</td><td>1,036</td><td>808</td></tr>
<tr><td>Lead time (seconds)<sup>[4]</sup></td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr>
<tr><td>Components planned (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td></tr>
<tr><td>Components completed (#)</td><td>8</td><td>8</td><td>8</td><td>8</td><td>8</td><td>7</td><td>7</td><td>7</td><td>7</td><td>6</td></tr>
<tr><td>Completion rate (%)</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>87.5</td><td>87.5</td><td>87.5</td><td>87.5</td><td>75</td></tr>
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

Table 6.1 summarizes the data processing pipeline and event counts. A signal-to-noise ratio of 37% was achieved after filtering. For additional details, see the [`scenario_03_data_analyzed.xlsx`](data/scenario_03_data_analyzed.xlsx) file, specifically the "pre-process", "extraction", and "process_calculation" sheets.

**Table 6.1.** Data quality statistics showing processing stages

| Stage | Event count | Description |
|-------|-------------|-------------|
| **Raw events** | 1,235 | Original recorded events from IT system |
| **Preprocessed** | 1,245 | +10 events added during preprocessing |
| **Clean events** | 464 | Final usable events after cleaning |
| - OK (from raw) | 396 | Events validated from raw data (includes sequence errors) |
| - Cleaned | 66 | Manually corrected events |
| - Calculated | 23 | Estimated from averages |
| - Start | 10 | Manually added start events |
| - Unfinished | 31 | Events marked as unfinished PO (excluded) |
| - Missing | 5 | Missing events (excluded) |
| **Filtered noise** | 781 | Events removed as noise (63%) |
| **Signal-to-noise ratio** | 37% | Percentage of usable data |