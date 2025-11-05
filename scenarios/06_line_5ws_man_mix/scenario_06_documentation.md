# Scenario 6: Line with Mixed Quality Portfolio (5 Workstations)

**Date:** January 10, 2025
**Duration:** 11:17:00 - 11:57:01

## Summary
📊 **10 cars** | 🎯 **HD (30%), SA (30%), RD (30%), TL (10%)** | 🏭 **5 workstations** | 👷 **Manual processing** | ⏱️ **40.02 minutes** | ✅ **96.75% completion**

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

This scenario presents a 5-workstation line configuration processing 10 cars with a mixed quality portfolio.

### 1.1 Key Characteristics

Table 1.1 summarizes the key characteristics of this scenario. The configuration uses a line layout with manual processing, demonstrating sequential multi-station flow with quality-dependent routing.

**Table 1.1.** Key characteristics of Scenario 6

| Characteristic | Value |
|---------------|--------|
| **System design** | Line with 5 workstations (WS-01 to WS-05) |
| **Product portfolio** | 10 cars with mixed quality types |
| **Product mix** | HD (30%), SA (30%), RD (30%), TL (10%) |
| **Disassembly depths** | Variable (quality-dependent) |
| **Total units** | 10 cars (PO-01 to PO-10) |
| **Processing type** | Manual (operator disassembles by hand) |
| **Flow pattern** | Multi-station flow (sequential movement between stations) |

<br>



### 1.2 Material Flow
Figure 1.1 shows the material flow diagram, which illustrates how EOL products are routed through the disassembly system.

![Material Flow Diagram](figures/scenario_06_material_flow.svg)

**Figure 1.1:** Material flow for mixed quality portfolio with multi-station processing

<br>

### 1.3 Files & Resources

Table 1.2 lists all the data, documentation, and production order (PO) files for this disassembly scenario. For a more detailed description of the Excel spreadsheet, please refer to the [README.md](../../README.md) file.

**Table 1.2.** Complete file listing for Scenario 6

| **Category** | **File** | **Description** |
|--------------|----------|-----------------|
| **Data files** | [`scenario_06_data_raw.csv`](data/scenario_06_data_raw.csv) | Raw material flow data (563 recorded events) |
| | [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx) | Cleaned data with analysis sheets |
| **Material flow** | [`scenario_06_material_flow.svg`](figures/scenario_06_material_flow.svg) | System layout and material flow diagram |
| **Disassembly sequences** | [`scenario_06_sequence_HD.svg`](figures/scenario_06_sequence_HD.svg) | HD (Hail damage) disassembly sequence |
| | [`scenario_06_sequence_TL.svg`](figures/scenario_06_sequence_TL.svg) | TL (Total loss) disassembly sequence |
| | [`scenario_06_sequence_SA.svg`](figures/scenario_06_sequence_SA.svg) | SA (Shock absorber) disassembly sequence |
| | [`scenario_06_sequence_RD.svg`](figures/scenario_06_sequence_RD.svg) | RD (Rear damage) disassembly sequence |
| **Work instructions** | [`scenario_06_WI_HD.pdf`](figures/scenario_06_WI_HD.pdf) | Work instructions for HD quality type |
| | [`scenario_06_WI_TL.pdf`](figures/scenario_06_WI_TL.pdf) | Work instructions for TL quality type |
| | [`scenario_06_WI_SA.pdf`](figures/scenario_06_WI_SA.pdf) | Work instructions for SA quality type |
| | [`scenario_06_WI_RD.pdf`](figures/scenario_06_WI_RD.pdf) | Work instructions for RD quality type |

<br>

<!-- ================================================== -->
<!-- SYSTEM CONFIGURATION -->
<!-- ================================================== -->
## 2. System Configuration

### 2.1 Workstation Layout

Table 2.1 shows the physical configuration of the workstations within the system. B-Transfer serves as the final output buffer for finished components.

**Table 2.1.** Workstation layout and buffer configuration (Source: [`scenario_06_material_flow.svg`](figures/scenario_06_material_flow.svg))

