# Section 1
### - 1.1 - Review the column that you are looking to change
- SELECT Accel FROM evCars

### - 1.2 - Selecting the correct string function
- SELECT RTRIM(Accel, ' sec')
FROM evCars;

### - 1.3 - Visualizing the changes before making them
- SELECT Accel, RTRIM(Accel, ' sec')
FROM evCars;

### - 1.4 UPDATE the records
- UPDATE evCars
SET Accel = RTRIM(Accel, ' sec'); 

### - 1.5 Check your work
- SELECT Accel 
FROM evCars;

### - 1.6 Rename the column
- ALTER TABLE evCars
RENAME Accel TO AccelSec;

# Section 2
### - 2.1 Review the column that you are looking to change 
- SELECT TopSpeed
FROM evCars;

### - 2.2 Selecting the correct String Function
- SELECT RTRIM(TopSpeed, ' km/h')
FROM evCars;

### - 2.3 Visualizing the Changes before making them 
- SELECT TopSpeed, RTRIM(TopSpeed, ' km/h')
FROM evCars;

### - 2.4 UPDATE the records
- UPDATE evCars
SET TopSpeed = RTRIM(TopSpeed, ' km/h');

### - 2.5 Check your work 
- SELECT TopSpeed 
FROM evCars;

### - 2.6 Convert the units to MPH
- SELECT TopSpeed, ROUND((TopSpeed * 0.621371), 1) as TopSpeedMPH
FROM evCars;

- UPDATE evCars
SET TopSpeed = ROUND((TopSpeed * 0.621371), 1);

- SELECT TopSpeed
FROM evCars;

### - 2.7 Rename the column
- ALTER TABLE evCars
RENAME TopSpeed TO TopSpeedMPH;

### - 2.8  Select All of the records to get a look at the whole table with your recent changes.
- SELECT *
FROM evCars;

# Section 3 
### - 3.1 Review the column that you are looking to change 
- SELECT Range
FROM evCars;

### - 3.2 Selecting the correct String Function
- SELECT RTRIM(Range, ' km')
FROM evCars;

### - 3.3 Visualizing the Changes before making them
- SELECT Range, RTRIM(Range, ' km')
FROM evCars;

### - 3.4 UPDATE the records
- UPDATE evCars
SET Range = RTRIM(Range, ' km');

### - 3.5 Check your work 
- SELECT Range
FROM evCars;

### - 3.6 Convert the units to MPH
- SELECT Range, ROUND((Range * 0.621371), 1) as RangeMiles
FROM evCars;

- UPDATE evCars
SET Range = ROUND((Range * 0.621371), 1);

- SELECT Range
FROM evCars;

### - 3.7 Rename the column
- ALTER TABLE evCars
RENAME Range TO RangeMiles;

### - 3.8  Select All of the records to get a look at the whole table with your recent changes. 
- SELECT *
FROM evCars;

# SECTION 4 
### - 4.1 Write a select statement to review both of the columns that you are looking to change 
- SELECT Efficiency, FastCharge
FROM evCars;

### - 4.2 Selecting the correct String Function that we need to remove for each column.
- SELECT RTRIM(Efficiency, ' Wh/km'), RTRIM(FastCharge, 'km/h')
FROM evCars;

### - 4.3 Visualizing the Changes before making them 
- SELECT Efficiency, RTRIM(Efficiency, ' Wh/km'), FastCharge, RTRIM(FastCharge, 'km/h')
FROM evCars;

### - 4.4 UPDATE the records
- UPDATE evCars
SET Efficiency = RTRIM(Efficiency, ' Wh/km'), FastCharge = RTRIM(FastCharge, 'km/h');

### - 4.5 Check your work 
- SELECT Efficiency, FastCharge
FROM evCars;

### - 4.6 Convert the `FastCharge` units to MPH
- SELECT FastCharge, ROUND((FastCharge * 0.621371), 1) as OneHourFastChargeMiles
FROM evCars;

- UPDATE evCars
SET FastCharge = ROUND((FastCharge * 0.621371), 1);

- SELECT FastCharge
FROM evCars;

### - 4.7 Rename the column
- ALTER TABLE evCars
RENAME FastCharge to OneHourFastChargeMiles;

- ALTER TABLE evCars
RENAME Efficiency to EfficiencyWHperKM;

### - 4.8 Select All of the records to get a look at the whole table with your recent changes. 
- SELECT * 
FROM evCars;

# SECTION 5 
### - 5.1 Working with `RapidCharge`
- SELECT RapidCharge, COUNT(RapidCharge)
FROM evCars
GROUP BY RapidCharge;

### - 5.2 making data cleaning choices 

### - 5.3 Please fill in the blank on your .md answer sheet
- For the purpose of this exercise, if the car's `RapidCharge` value equals "Rapid charging possible" then I want you to change the value to 'Yes' 
- If the `RapidCharge` value equals "Rapid charging not possible" then I want you to change the value to 'No'.

### - 5.2 Writing the update Statements 
- UPDATE evCars
SET RapidCharge = 'Yes'
WHERE RapidCharge IS 'Rapid charging possible';

- UPDATE evCars
SET RapidCharge = 'No'
WHERE RapidCharge IS 'Rapid charging not possible';

# SECTION 6 
### -6.1 Visualize the `Powertrain` records
- SELECT PowerTrain, COUNT(PowerTrain)
FROM evCars
GROUP BY PowerTrain;

### - 6.2 Please fill in the blank on your .md answer sheet
- If the PowerTrain equals All Wheel Drive then I want you to change the value to 'AWD'
- If the PowerTrain equals Rear Wheel Drive then I want you to change the value to 'RWD'
- If the PowerTrain equals Front Wheel Drive then I want you to change the value to 'FWD'

### - 6.3 Write three update statements for the three different conditions 
- UPDATE evCars
SET PowerTrain = 'AWD'
WHERE PowerTrain = 'All Wheel Drive'; 

- UPDATE evCars
SET PowerTrain = 'RWD'
WHERE PowerTrain = 'Rear Wheel Drive'; 

- UPDATE evCars
SET PowerTrain = 'FWD'
WHERE PowerTrain = 'Front Wheel Drive'; 

### - 6.4 Write a query to Select all of the records to view your changes. 
- SELECT *
FROM evCars;

# SECTION 7 
### - 7.1 Convert the `PriceEuro` to `PriceUSD` 
- SELECT PriceEuro, ROUND((PriceEuro * 1.09), 2) as PriceUSD
FROM evCars;

### - 7.2 Write the Update Statements 
- UPDATE evCars
SET PriceEuro = ROUND((PriceEuro * 1.09), 2);

### - 7.3 Rename the Column
- ALTER TABLE evCars
RENAME PriceEuro TO PriceUSD;

