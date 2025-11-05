# DisAssembly Scenario Learning Factory Dataset (DASCEN-LF)

![Version](https://img.shields.io/badge/version-2025.10-blue)
![Status](https://img.shields.io/badge/status-research%20dataset-orange)

This repository contains a dataset from a learning factory, which was collected using the flexible disassembly demonstrator developed by [Jordan et al. (2025)](#jordan-et-al-2025).

> 📊 **Dataset Overview**
> - 6 scenarios | 60 production orders (toy cars) | 390 components tracked
> - 3 to 5 workstations | Line & Workshop layouts | Manual & Automated processing
> - 4 quality types (HD, TL, SA, RD) with variable disassembly depths (4-8 target components per quality)
> - 18 unique component types tracked (9 target, 5 intermediate, 4 remaining)

## Table of Contents
- [Contact](#contact)
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Dataset Details](#dataset-details)
- [Cross-Scenario Data Analysis](#cross-scenario-data-analysis)
- [Citation](#citation)
- [License](#license)
- [References](#references)


## Contact
### Contact Details
Corresponding author: Patrick Jordan, patrick.jordan@iwb.tum.de


### Useful Links
- **[Visit our other repositories](https://iwb.github.io)**  
Explore more tools and resources from our research institute.

- **[Visit our institute for more information](https://www.mec.ed.tum.de/en/iwb/homepage/)**  
Learn more about our research and ongoing projects.

<!-- ================================================== -->
<!-- INTRODUCTION SECTION -->
<!-- ================================================== -->
## Introduction
This repository contains a dataset from six disassembly runs carried out in January 2025 at the Smart Production Lab (SPL) at the Institute for Machine Tools and Industrial Management (*iwb*) at the Technical University of Munich (https://iwb-spl.de/). The dataset provides the complete disassembly process data for 60 remotely controlled electric toy cars (RC cars). 

A disassembly scenario combines two elements: a **system design scenario** (layout and workstation configuration) and a **product scenario** (incoming products and disassembly depths). Since these decisions are interdependent, multiple scenario combinations are possible. Comparing these scenarios is necessary to determine the economically and ecologically appropriate disassembly approach
[(Jordan et al. 2024)](#jordan-et-al-2024) The six scenarios presented in this repository include system designs with three to five workstations, one to four product types per product portfolio, and various layouts. This provides diverse material flow data. The dataset for each scenario is divided into two types: gathered raw event data and pre-processed data, including an initial analysis of the performance of each disassembly scenario.

### Research Context
The data was collected in the **Smart Production Lab (SPL)** at the Institute for Machine Tools and Industrial Management (iwb), Technical University of Munich. The SPL is a learning factory for lean, digital, automated, and circular manufacturing. It offers various disassembly system designs that represent different scenarios, building upon the infrastructure described in [Jordan et al. (2025)](#jordan-et-al-2025). As outlined in [Jordan et al. (2025)](#jordan-et-al-2025), the demonstrator facilitates the comparison of real-world data with synthetic simulation data. This enables the validation of disasembly simulation models while simultaneously exploring different disassembly system designs and the impact of the disassembly depth on the system performance. Beyond the proposed use for the validation of flexible disassembly simulation models, the data could be used for various purposes, such as comparing different layouts, benchmarking process mining techniques, and analyzing resource allocation policies in diverging material flows.

### Related Research Work
The dataset is an extension of the initial testing phase of the demonstrator, as described in the following article:

**"Demonstrator-based implementation of an infrastructure for event data acquisition in disassembly material flows"**  
*Patrick Jordan, Lasse Streibel, Niklas Lindholm, Wesal Maroof, Susanne Vernim, Laura Goebel, Michael F. Zaeh*<br/> 
Proceedings of the 58th CIRP Conference on Manufacturing Systems 2025

[For more details, see the published article (Link)](https://doi.org/10.1016/j.procir.2025.03.040) 

### Experimental Design
A disassembly graph containing over 60 components was used to design four quality levels for the cars: Hail Damage (HD), Rear Damage (RD), Total Loss (TL), and Shock Absorber defects (SA). For each quality level, disassembly sequences were defined based on the graph structure. These sequences were subsequently translated into quality- and scenario-specific work instructions, which provided operators with a step-by-step disassembly plan and routing information for each production order.

Each disassembly scenario was executed for approximately 40 minutes with one operator per workstation. Each operator managed the material flow between workstations based on the information provided in the work instructions. An additional operator removed the final disassembled components from the shop floor. The logistics data after the last disassembly step cannot be used because components were randomly removed from the final buffer location (B-Transfer), making the timing data unreliable. From the solution elements of the demonstrator ([Jordan et al. 2025](#jordan-et-al-2025)), the assignment app was used to ensure that each incoming production order was linked to a single tracking device. During the disassembly process, the inheritance app was used to ensure that each component was linked correctly to the original production order. The collision zones were used for the automatic timestamp capture (event data), and the central database was used for recording that event data. Instead of utilizing the work instructions app, manual work instructions were provided to manage the material flow. For more information about the demonstrator, please refer to [Jordan et al. (2025)](#jordan-et-al-2025).


### Data Quality Considerations
⚠️ **Known Limitations:**
- The signal-to-noise ratio varies due to the system's location-based tracking, which creates duplicates in timestamps. For example, a product may enter and exit a workstation multiple times if it is too close to the edge of the virtual collision zone. For more detailed information about the collision zones, please refer to [Jordan et al. (2025)](#jordan-et-al-2025).
- It has been observed that operators have, on occasion, deviated from the work instructions. For instance, operators disassembled multiple components simultaneously, not sequentially, as defined.
- Sometimes, timestamps had to be calculated from averages when events were not properly captured.
- Due to the aforementioned limitations, extensive manual data cleaning was necessary. This process may have introduced errors, such as selecting incorrect timestamps for certain activities.



<!-- ================================================== -->
<!-- DATASET SECTION -->
<!-- ================================================== -->
## Dataset

### Dataset Overview
> **⚠️ Experimental Design Note:** The experimental design prioritized operational diversity over performance optimization in the disassembly scenarios. The unbalanced workstation assignments and varied material flows are intentional. The objective of this work was to create diverse disassembly data, enabling the analysis of different system behaviors and to validate the simulation framework.

<!-- ================================================== -->
<!-- DATASET DETAILS SECTION -->
<!-- ================================================== -->
The detailed documentation, data, and analysis for each disassembly scenario can be found in the respective folders:

<ins>Scenario 1: Line Layout - Mixed Portfolio</ins>
- System configuration: 3 workstations, line layout, automated processing
- Product portfolio: RD (60%), TL (20%), SA (20%)
- Documentation: [`scenario_01_documentation.md`](scenarios/01_line_3ws_auto_mix/scenario_01_documentation.md)

<ins>Scenario 2: Workshop Layout - HD Portfolio</ins>
- System configuration: 4 workstations, workshop layout, manual processing
- Product portfolio: HD (100%)
- Documentation: [`scenario_02_documentation.md`](scenarios/02_wshop_4ws_man_HD/scenario_02_documentation.md)

<ins>Scenario 3: Line Layout - HD Portfolio</ins>
- System configuration: 5 workstations, line layout, automated processing
- Product portfolio: HD (100%)
- Documentation: [`scenario_03_documentation.md`](scenarios/03_line_5ws_auto_HD/scenario_03_documentation.md)

<ins>Scenario 4: Workshop Layout - HD Portfolio</ins>
- System configuration: 5 workstations, workshop layout, manual processing
- Product portfolio: HD (100%)
- Documentation: [`scenario_04_documentation.md`](scenarios/04_wshop_5ws_man_HD/scenario_04_documentation.md)

<ins>Scenario 5: Workshop Layout - Mixed Portfolio</ins>
- System configuration: 5 workstations, workshop layout, automated processing
- Product portfolio: HD (70%), TL (10%), SA (10%), RD (10%)
- Documentation: [`scenario_05_documentation.md`](scenarios/05_wshop_5ws_auto_mix/scenario_05_documentation.md)

<ins>Scenario 6: Line Layout - Mixed Portfolio</ins>
- System configuration: 5 workstations, line layout, manual processing
- Product portfolio: HD (30%), SA (30%), RD (30%), TL (10%)
- Documentation: [`scenario_06_documentation.md`](scenarios/06_line_5ws_man_mix/scenario_06_documentation.md)


<br>


### File Organization
Each scenario contains:
- **Raw CSV data:** Original tracking data with all noise and intermediate events
- **Excel analysis file:** Processed data with validation columns, extracted sequences, and analysis
- **Material flow diagrams:** Visual representation of the material flow and system layout (not to scale)
- **Disassembly sequences:** Visual representation of the disassembly process for each quality type
- **Work instructions (WI):** Quality-specific work instructions including production order information, delivery times, and step-by-step disassembly procedures. Note that each scenario has 10 production orders, but work instructions are grouped by quality type (e.g., scenario 1 has 10 POs but only 3 WI files for RD, TL, and SA quality types)


#### Raw Data - CSV Data Fields

Table 1 provides an overview of the structure of the raw CSV data fields utilized for the tracking events, along with the translation of the original German column names. The raw data files contain tracking events with timestamps, locations, and component identifiers.

**Table 1.** CSV data field structure

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| `fauf` | String | Production Order ID | PO-01 |
| `materialnummer` | String | Component identifier | Car-01, BOSP |
| `menge` | Integer | Quantity | 1 |
| `arbeitsstation` | String | Workstation/location | WS-01, B-Transfer |
| `eventtyp` | String | Event type | Generation, Entry, Exit |
| `zustand` | String | Quality condition | Standard, HD |
| `zeitstempel` | Timestamp | ISO timestamp | 2025-01-03 08:56:00.719+01 |
| `tag_id` | String | Identifier of UWB Tag| 84b31b00000b807d |

<br>


#### Excel Analysis Structure

Table 2 lists the eight standardized sheets included in each Excel analysis file. Each sheet serves a specific purpose in the data processing and analysis pipeline, from raw event logs to final performance indicators.

**Table 2.** Excel sheet structure and purpose

| Sheet | Description | Purpose |
|-------|-------------|---------|
| `raw_data` | Original tracking events | Unprocessed event log |
| `delivery_times` | Manual arrival records | Start time documentation |
| `preprocess` | Data validation and cleaning | Event filtering with OK/SKIP flags |
| `extraction` | Clean event sequences by PO | Final material flow per order |
| `workstation_timeline` | Workstation-based event ordering | Utilization analysis |
| `process_calculation` | Time indicators and KPIs | Performance calculations |
| `analysis` | Configuration and performance summary | Final indicators and KPIs |
| `timestamp_calculation` | Missing value estimation | Gap filling using averages |

<br>


### Component Dictionary

Table 3 lists all component codes and descriptions, which are standardized across all scenarios. For detailed information about the components and the material flows, please refer to the sequence files of the respective scenario.

<table>
  <caption style="text-align: left;"><strong>Table 3.</strong> Component codes and descriptions</caption>
  <thead>
    <tr>
      <th>Code</th>
      <th>Component</th>
      <th>Quantity</th>
      <th>Weight (g)<sup>[1]</sup></th>
      <th>Value (Euro)<sup>[2]</sup></th>
      <th>Destination</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Car</td><td>-</td><td>1</td><td>1360</td><td>230</td><td>-</td><td>-</td></tr>
    <tr><td colspan="7"><strong>Target Components</strong></td></tr>
    <tr><td>BOSP</td><td>Body & spoiler</td><td>1+1</td><td>77</td><td>44</td><td>Recycle</td><td>-</td></tr>
    <tr><td>BAT</td><td>Battery</td><td>1</td><td>396</td><td>42</td><td>Reuse</td><td>-</td></tr>
    <tr><td>RT</td><td>Rear tires</td><td>2</td><td>142</td><td>26</td><td>Recycle/Reuse</td><td>-</td></tr>
    <tr><td>FT</td><td>Front tires</td><td>2</td><td>97</td><td>24</td><td>Reuse</td><td>-</td></tr>
    <tr><td>FAXS</td><td>Front axis with shock absorbers</td><td>1</td><td>155</td><td>50</td><td>None (intermediate assembly)</td><td>Consists of front axis, SSA<sup>[3]</sup></td></tr>
    <tr><td>SSA</td><td>Small shock absorbers</td><td>2</td><td>15</td><td>21</td><td>Recycle</td><td>Consists of: damper spring, damper housing, damper housing cap</td></tr>
    <tr><td>FAX</td><td>Front axis</td><td>1</td><td>140</td><td>30</td><td>Remanufacture</td><td>-</td></tr>
    <tr><td>CHS</td><td>Chassis</td><td>1</td><td>414</td><td>56</td><td>Reuse</td><td>Consists of chassis and power steering; only HD<sup>[4]</sup></td></tr>
    <tr><td>CORE</td><td>Chassis with systems and engine (excluding rear axis)</td><td>1</td><td>600</td><td>110</td><td>Reuse</td><td>only RD<sup>[4]</sup></td></tr>
    <tr><td>BSA</td><td>Big shock absorbers</td><td>2</td><td>15</td><td>21</td><td>Remanufacture</td><td>Consists of: damper spring, damper housing, damper housing cap</td></tr>
    <tr><td colspan="7"><strong>Intermediate assemblies<sup>[5]</sup></strong></td></tr>
    <tr><td>CRAXS</td><td>Chassis with rear axis and shock absorbers</td><td>1</td><td>950</td><td>-</td><td>None (intermediate assembly)</td><td>only HD</td></tr>
    <tr><td>CREW</td><td>Chassis, remaining systems, engine, and wheels</td><td>1</td><td>887</td><td>-</td><td>None (intermediate assembly)</td><td>only TL</td></tr>
    <tr><td>RAXS</td><td>Rear axis with motor and big shock absorbers</td><td>1</td><td>540</td><td>-</td><td>None (intermediate assembly)</td><td>only HD, RD</td></tr>
    <tr><td>CSEWF</td><td>Chassis with systems, engine, and front wheels</td><td>1</td><td>1140</td><td>-</td><td>None (intermediate assembly)</td><td>only RD</td></tr>
    <tr><td colspan="7"><strong>Remaining Parts<sup>[6]</sup></strong></td></tr>
    <tr><td>RAX (HD)</td><td>Rear axis</td><td>1</td><td>500</td><td>50</td><td>Recycle</td><td>Consists of rear axis, engine, gear cover, gears; only HD</td></tr>
    <tr><td>RAX (RD)</td><td>Rear axis</td><td>1</td><td>500</td><td>50</td><td>Repair</td><td>Consists of rear axis, engine, gear cover, gears; only RD</td></tr>
    <tr><td>CRE (TL)</td><td>Chassis, remaining systems, engine</td><td>1</td><td>648</td><td>94</td><td>Recycle</td><td>only TL</td></tr>
    <tr><td>CSEB-NABS (SA)</td><td>Chassis, systems, engine, body</td><td>1</td><td>1090</td><td>138</td><td>Recycle</td><td>only SA</td></tr>
  </tbody>
</table>

Notes:

<sup>[1]</sup> Component weights are based on manual weighing. 

<sup>[2]</sup> Component values are estimated based on the new value. For assemblies, the approximate sum of the components contained within is used.

<sup>[3]</sup> FAXS is disassembled into FAX and SSA. In some cases (e.g., scenario 2), timestamps for this split were gathered manually by the operator.

<sup>[4]</sup> CHS and CORE represent physically distinct assemblies corresponding to different quality types (HD and RD, respectively). However, the disassembly tasks performed on both components are identical. Process times are therefore reported as CHS/CORE.

<sup>[5]</sup> These assemblies represent temporary intermediate states during disassembly. They are not tracked as separate entities in the dataset.

<sup>[6]</sup> Remaining parts represent assemblies that retain the tracking tag from the original car and are not fully disassembled.

<br>


### Disassembly Strategies

Table 4 summarizes the four quality-dependent disassembly strategies. Different disassembly strategies were implemented based on simulated quality conditions, resulting in varying disassembly depths and component recovery patterns.

**Table 4.** Quality-dependent disassembly strategies

| Code | Quality type | Strategy | Target Components | Count | Remaining Assembly | Recorded as `zustand` |
|:----:|--------------|----------|-------------------|:-----:|--------------------|------------|
| **HD** | Hail Damage | Maximum disassembly | BOSP, BAT, RT, FT, SSA, FAX, CHS, BSA | 8 | RAX (HD) | Standard |
| **RD** | Rear Damage | Rear axis repair | BOSP, RT, CORE, BSA | 4 | RAX (RD) | Unfallfahrzeug mit Heckschaden |
| **TL** | Total Loss | Material recovery | BOSP, BAT, RT, FT | 4 | CRE (TL) | Totalschaden |
| **SA** | Shock Absorber | Part recall | RT, FT, SSA, BSA | 4 | CSEB-NABS (SA) | Produktionsfehler an Stoßdaempfern |




<!-- ================================================== -->
<!-- CROSS-SCENARIO PROCESS ANALYSIS SECTION -->
<!-- ================================================== -->
## Cross-Scenario Data Analysis

This section presents the aggregated disassembly time statistics across all six scenarios. The analysis distinguishes between manual and automated tools.

### Process Step Times

Tables 5 and 6 present the average handling and disassembly times per process step across all scenarios. **Handling time** (Table 5) includes both disassembly time (component removal) and movement time (transport to next buffer). It represents the total time from when a component enters a workstation until it exits. As outlined in Table 6, the **disassembly time** does not include the operator's moving time. It represents solely the duration during which the worker actively processes the component. Both raw and cleaned values are provided. Outliers were removed using the interquartile range (IQR) method to support the reproducibility of the results. Please note that due to the inconsistent quality of incoming products, there may be significant variations in disassembly times. In some cases, the disassembly of components proved challenging, often due to the presence of worn screws. This is an example of the unpredictable behavior that can occur in disassembly systems. **Manual work** was carried out by hand, while **automated work** was carried out using a cordless screwdriver.


<table>
  <caption style="text-align: left;"><strong>Table 5.</strong> Average handling times per process step (in seconds)</caption>
  <thead>
    <tr>
      <th rowspan="2">Step</th>
      <th rowspan="2">Operation</th>
      <th rowspan="2">Tool</th>
      <th colspan="6">Statistics</th>
    </tr>
    <tr>
      <th>N</th>
      <th>Mean</th>
      <th>Std</th>
      <th>Mean (clean)</th>
      <th>Std (clean)</th>
      <th>Outliers</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>S1</td><td>BOSP</td><td>Man</td><td>56</td><td>93</td><td>43</td><td>90</td><td>37</td><td>1</td></tr>
    <tr><td>S2</td><td>BAT</td><td>Man</td><td>43</td><td>81</td><td>32</td><td>81</td><td>32</td><td>0</td></tr>
    <tr><td rowspan="2">S3</td><td rowspan="2">RT</td><td>Man</td><td>37</td><td>118</td><td>63</td><td>105</td><td>33</td><td>3</td></tr>
    <tr><td>Auto</td><td>20</td><td>103</td><td>58</td><td>103</td><td>58</td><td>0</td></tr>
    <tr><td rowspan="2">S4</td><td rowspan="2">FT</td><td>Man</td><td>31</td><td>126</td><td>60</td><td>120</td><td>50</td><td>1</td></tr>
    <tr><td>Auto</td><td>14</td><td>75</td><td>30</td><td>75</td><td>30</td><td>0</td></tr>
    <tr><td rowspan="2">S5</td><td rowspan="2">FAXS</td><td>Man</td><td>18</td><td>197</td><td>62</td><td>197</td><td>62</td><td>0</td></tr>
    <tr><td>Auto</td><td>16</td><td>163</td><td>108</td><td>127</td><td>43</td><td>2</td></tr>
    <tr><td rowspan="2">S6</td><td rowspan="2">SSA</td><td>Man</td><td>21</td><td>182</td><td>96</td><td>157</td><td>59</td><td>2</td></tr>
    <tr><td>Auto</td><td>18</td><td>121</td><td>25</td><td>121</td><td>25</td><td>0</td></tr>
    <tr><td rowspan="2">S7</td><td rowspan="2">CHS/CORE</td><td>Man</td><td>20</td><td>159</td><td>57</td><td>159</td><td>57</td><td>0</td></tr>
    <tr><td>Auto</td><td>24</td><td>147</td><td>65</td><td>121</td><td>29</td><td>4</td></tr>
    <tr><td rowspan="2">S8</td><td rowspan="2">BSA</td><td>Man</td><td>21</td><td>147</td><td>48</td><td>147</td><td>48</td><td>0</td></tr>
    <tr><td>Auto</td><td>22</td><td>125</td><td>51</td><td>125</td><td>51</td><td>0</td></tr>
  </tbody>
</table>

<br>

<!-- Table 6: Average disassembly times per process step (in seconds) --> 
<table>
  <caption style="text-align: left;"><strong>Table 6.</strong> Average disassembly times per process step (in seconds)</caption>
  <thead>
    <tr>
      <th rowspan="2">Step</th>
      <th rowspan="2">Operation</th>
      <th rowspan="2">Tool</th>
      <th colspan="6">Statistics</th>
    </tr>
    <tr>
      <th>N</th>
      <th>Mean</th>
      <th>Std</th>
      <th>Mean (clean)</th>
      <th>Std (clean)</th>
      <th>Outliers</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>S1</td><td>BOSP</td><td>Man</td><td>56</td><td>58</td><td>39</td><td>53</td><td>29</td><td>2</td></tr>
    <tr><td>S2</td><td>BAT</td><td>Man</td><td>43</td><td>44</td><td>25</td><td>42</td><td>23</td><td>1</td></tr>
    <tr><td rowspan="2">S3</td><td rowspan="2">RT</td><td>Man</td><td>37</td><td>79</td><td>63</td><td>67</td><td>31</td><td>2</td></tr>
    <tr><td>Auto</td><td>20</td><td>59</td><td>46</td><td>59</td><td>46</td><td>0</td></tr>
    <tr><td rowspan="2">S4</td><td rowspan="2">FT</td><td>Man</td><td>31</td><td>81</td><td>59</td><td>75</td><td>48</td><td>1</td></tr>
    <tr><td>Auto</td><td>14</td><td>36</td><td>19</td><td>36</td><td>19</td><td>0</td></tr>
    <tr><td rowspan="2">S5</td><td rowspan="2">FAXS</td><td>Man</td><td>18</td><td>149</td><td>52</td><td>141</td><td>41</td><td>1</td></tr>
    <tr><td>Auto</td><td>16</td><td>97</td><td>45</td><td>97</td><td>45</td><td>0</td></tr>
    <tr><td rowspan="2">S6</td><td rowspan="2">SSA</td><td>Man</td><td>21</td><td>142</td><td>67</td><td>131</td><td>46</td><td>1</td></tr>
    <tr><td>Auto</td><td>18</td><td>83</td><td>33</td><td>83</td><td>33</td><td>0</td></tr>
    <tr><td rowspan="2">S7</td><td rowspan="2">CHS/CORE</td><td>Man</td><td>20</td><td>125</td><td>52</td><td>125</td><td>52</td><td>0</td></tr>
    <tr><td>Auto</td><td>24</td><td>96</td><td>56</td><td>78</td><td>31</td><td>3</td></tr>
    <tr><td rowspan="2">S8</td><td rowspan="2">BSA</td><td>Man</td><td>21</td><td>106</td><td>48</td><td>99</td><td>38</td><td>1</td></tr>
    <tr><td>Auto</td><td>22</td><td>83</td><td>41</td><td>83</td><td>41</td><td>0</td></tr>
  </tbody>
</table>


**Notes for Tables 5 and 6:**
- **Handling time** (Table 5) = Disassembly time + movement time at workstation
- **Disassembly time** (Table 6) = Active processing time only, excludes movement to buffer
- **N**: Total number of observations across all scenarios
- **Mean/Std**: Original values including all data points
- **Mean (Clean)/Std (clean)**: Values after outlier removal using IQR method (Q1 - 1.5×IQR, Q3 + 1.5×IQR)
- **Outliers**: Number of observations removed during cleaning
- **Tool types**: Man = Manual tools, Auto = Cordless screwdrivers

For more details about the analysis, see [`disassembly_and_handling_times_all_scenarios.xlsx`](data/disassembly_and_handling_times_all_scenarios.xlsx)
<br>



<!-- ================================================== -->
<!-- CITATION SECTION -->
<!-- ================================================== -->
## Citation
If you use this repository for your research or industry projects, please cite the following article:

```bibtex
@article{JORDAN2025277,
title = {Demonstrator-based implementation of an infrastructure for event data acquisition in disassembly material flows},
journal = {Procedia CIRP},
volume = {134},
pages = {277-282},
year = {2025},
note = {58th CIRP Conference on Manufacturing Systems 2025},
issn = {2212-8271},
doi = {https://doi.org/10.1016/j.procir.2025.03.040},
url = {https://www.sciencedirect.com/science/article/pii/S2212827125004810},
author = {Patrick Jordan and Lasse Streibel and Niklas Lindholm and Wesal Maroof and Susanne Vernim and Laura Goebel and Michael F. Zaeh},
}
```


## License
This repository and its contents are licensed under the [MIT License](./LICENSE).

### Acknowledgements
This research was conducted at the Institute for Machine Tools and Industrial Management (*iwb*) at the Technical University of Munich. This research was funded by the Federal Ministry of Economic Affairs and Energy (BMWE) as part of the "Car2Car – Kreislauffahige, nachhaltige Fahrzeugverwertungskonzepte" project (19S22007H). The corresponding author wants to thank the more than 25 scientific colleagues from the *iwb* who participated in the disassembly runs in January 2025. Additionally, the author would like to express his gratitude to Patrick Schwartz for his assistance in the creation of the material flow diagrams.

## References

#### Jordan et al. 2024
Jordan, P., Kroeger, S., Streibel, L., Vernim, S., Zaeh, M.F. (2024). Concept for a data-based approach to support decision-making in tactical tasks for planning disassembly systems. Procedia CIRP, 122, 288–293. https://doi.org/10.1016/j.procir.2024.01.042


#### Jordan et al. 2025
Jordan, P., Streibel, L., Lindholm, N., Maroof, W., Vernim, S., Goebel, L., Zaeh, M.F. (2025). Demonstrator-based implementation of an infrastructure for event data acquisition in disassembly material flows. Procedia CIRP, 134, 277–282. https://doi.org/10.1016/j.procir.2025.03.040

---
For questions, suggestions, or collaboration opportunities, please contact the corresponding author or visit our [institute website](https://www.mec.ed.tum.de/en/iwb/homepage/).
