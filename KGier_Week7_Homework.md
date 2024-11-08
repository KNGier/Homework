# Section 7.1
## Question 1
```SQL

SELECT "ModelYear", "Make", "Model"
FROM EVRegistry;

```
## Question 2 
```SQL

SELECT DISTINCT "ElectricVehicleType"
FROM EVRegistry;

```
## Question 3 
```SQL

SELECT *
FROM EVRegistry
WHERE "ElectricVehicleType" = "Battery Electric Vehicle (BEV)";

```
## Question 4 
```SQL

SELECT "Make", "Model"
FROM EVRegistry
WHERE "BaseMSRP" > 20000 AND "BaseMSRP" < 35000;

```
# Section 7.2 
## Question 1
```SQL

SELECT *
FROM EVRegistry
WHERE "City" IS NULL;

```
## Question 2 
```SQL

SELECT "Make", "Model", "ElectricVehicleType"
FROM EVRegistry
WHERE "VIN" LIKE "%3E1EA1J";

```
## Question 3 
```SQL

SELECT "ModelYear", "Make", "Model", "ElectricVehicleType", "ElectricRange"
FROM EVRegistry
WHERE "Make" IS "TESLA" OR MAKE IS "CHEVROLET"
ORDER BY "Make", "ModelYear" DESC;

```
## Question 4 
```SQL

SELECT "stationId", count(*) as "Times Used"
FROM EVCharging
GROUP BY "stationId"
ORDER BY "Times Used" DESC
LIMIT 5;

```
## Question 5 
```SQL

SELECT "userId", MIN("chargeTimeHrs") as "minTime", MAX("chargeTimeHrs") as "maxTime" 
FROM EVCharging
WHERE "chargeTimeHrs" > 0.5
GROUP BY "userId"
ORDER BY "minTime", "maxTime"

```
# Section 7.3 
## Question 1
```SQL

SELECT weekday, ROUND(AVG(chargeTimeHrs), 2) as avgChargeTime
FROM EVCharging
GROUP BY weekday
ORDER BY avgChargeTime DESC
LIMIT 1;

```
## Question 2 
```SQL

SELECT userId, ROUND(SUM(kwhTotal), 2) as totalPower
From EVCharging
GROUP BY userId
ORDER BY totalPower DESC
LIMIT 15;

```
## Question 3 
```SQL

SELECT dimFacility.typeFacility, COUNT(DISTINCT factCharge.stationId) as numStation
FROM factCharge
INNER JOIN dimFacility
ON factCharge.facilityID = dimFacility.FacilityKey
GROUP BY dimFacility.typeFacility
ORDER BY numStation DESC; 

```
## Question 4 
##### Each table has a key field that is populated with distinct values. The primary key is the key for the main table you're working with, and all primary key values are unique. Foreign keys are primary keys in other tables, but they also appear in the main table. In the main table, values in the foreign key fields can be duplicated. Foreign keys are what make joins possible. 

## Question 5 
```SQL

SELECT userId, MIN(chargeTimeHrs) as minTime, MAX(chargeTimeHrs) as maxTime
FROM EVCharging
GROUP BY userId
HAVING maxTime > 1 AND minTime > 1
ORDER BY minTime, maxTime;

```