| Workstation | Position | Buffer before | Buffer after | Equipment type |
|---------|----------|---------------|--------------|----------------|
| WS-01 | Line workstation 1 | B-Goods-In | B-02, B-Transfer | Manual |
| WS-02 | Line workstation 2 | B-Goods-In, B-02 | B-Transfer | Manual |
| WS-03 | Line workstation 3 | B-03 | B-04, B-05, B-Transfer | Manual |
| WS-04 | Line workstation 4 | B-04 | B-05, B-Transfer | Manual |
| WS-05 | Line workstation 5 | B-05 | B-Transfer | Manual |

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
| CORE | Chassis with systems and engine (excluding rear axis) | 1 | Reuse |
| BSA | Big shock absorbers | 2 | Remanufacture |
| RAX (HD) | Rear axis | 1 | Recycle |
| RAX (RD) | Rear axis | 1 | Repair |
| CRE (TL) | Chassis, remaining systems, engine | 1 | Recycle |
| CSEB-NABS (SA) | Chassis, systems, engine, body | 1 | Recycle |

<br>

<!-- ================================================== -->
<!-- DISASSEMBLY PROCESS -->
<!-- ================================================== -->
## 3. Disassembly Process

### 3.1 Quality-Based Routing

Table 3.1 illustrates the routing patterns for each quality type through the disassembly system. Each vehicle follows a specific route based on its quality type, with vehicles moving between multiple workstations.

**Table 3.1.** Quality-dependent routing and target components (Source: [`scenario_06_material_flow.svg`](figures/scenario_06_material_flow.svg))

| Quality type | Count | Material flow | Target components | Remaining |
|--------------|-------|---------------|-------------------|-----------|
| **HD** (Hail damage) | 3 | WS-01→WS-02→WS-03→WS-04→WS-05 | BOSP, BAT, RT, FT, FAXS, SSA, CHS, BSA | RAX (HD) |
| **SA** (Shock absorber) | 3 | Variable (WS-02→WS-05 or WS-01→WS-02→WS-05) | BOSP, RT, FT, SSA, BSA | CSEB-NABS (SA) |
| **RD** (Rear damage) | 3 | WS-01→WS-02→WS-04→WS-05 | BOSP, RT, BSA | RAX (RD) |
| **TL** (Total loss) | 1 | WS-01→WS-02 | BOSP, BAT, RT, FT | CRE (TL) |

<br>

### 3.2 Process Step Mapping

Table 3.2 maps which disassembly steps are performed for each quality type. The table shows typical workstation assignments for each disassembly step.

**Table 3.2.** Process steps by quality type (Source: [`scenario_06_material_flow.svg`](figures/scenario_06_material_flow.svg))

| Step | Operation | HD | TL | SA | RD | Workstation(s) |
|------|-----------|----|----|----|----|-------------|
| S1 | Remove body & spoiler | ✓ | ✓ | - | ✓ | WS-01 |
| S2 | Remove battery | ✓ | ✓ | - | - | WS-01 |
| S3 | Remove rear tires | ✓ | ✓ | ✓ | ✓ | WS-02 |
| S4 | Remove front tires | ✓ | ✓ | ✓ | - | WS-02 |
| S5 | Process FAXS | ✓ | - | - | - | WS-03 |
| S6 | Remove small shock absorbers | ✓ | - | ✓ | - | WS-05 |
| S7 | Remove chassis/core | ✓ | - | - | ✓ | WS-04 |
| S8 | Remove big shock absorbers | ✓ | - | ✓ | ✓ | WS-05 |

<br>

<!-- ================================================== -->
<!-- PRODUCTION SCHEDULE -->
<!-- ================================================== -->
## 4. Production Schedule

Table 4.1 shows the arrival schedule and processing status of all production orders. PO-10 routing through WS-01 was an operator-introduced error; SA quality should typically start at WS-02.

**Table 4.1.** Production order schedule and completion status (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheets "delivery_times" and "extraction")

| Order | Arrival time | Quality type | Material flow | Status |
|-------|--------------|--------------|-------|--------|
| PO-01 | 11:17:00 | SA | WS-02→WS-05 | Complete |
| PO-02 | 11:18:30 | RD | WS-01→WS-02→WS-04→WS-05 | Complete |
| PO-03 | 11:20:00 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-04 | 11:21:30 | TL | WS-01→WS-02 | Complete |
| PO-05 | 11:23:00 | SA | WS-02→WS-05 | Complete |
| PO-06 | 11:24:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Complete |
| PO-07 | 11:26:00 | RD | WS-01→WS-02→WS-04→WS-05 | Complete |
| PO-08 | 11:27:30 | HD | WS-01→WS-02→WS-03→WS-04→WS-05 | Incomplete |
| PO-09 | 11:29:00 | RD | WS-01→WS-02→WS-04→WS-05 | Complete |
| PO-10 | 11:30:30 | SA | WS-01→WS-02→WS-05 | Incomplete |

