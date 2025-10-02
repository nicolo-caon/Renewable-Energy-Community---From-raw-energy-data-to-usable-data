# Renewable Energy Community Data Aggregator

Managing energy within a Renewable Energy Community (REC) requires tracking production and consumption differently than for the national grid. Energy used internally and energy exchanged with the main network have distinct incentives, making accurate data aggregation essential for analysis and reporting.

This project provides a Python script to process monthly REC data downloaded from the e-distribuzione portal, aggregating it into hourly intervals independent of individual producers or consumers.

# Workflow

Data is manually downloaded month by month for each participant. Once downloaded, the files are organized into two separate folders: immessa for energy fed into the grid and prelevata for energy consumed from the grid, with each file named according to the month (e.g., January.xlsx). Before processing, the monthly files are compressed into a ZIP file for each folder. The script processes one ZIP at a time, reading all included files and producing a single aggregated output with hourly intervals, regardless of the original producer or consumer.

To run the script, simply specify the ZIP file to process and the desired output file name. The result is a clean CSV containing the aggregated hourly data, ready for analysis or further reporting.

# Features

The script handles both immessa and prelevata data, converts 15-minute interval readings into hourly aggregates, and produces a single dataset combining all participants in the folder. It is designed to work with manually downloaded data, requiring no API.
