# Renewable Energy Community Data Aggregator

Managing energy within a Renewable Energy Community (CER) requires tracking production and consumption differently than for the national grid. Energy used internally and energy exchanged with the main network have distinct incentives, making accurate data aggregation essential for analysis and reporting.

This project provides a Python script to process monthly CER data downloaded from the e-distribuzione portal, aggregating it into hourly intervals independent of individual producers or consumers.

# Workflow

Data is manually downloaded month by month for each participant (no API avilable yet). In the first version of the code, the one named "Old_", the files werre organized into two separate folders: "immessa" for energy fed into the grid and "prelevata" for energy consumed from the grid, with each file named according to the month and name of the producer plus "i" for "immessa" or "p" for "prelevata (e.g., i_gennaio_rossi.csv). Before processing, the monthly files are compressed into a ZIP file for each folder. The script processes one ZIP at a time, reading all included files and producing a single aggregated output with hourly intervals, regardless of the original producer or consumer.

To run the script, simply specify the ZIP file to process and the desired output file name. The result is a clean CSV containing the aggregated hourly data, ready for analysis or further reporting. 

While this worked, I was asked some further elaboration also showing single plant data instead of only showing the aggregates.

In the newer version of the code, divided in three scripts, I again have two folders, "Immessa" and "Prelevata", each containing a folder for each solar plant. In the first script I generate the dataframes, aggregate data from 15 min intervals to 1 hour intervals, concatenating by months to get a singe file for each plant. 

In the second script I calculate daily energy and generate two plots (one for "Immessa" and the other for "Prelevata") showing how energy changes over time.

In the third sript I first plot daily energy of "Immessa" and "Prelevata", then I compare the two df, confrontign energy data pairwise (same day, same hour), selecting the minimum. This will generate a df containign the hourly minimum between "Immessa" and "Prelevata", and it's what we need to calculate the incentive the CER will receive.


