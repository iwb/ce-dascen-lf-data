# Scenario 1: Line with Mixed Quality Types (3 Workstations)

**Date:** January 7, 2025  
**Duration:** 09:26:00 - 10:06:16

## Summary
📊 **10 cars** | 🎯 **RD (60%), TL (20%), SA (20%)** | 🏭 **3 workstations** | 👷 **Automated processing** | ⏱️ **40.27 minutes** | ✅ **100% completion**

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

This scenario presents a 3-workstation line configuration processing 10 cars with mixed quality types (RD, TL, SA).

### 1.1 Key Characteristics

Table 1.1 summarizes the key characteristics of this scenario. The configuration uses a line layout with automated processing for three different quality types.

**Table 1.1.** Key characteristics of Scenario 1

| Characteristic | Value |
|---------------|--------|
| **System design** | Line with 3 workstations (WS-03, WS-04, WS-05) |
| **Product portfolio** | 10 cars with 3 quality types (no HD) |
| **Product mix** | RD (60%), TL (20%), SA (20%) |
| **Disassembly depths** | Variable (quality-dependent) |
| **Total units** | 10 cars (PO-01 to PO-10) |
| **Processing type** | Automated (operator uses cordless screwdriver) |
| **Flow pattern** | Multi-station flow |

<br>

### 1.2 Material Flow

Figure 1.1 shows the material flow diagram, which illustrates how EOL products are routed through the disassembly system.

![Material Flow Diagram](figures/scenario_01_material_flow.svg)

**Figure 1.1:** Material flow for mixed product portfolio (TL, RD, SA) with 3 workstations (WS-03 to WS-05) in linear configuration

<br>

### 1.3 Files & Resources

Table 1.2 lists all the data, documentation, and production order (PO) files for this disassembly scenario. For a more detailed description of the Excel spreadsheet, please refer to the [README.md](../../README.md) file.

**Table 1.2.** Complete file listing for Scenario 1

| **Category** | **File** | **Description** |
|--------------|----------|-----------------|
| **Data files** | [`scenario_01_data_raw.csv`](data/scenario_01_data_raw.csv) | Raw material flow data (477 recorded events) |
| | [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx) | Cleaned data with analysis sheets |
| **Material flow** | [`scenario_01_material_flow.svg`](figures/scenario_01_material_flow.svg) | System layout and material flow diagram |
| **Disassembly sequences** | [`scenario_01_sequence_RD.svg`](figures/scenario_01_sequence_RD.svg) | RD (Rear damage) disassembly sequence |
| | [`scenario_01_sequence_TL.svg`](figures/scenario_01_sequence_TL.svg) | TL (Total loss) disassembly sequence |
| | [`scenario_01_sequence_SA.svg`](figures/scenario_01_sequence_SA.svg) | SA (Shock absorber) disassembly sequence |
| **Work instructions** | [`scenario_01_WI_RD.pdf`](figures/scenario_01_WI_RD.pdf) | Work instructions for RD quality type |
| | [`scenario_01_WI_TL.pdf`](figures/scenario_01_WI_TL.pdf) | Work instructions for TL quality type |
| | [`scenario_01_WI_SA.pdf`](figures/scenario_01_WI_SA.pdf) | Work instructions for SA quality type |

<br>

<!-- ================================================== -->
<!-- SYSTEM CONFIGURATION -->
<!-- ================================================== -->

## 2. System Configuration

### 2.1 Workstation Layout

Table 2.1 shows the physical configuration of the workstations within the system. B-Transfer serves as the final output buffer for finished components.

**Table 2.1.** Workstation layout and buffer configuration (Source: [`scenario_01_material_flow.svg`](figures/scenario_01_material_flow.svg))

| Workstation | Position | Buffer before | Buffer after | Equipment type |
|---------|----------|---------------|--------------|----------------|
| WS-03 | First | B-03 | B-04 | Automated |
| WS-04 | Middle | B-04 | B-05 | Automated |
| WS-05 | Last | B-05 | B-Transfer | Automated |

<br>

### 2.2 Workstation Distances

