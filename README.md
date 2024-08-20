# Water-Station-Data-Visualization
This project simulates data generation and aggregation for water stations, including pump operation, maintenance activities, customer complaints, and leakage events. The data is processed into dimension and fact tables to support analytics on water station operations.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Generated Data](#generated-data)

## Introduction

This project uses Python to generate and organize water station operation data. The tools and libraries utilized include:
- **Pandas**: For data manipulation and creation of dimension and fact tables.
- **Numpy**: For numerical computations in generating random data.
- **Datetime**: For handling date and time objects.
- **Random**: For generating random values used in simulations.

The project generates data across several domains:
- **Pump Operations**: Tracking pump statuses such as 'power on', 'standby', and 'maintenance'.
- **Maintenance**: Simulating monthly maintenance activities for each water station, including equipment usage.
- **Customer Complaints**: Recording water-related complaints from customers.
- **Leakages**: Capturing water leakage events with resolution times and water wasted.

## Installation

To use this project, you'll need the following dependencies installed:

1. Python 3.x
2. Pandas: `pip install pandas`
3. Numpy: `pip install numpy`
4. Datetime (built-in)
5. Random (built-in)

You can install the dependencies using the following command:
```bash
pip install pandas numpy
```

## Generated Data

The following data is generated in CSV format:

1. **Pump Dimension Table (`pump_dim.csv`)**:  
   Contains details on pump operations such as `pump_ID`, `station_id`, `pump_status`, `power_consumption`, and more.

2. **Water Station Dimension Table (`station_dim.csv`)**:  
   Includes water station metadata like `water_station_id`, `Water_station_name`, `lat`, `lan`, and `Number_of_pumps`.

3. **Maintenance Dimension Table (`maintenance_dim.csv`)**:  
   Records maintenance activities, including `maintenance_id`, `employee_id`, `equipment_name`, and `cost_per_hour`.

4. **Customer Complaints Dimension Table (`customer_dim.csv`)**:  
   Captures customer complaints with fields like `complaint_id`, `complaint_type`, `complaint_resolution_time`, etc.

5. **Leakage Dimension Table (`leakage_dim.csv`)**:  
   Contains leakage events with `leakage_id`, `leakage_lat`, `leakage_lan`, `leakage_water_wasted`, and more.

6. **Fact Table (`fact_table.csv`)**:  
   A consolidated table with aggregated metrics such as total operating pumps, total maintenance pumps, water input/output flows, tank levels, and references to complaint, maintenance, and leakage events.