<br>

<!-- ================================================== -->
<!-- SCENARIO ANALYSIS -->
<!-- ================================================== -->
## 5. Scenario Analysis

> 📊 **Note on Data Presentation:** The tables and metrics in this section provide a concise summary. For detailed analysis, refer to the Excel analysis file ([`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx)). This file contains the complete dataset and calculations.


### 5.1 System-Level Indicators

Table 5.1 presents the overall system throughput performance. Eight of ten production orders had a completion rate of 100%.

**Table 5.1.** System-level performance indicators (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>Value</th></tr>
<tr><td>Total processing time (minutes)</td><td>40.02</td></tr>
<tr><td>POs processed (#)</td><td>10</td></tr>
<tr><td>System throughput rate (POs/hour)</td><td>14.5</td></tr>
<tr><td>Total components planned (#)<sup>[1]</sup></td><td>53</td></tr>
<tr><td>Total components completed (#)<sup>[1]</sup></td><td>51</td></tr>
<tr><td>Overall completion rate (%)</td><td>96.75</td></tr>
</table>

Notes:

<sup>[1]</sup> Component counts based on target components defined in Table 3 of the [README.md](../../README.md). Components are counted by their codes (e.g., BOSP, RT, BSA) as defined in Table 2.3, where each code represents one component unit regardless of quantity.

<br><br>

Table 5.2 summarizes the total number of components of each type that were disassembled. The summary reflects the mixed quality portfolio with different disassembly depths and multi-station flow.

**Table 5.2.** Component processing summary (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheet "analysis")

| Code | Component | Quantity | Instances | Total components disassembled |
|------|-----------|----------|-----------|-------------------------------|
| BOSP | Body & spoiler | 1+1 | 8 | 16 |
| BAT | Battery | 1 | 4 | 4 |
| RT | Rear tires | 2 | 10 | 20 |
| FT | Front tires | 2 | 7 | 14 |
| SSA | Small shock absorbers | 2 | 6 | 12 |
| CHS | Chassis | 1 | 3 | 3 |
| BSA | Big shock absorbers | 2 | 7 | 14 |
| CORE | Chassis with systems and engine | 1 | 3 | 3 |
| FAXS | Front axis with shock absorbers | 1 | 3 | 3 |
| **Total** | **-** | **-** | **51** | **89** |

Note: Only target components shown. Remaining components (RAX, CRE, CSEB-NABS) are excluded from this count. FAXS is included as it was removed but not separated into SSA and FAX in this scenario (FAX = 0 instances). Intermediate assemblies CRAXS and CREW are also excluded.

<br>

### 5.2 Workstation Performance

Table 5.3 shows the utilization and workload distribution across workstations. Workstation performance varies based on the routing patterns and quality types processed. The average utilization across all workstations is 54.3%.

**Table 5.3.** Workstation performance indicators (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheet "analysis")

| Indicator | WS-01 | WS-02 | WS-03 | WS-04 | WS-05 |
|--------|-------|-------|-------|-------|-------|
| POs processed | 8/10 | 10/10 | 3/10 | 6/10 | 9/10 |
| Components disassembled | 12 | 17 | 3 | 6 | 13 |
| Total busy time (seconds) | 990 | 2,009 | 495 | 1,304 | 1,604 |
| Total busy time (minutes) | 16.5 | 33.5 | 8.3 | 21.7 | 26.7 |
| Utilization rate (%) | 41.2 | 83.7 | 20.6 | 54.3 | 66.8 |
| Quality types handled | HD, TL, RD | All | HD | HD, RD | HD, SA, RD |

<br>

### 5.3 Production Order Analysis

Table 5.4 shows the handling time, in seconds, for each component across all production orders. The handling time includes both the disassembly time and the waiting time at a workstation.

**Table 5.4.** Component handling times per production order (seconds)
*Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx) - Process_calculation sheet*

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 78 | 30 | - | 139 | 45 | 60 | - | 94 | 75 | 60 | 60 | 89 |
| S2 | BAT | 71 | 19 | - | - | 75 | 89 | - | 75 | - | 44 | - | - |
| S3 | RT | 163 | 93 | 90 | 210 | 123 | 105 | 160 | 90 | 165 | 120 | 405 | 164 |
| S4 | FT | 124 | 59 | 90 | - | 229 | 172 | 56 | 105 | - | 127 | - | 90 |
| S5 | FAXS | 175 | 61 | - | - | 240 | - | - | 120 | - | 165 | - | - |
| S6 | SSA | 173 | 131 | 90 | - | 45 | - | 135 | 240 | - | 405 | - | 120 |
| S7 | CHS/CORE | 147 | 72 | - | 239 | 240 | - | - | 90 | 120 | 90 | 105 | - |
| S8 | BSA | 122 | 35 | 165 | 120 | 105 | - | 165 | 75 | 135 | - | 90 | - |

<br><br>

Table 5.5 shows the actual disassembly time, in seconds, for each component across all production orders. Disassembly time represents only active processing duration (excludes waiting time).

**Table 5.5.** Component disassembly times per production order (seconds) (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 43 | 30 | - | 105 | 15 | 16 | - | 59 | 30 | 31 | 31 | 60 |
| S2 | BAT | 38 | 7 | - | - | 45 | 44 | - | 34 | - | 30 | - | - |
| S3 | RT | 112 | 96 | 60 | 136 | 59 | 75 | 112 | 59 | 75 | 75 | 375 | 90 |
| S4 | FT | 87 | 58 | 59 | - | 192 | 134 | 41 | 30 | - | 90 | - | 61 |
| S5 | FAXS | 110 | 38 | - | - | 150 | - | - | 74 | - | 105 | - | - |
| S6 | SSA | 160 | 110 | 60 | - | 90 | - | 121 | 210 | - | 360 | - | 120 |
| S7 | CHS/CORE | 108 | 60 | - | 149 | 210 | - | - | 61 | 61 | 74 | 90 | - |
| S8 | BSA | 90 | 39 | 150 | 75 | 75 | - | 135 | 45 | 90 | - | 60 | - |

<br><br>

Table 5.6 summarizes the performance indicators for each production order. PO-08 and PO-10 had incomplete disassembly with 87.5% and 80% completion rates respectively.

**Table 5.6.** Production order performance indicators (Source: [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>PO-01</th><th>PO-02</th><th>PO-03</th><th>PO-04</th><th>PO-05</th><th>PO-06</th><th>PO-07</th><th>PO-08</th><th>PO-09</th><th>PO-10</th></tr>
<tr><td>Handling time (seconds)<sup>[1]</sup></td><td>435</td><td>708</td><td>1,102</td><td>426</td><td>516</td><td>889</td><td>495</td><td>1,011</td><td>660</td><td>463</td></tr>
<tr><td>Disassembly time (seconds)<sup>[2]</sup></td><td>329</td><td>465</td><td>836</td><td>269</td><td>409</td><td>572</td><td>256</td><td>765</td><td>556</td><td>331</td></tr>
<tr><td>Waiting time (seconds)<sup>[3]</sup></td><td>151</td><td>154</td><td>451</td><td>256</td><td>524</td><td>692</td><td>705</td><td>915</td><td>810</td><td>1,188</td></tr>
<tr><td>Lead time (seconds)<sup>[4]</sup></td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td><td>-</td></tr>
<tr><td>Components planned (#)</td><td>4</td><td>4</td><td>8</td><td>4</td><td>4</td><td>8</td><td>4</td><td>8</td><td>4</td><td>5</td></tr>
<tr><td>Components completed (#)</td><td>4</td><td>4</td><td>8</td><td>4</td><td>4</td><td>8</td><td>4</td><td>7</td><td>4</td><td>4</td></tr>
<tr><td>Completion rate (%)</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>87.5</td><td>100</td><td>80</td></tr>
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

Table 6.1 summarizes the data processing pipeline and event counts. A signal-to-noise ratio of 56% was achieved after filtering. For additional details, see the [`scenario_06_data_analyzed.xlsx`](data/scenario_06_data_analyzed.xlsx) file, specifically the "pre-process", "extraction", and "process_calculation" sheets.

**Table 6.1.** Data quality statistics showing processing stages

| Stage | Event count | Description |
|-------|-------------|-------------|
| **Raw events** | 563 | Original recorded events from IT system |
| **Preprocessed** | 573 | +10 events added during preprocessing |
| **Clean events** | 321 | Final usable events after cleaning |
| - OK (from raw) | 235 | Events validated from raw data |
| - Cleaned | 72 | Manually corrected events |
| - Calculated | 18 | Estimated from averages |
| - Start | 10 | Manually added start events |
| - Unfinished | 14 | Events marked as unfinished PO (excluded) |
| **Filtered noise** | 252 | Events removed as noise (44%) |
| **Signal-to-noise ratio** | 56% | Percentage of usable data |