Table 2.2 shows the physical distances between workstations and key locations in the system. These distances are measured in meters and represent the shortest path between locations.

**Table 2.2.** Workstation distance matrix in meters (measured approximately)

|            | Goods-in | WS-03 | WS-04 | WS-05 | Warehouse |
|------------|----------|-------|-------|-------|-----------|
| Goods-in   | 0        | 3.2   | 5.4   | 7.8   | 5.2       |
| WS-03      | 3.2      | 0     | 2.5   | 5.0   | 2.0       |
| WS-04      | 5.4      | 2.5   | 0     | 2.5   | 2.0       |
| WS-05      | 7.8      | 5.0   | 2.5   | 0     | 2.0       |
| Warehouse  | 5.2      | 2.0   | 2.0   | 2.0   | 0         |

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
| SSA | Small shock absorbers | 2 | Recycle |
| CORE | Chassis with systems and engine (excluding rear axis) | 1 | Reuse |
| BSA | Big shock absorbers | 2 | Remanufacture |
| RAX (RD) | Rear axis | 1 | Repair |
| CRE (TL) | Chassis, remaining systems, engine | 1 | Recycle |
| CSEB-NABS (SA) | Chassis, systems, engine, body | 1 | Recycle |

<br>

<!-- ================================================== -->
<!-- DISASSEMBLY PROCESS -->
<!-- ================================================== -->

## 3. Disassembly Process

### 3.1 Quality-Based Routing

Table 3.1 illustrates the routing patterns for each quality type through the disassembly system. Each quality type has a specific route and targets different sets of components based on the product scenario.

**Table 3.1.** Quality-dependent routing and target components (Source: [`scenario_01_material_flow.svg`](figures/scenario_01_material_flow.svg))

| Quality type | Count | Material flow | Target components | Remaining |
|--------------|-------|-------|-------------------|-----------|
| **RD** (Rear damage) | 6 | WS-03→WS-04→WS-05 | BOSP, RT, CORE, BSA | RAX (RD) |
| **TL** (Total loss) | 2 | WS-03 only | BOSP, BAT, RT, FT | CRE (TL) |
| **SA** (Shock absorber) | 2 | WS-03→WS-05 | RT, FT, SSA, BSA | CSEB-NABS (SA) |

<br>

### 3.2 Process Step Mapping

Table 3.2 maps which disassembly steps are performed for each quality type. Step S5 is not relevant to this scenario.

**Table 3.2.** Process steps by quality type and workstation assignment (Source: [`scenario_01_material_flow.svg`](figures/scenario_01_material_flow.svg))

| Step | Operation | TL | RD | SA | Workstation |
|------|-----------|----|----|-------|---------|
| S1 | Remove body & spoiler | ✓ | ✓ | - | WS-03 |
| S2 | Remove battery | ✓ | - | - | WS-03 |
| S3 | Remove rear tires | ✓ | ✓ | ✓ | WS-03 |
| S4 | Remove front tires | ✓ | - | ✓ | WS-03 |
| S5 | Remove front axis with shock absorbers | - | - | - | N/A |
| S6 | Remove small shock absorbers | - | - | ✓ | WS-05 |
| S7 | Remove core (chassis/systems/engine) | - | ✓ | - | WS-04 |
| S8 | Remove big shock absorbers | - | ✓ | ✓ | WS-05 |

<br>

<!-- ================================================== -->
<!-- PRODUCTION SCHEDULE -->
<!-- ================================================== -->

## 4. Production Schedule

Table 4.1 shows the arrival schedule and processing status of all production orders. PO-07 had tracking issues (Section 6).

**Table 4.1.** Production order schedule and completion status (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheets "delivery_times" and "extraction")

| Order | Arrival time | Quality type | Material flow | Status |
|-------|--------------|--------------|------------------|--------|
| PO-01 | 09:26:00 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-02 | 09:28:00 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-03 | 09:30:00 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-04 | 09:32:00 | TL | WS-03 only | Complete |
| PO-05 | 09:35:00 | SA | WS-03→WS-05 | Complete |
| PO-06 | 09:36:00 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-07 | 09:38:00 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-08 | 09:40:30 | TL | WS-03 only | Complete |
| PO-09 | 09:44:30 | RD | WS-03→WS-04→WS-05 | Complete |
| PO-10 | 09:56:00 | SA | WS-03→WS-05 | Complete |

<br>

<!-- ================================================== -->
<!-- SCENARIO ANALYSIS -->
<!-- ================================================== -->

## 5. Scenario Analysis

> 📊 **Note on Data Presentation:** The tables and metrics in this section provide a concise summary. For detailed analysis, refer to the Excel analysis file ([`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx)). This file contains the complete dataset and calculations.


### 5.1 System-Level Indicators

Table 5.1 presents the overall system throughput performance. All production orders had a completion rate of 100%.

**Table 5.1.** System-level performance indicators (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>Value</th></tr>
<tr><td>Total processing time (minutes)</td><td>40.27</td></tr>
<tr><td>POs processed (#)</td><td>10</td></tr>
<tr><td>System throughput rate (POs/hour)</td><td>14.9</td></tr>
<tr><td>Total components planned (#)<sup>[1]</sup></td><td>40</td></tr>
<tr><td>Total components completed (#)<sup>[1]</sup></td><td>40</td></tr>
<tr><td>Overall completion rate (%)</td><td>100</td></tr>
</table>

Notes:

<sup>[1]</sup> Component counts based on target components defined in Table 3 of the [README.md](../../README.md). Components are counted by their codes (e.g., BOSP, RT, BSA) as defined in Table 2.3, where each code represents one component unit regardless of quantity.

<br>

Table 5.2 summarizes the total number of components of each type that were disassembled. The summary reflects the quality-dependent disassembly scenarios RD, TL, and SA.

**Table 5.2.** Component processing summary (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

| Code | Component | Quantity | Instances | Total components disassembled |
|------|-----------|----------|-----------|-------------------------------|
| BOSP | Body & spoiler | 1+1 | 8 | 16 |
| BAT | Battery | 1 | 2 | 2 |
| RT | Rear tires | 2 | 10 | 20 |
| FT | Front tires | 2 | 4 | 8 |
| SSA | Small shock absorbers | 2 | 2 | 4 |
| CORE | Chassis with systems and engine | 1 | 6 | 6 |
| BSA | Big shock absorbers | 2 | 8 | 16 |
| **Total** | **-** | **-** | **40** | **72** |

Note: Only target components shown. Intermediate assemblies (FAXS, CRAXS, CREW) and remaining components (RAX, CRE, CSEB-NABS) are excluded from this count.

<br>

### 5.2 Workstation Performance

Table 5.3 shows the utilization and workload distribution across workstations. The average utilization across all workstations is 55.7%.

**Table 5.3.** Workstation performance indicators (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

| Indicator | WS-03 | WS-04 | WS-05 |
|--------|-------|-------|-------|
| POs processed | 10/10 | 6/10 | 8/10 |
| Components disassembled | 24 | 6 | 10 |
| Total busy time (seconds) | 1,988 | 756 | 1,290 |
| Total busy time (minutes) | 33.1 | 12.6 | 21.5 |
| Utilization rate (%) | 82.3 | 31.3 | 53.4 |
| Quality types handled | RD, TL, SA | RD only | RD, SA |

<br>

### 5.3 Production Order Analysis

Table 5.4 shows the handling time, in seconds, for each component across all production orders. The handling time includes both the disassembly time and the waiting time at a workstation.

**Table 5.4.** Component handling times per production order (seconds) (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 78 | 31 | 90 | 135 | 76 | 30 | - | 60 | 88 | 88 | 60 | - |
| S2 | BAT | 120 | 42 | - | - | - | 150 | - | - | - | 90 | - | - |
| S3 | RT | 90 | 45 | 90 | 61 | 75 | 104 | 194 | 60 | 45 | 135 | 75 | 60 |
| S4 | FT | 86 | 25 | - | - | - | 118 | 60 | - | - | 90 | - | 75 |
| S6 | SSA | 120 | 21 | - | - | - | - | 135 | - | - | - | - | 105 |
| S7 | CORE | 129 | 85 | 299 | 105 | 105 | - | - | 105 | 102 | - | 60 | - |
| S8 | BSA | 148 | 55 | 150 | 181 | 104 | - | 166 | 255 | 148 | - | 90 | 90 |

<br><br>

Table 5.5 shows the actual disassembly time, in seconds, for each component across all production orders. Disassembly time represents only active processing duration (excludes waiting time).

**Table 5.5.** Component disassembly times per production order (seconds) (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

| Step | Component | Avg (s) | Std (s) | PO-01 | PO-02 | PO-03 | PO-04 | PO-05 | PO-06 | PO-07 | PO-08 | PO-09 | PO-10 |
|------|-----------|---------|---------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| S1 | BOSP | 43 | 23 | 60 | 91 | 30 | 15 | - | 30 | 43 | 43 | 31 | - |
| S2 | BAT | 75 | 43 | - | - | - | 105 | - | - | - | 44 | - | - |
| S3 | RT | 47 | 36 | 45 | 31 | 45 | 30 | 105 | 15 | 15 | 120 | 29 | 30 |
| S4 | FT | 43 | 23 | - | - | - | 75 | 23 | - | - | 45 | - | 30 |
| S6 | SSA | 75 | 21 | - | - | - | - | 90 | - | - | - | - | 60 |
| S7 | CORE | 77 | 68 | 209 | 76 | 76 | - | - | 30 | 27 | - | 45 | - |
| S8 | BSA | 98 | 32 | 105 | 135 | 89 | - | 90 | 150 | 98 | - | 60 | 60 |

<br><br>

Table 5.6 summarizes the performance indicators for each production order. All orders were completed at a 100% rate.

**Table 5.6.** Production order performance indicators (Source: [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx), sheet "analysis")

<table>
<tr><th>Indicator</th><th>PO-01</th><th>PO-02</th><th>PO-03</th><th>PO-04</th><th>PO-05</th><th>PO-06</th><th>PO-07</th><th>PO-08</th><th>PO-09</th><th>PO-10</th></tr>
<tr><td>Handling time (seconds)<sup>[1]</sup></td><td>629</td><td>482</td><td>360</td><td>402</td><td>555</td><td>480</td><td>383</td><td>403</td><td>285</td><td>330</td></tr>
<tr><td>Disassembly time (seconds)<sup>[2]</sup></td><td>419</td><td>333</td><td>240</td><td>225</td><td>308</td><td>225</td><td>183</td><td>252</td><td>165</td><td>180</td></tr>
<tr><td>Waiting time (seconds)<sup>[3]</sup></td><td>46</td><td>151</td><td>347</td><td>331</td><td>452</td><td>736</td><td>1,066</td><td>603</td><td>706</td><td>211</td></tr>
<tr><td>Lead time (seconds)<sup>[4]</sup></td><td>586</td><td>721</td><td>721</td><td>530</td><td>976</td><td>1,231</td><td>941</td><td>931</td><td>1,082</td><td>616</td></tr>
<tr><td>Components planned (#)</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td></tr>
<tr><td>Components completed (#)</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td><td>4</td></tr>
<tr><td>Completion rate (%)</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td></tr>
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

Table 6.1 summarizes the data processing pipeline and event counts. A signal-to-noise ratio of 48% was achieved after filtering. For additional details, see the [`scenario_01_data_analyzed.xlsx`](data/scenario_01_data_analyzed.xlsx) file, specifically the "pre-process", "extraction", and "process_calculation" sheets.

**Table 6.1.** Data quality statistics showing processing stages

| Stage | Event count | Description |
|-------|-------------|-------------|
| **Raw events** | 477 | Original recorded events from IT system |
| **Preprocessed** | 487 | +10 events added during preprocessing |
| **Clean events** | 236 | Final usable events after cleaning |
| - OK (from raw) | 140 | Events validated from raw data (includes sequence errors) |
| - Cleaned | 35 | Manually corrected events |
| - Calculated | 24 | Estimated from averages |
| - Start | 10 | Manually added start events |
| **Filtered noise** | 251 | Events removed as noise (52%) |
| **Signal-to-noise ratio** | 48% | Percentage of usable data |