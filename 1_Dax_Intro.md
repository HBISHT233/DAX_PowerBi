### DAX_Intro

#### Resource

![DAX_Intro](https://github.com/HBISHT233/DAX_PowerBi/blob/main/Images/2024-10-23-12-41-56-image.png)

#### Data Table vs Lookup Table

Here’s a comparison between a **data table** and a **lookup table** in a tabular format:

| Feature           | Data Table                                                                                 | Lookup Table                                                                                          |
| ----------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| **Content**       | Contains actual transactional or factual or Measurable  data (e.g., sales amounts, dates). | Contains dimension or descriptive data for lookup (e.g., product names, customer types).              |
| **Purpose**       | Stores primary business data or facts for analysis (e.g., sales, orders).                  | Stores reference information used to enrich or categorize data (e.g., product details, region names). |
| **Size**          | Usually larger with many records (transactions, events).                                   | Typically smaller, containing fewer records (unique categories, types).                               |
| **Relationships** | Often forms the "many" side in one-to-many relationships.                                  | Forms the "one" side in one-to-many relationships.                                                    |
| **Updates**       | Frequently updated as new transactions occur.                                              | Rarely updated; mostly static data for reference.                                                     |
| **Examples**      | Sales transactions, customer orders, inventory records.                                    | Product categories, region codes, customer types.                                                     |
| **Usage**         | Used for reporting and analysis of business metrics.                                       | Used for joining with data tables to provide additional context or metadata.                          |

![DAX_Intro](https://github.com/HBISHT233/DAX_PowerBi/blob/main/Images/2024-10-23-12-56-48-image.png)

#### Primary Key V/S Foreign Key

Here’s a comparison of the **Primary Key** and **Foreign Key** in the context of Power BI:

| Feature                   | Primary Key                                                                                              | Foreign Key                                                                                              |
| ------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Purpose**               | Uniquely identifies each record in a table (lookup/dimension table).                                     | Refers to the primary key in another table (data/fact table). Used to link tables together.              |
| **Table Type**            | Found in lookup (dimension) tables, like `Products` or `Customers`.                                      | Found in data (fact) tables, like `Sales` or `Orders`.                                                   |
| **Uniqueness**            | Values must be unique for each record (e.g., `ProductID`, `CustomerID`).                                 | Values can repeat and refer to multiple records (e.g., multiple sales for the same `ProductID`).         |
| **Role in Relationships** | Forms the "one" side of a one-to-many relationship.                                                      | Forms the "many" side of a one-to-many relationship.                                                     |
| **Example in Power BI**   | `ProductID` in a `Products` table uniquely identifies each product.                                      | `ProductID` in a `Sales` table links back to the `ProductID` in the `Products` table.                    |
| **Usage in Model**        | Used for filtering and slicing the fact table data based on categories in the lookup table.              | Used to aggregate and analyze facts (e.g., total sales) based on attributes in the related lookup table. |
| **Power BI Relationship** | Typically, you create a **one-to-many** relationship, where the primary key connects to the foreign key. | Part of a **many-to-one** relationship with the primary key in the dimension table.                      |

#### DAX operators

![DAX_Intro](https://github.com/HBISHT233/DAX_PowerBi/blob/main/Images/2024-10-23-13-08-29-image.png)

#### Common DAX function

![DAX_Intro](https://github.com/HBISHT233/DAX_PowerBi/blob/main/Images/2024-10-23-13-09-56-image.png)

#### Math & Stats Functions

| **Function**      | **Syntax**                                                  | **Example**                                               |
| ----------------- | ----------------------------------------------------------- | --------------------------------------------------------- |
| **SUM**           | `SUM(<ColumnName>)`                                         | `TotalSales = SUM(Sales[SalesAmount])`                    |
| **AVERAGE**       | `AVERAGE(<ColumnName>)`                                     | `AvgPrice = AVERAGE(Products[UnitPrice])`                 |
| **MAX**           | `MAX(<ColumnName>)`                                         | `MaxSales = MAX(Sales[SalesAmount])`                      |
| **MIN**           | `MIN(<ColumnName>)`                                         | `MinSales = MIN(Sales[SalesAmount])`                      |
| **DIVIDE**        | `DIVIDE(<Numerator>, <Denominator>[, <AlternativeResult>])` | `ProfitMargin = DIVIDE(Sales[Profit], Sales[Revenue], 0)` |
| **COUNT**         | `COUNT(<ColumnName>)`                                       | `TotalOrders = COUNT(Orders[OrderID])`                    |
| **COUNTA**        | `COUNTA(<ColumnName>)`                                      | `TotalItems = COUNTA(Inventory[ItemName])`                |
| **COUNTROWS**     | `COUNTROWS(<TableName>)`                                    | `TotalRows = COUNTROWS(Customers)`                        |
| **DISTINCTCOUNT** | `DISTINCTCOUNT(<ColumnName>)`                               | `DistinctCustomers = DISTINCTCOUNT(Sales[CustomerID])`    |

### Iterator Functions

| **Function** | **Syntax**                                                 | **Example**                                                 |
| ------------ | ---------------------------------------------------------- | ----------------------------------------------------------- |
| **SUMX**     | `SUMX(<Table>, <Expression>)`                              | `TotalProfit = SUMX(Sales, Sales[Revenue] - Sales[Cost])`   |
| **AVERAGEX** | `AVERAGEX(<Table>, <Expression>)`                          | `AvgProfit = AVERAGEX(Sales, Sales[Revenue] - Sales[Cost])` |
| **MAXX**     | `MAXX(<Table>, <Expression>)`                              | `MaxProfit = MAXX(Sales, Sales[Revenue] - Sales[Cost])`     |
| **MINX**     | `MINX(<Table>, <Expression>)`                              | `MinProfit = MINX(Sales, Sales[Revenue] - Sales[Cost])`     |
| **RANKX**    | `RANKX(<Table>, <Expression>[, <Value>, <Order>, <Ties>])` | `RankSales = RANKX(ALL(Sales), Sales[SalesAmount])`         |
| **COUNTX**   | `COUNTX(<Table>, <Expression>)`                            | `CountProducts = COUNTX(Products, Products[Category])`      |

#### Logical Functions

Here’s a **table format** with the **syntax and example** for each **logical function** mentioned in the image based on **Power BI DAX functions**:

| **Function** | **Syntax**                                                     | **Example**                                                                                  |
| ------------ | -------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **IF**       | `IF(<Condition>, <TrueResult>, <FalseResult>)`                 | `ProfitCheck = IF(Sales[Profit] > 1000, "High", "Low")`                                      |
| **IFERROR**  | `IFERROR(<Value>, <AlternateResult>)`                          | `SafeDivide = IFERROR(DIVIDE(Sales[Profit], Sales[Cost]), 0)`                                |
| **AND**      | `AND(<Condition1>, <Condition2>)`                              | `CheckStatus = IF(AND(Sales[Profit] > 1000, Sales[Cost] < 500), "Good", "Bad")`              |
| **OR**       | `OR(<Condition1>, <Condition2>)`                               | `CheckDiscount = IF(OR(Sales[Discount] > 10, Sales[Profit] > 500), "Valid", "Invalid")`      |
| **NOT**      | `NOT(<Condition>)`                                             | `NotProfitable = IF(NOT(Sales[Profit] > 0), "Loss", "Profit")`                               |
| **SWITCH**   | `SWITCH(<Expression>, <Value1>, <Result1>, ..., <ElseResult>)` | `CategoryCheck = SWITCH(Products[Category], "Electronics", "E1", "Clothing", "C1", "Other")` |
| **TRUE**     | `TRUE()`                                                       | `AlwaysTrue = IF(TRUE(), "Yes", "No")`                                                       |
| **FALSE**    | `FALSE()`                                                      | `AlwaysFalse = IF(FALSE(), "No", "Yes")`                                                     |

#### Text Functions

Here’s a **table format** with the **syntax and example** for each **text function** mentioned in the image based on **Power BI DAX functions**:

| **Function**    | **Syntax**                                                           | **Example**                                                       |
| --------------- | -------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **CONCATENATE** | `CONCATENATE(<Text1>, <Text2>)`                                      | `FullName = CONCATENATE(Employee[FirstName], Employee[LastName])` |
| **FORMAT**      | `FORMAT(<Value>, <FormatString>)`                                    | `FormattedDate = FORMAT(Sales[Date], "DD-MM-YYYY")`               |
| **LEFT**        | `LEFT(<Text>, <NumberOfCharacters>)`                                 | `FirstThree = LEFT(Customer[PhoneNumber], 3)`                     |
| **MID**         | `MID(<Text>, <StartPosition>, <NumberOfCharacters>)`                 | `MiddlePart = MID(Product[SKU], 2, 3)`                            |
| **RIGHT**       | `RIGHT(<Text>, <NumberOfCharacters>)`                                | `LastTwo = RIGHT(Customer[PhoneNumber], 2)`                       |
| **UPPER**       | `UPPER(<Text>)`                                                      | `UpperCaseName = UPPER(Employee[FirstName])`                      |
| **LOWER**       | `LOWER(<Text>)`                                                      | `LowerCaseName = LOWER(Employee[LastName])`                       |
| **PROPER**      | `PROPER(<Text>)`                                                     | `ProperName = PROPER(Customer[FullName])`                         |
| **LEN**         | `LEN(<Text>)`                                                        | `NameLength = LEN(Customer[FullName])`                            |
| **SEARCH**      | `SEARCH(<FindText>, <WithinText>[, <StartPosition>])`                | `SearchResult = SEARCH("Sales", Sales[Comment], 1)`               |
| **FIND**        | `FIND(<FindText>, <WithinText>[, <StartPosition>, <NotFoundValue>])` | `FindResult = FIND("A", Customer[Name])`                          |
| **REPLACE**     | `REPLACE(<OldText>, <Start>, <NumChars>, <NewText>)`                 | `CorrectedPhone = REPLACE(Customer[Phone], 4, 3, "123")`          |
| **REPT**        | `REPT(<Text>, <NumberOfTimes>)`                                      | `RepeatedText = REPT("-", 5)`                                     |
| **SUBSTITUTE**  | `SUBSTITUTE(<Text>, <OldText>, <NewText>[, <InstanceNum>])`          | `CorrectedText = SUBSTITUTE(Customer[Name], "Inc.", "LLC")`       |
| **TRIM**        | `TRIM(<Text>)`                                                       | `CleanName = TRIM(Customer[FullName])`                            |
| **UNICHAR**     | `UNICHAR(<Number>)`                                                  | `UnicodeChar = UNICHAR(169)`                                      |

#### Filter Functions

Here’s a **table format** with the **syntax and example** for each **filter function** mentioned based on **Power BI DAX functions**:

| **Function**        | **Syntax**                                           | **Example**                                                                                                    |
| ------------------- | ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **CALCULATE**       | `CALCULATE(<Expression>, <Filter1>, <Filter2>, ...)` | `TotalSalesFiltered = CALCULATE(SUM(Sales[SalesAmount]), Sales[Region] = "North")`                             |
| **FILTER**          | `FILTER(<Table>, <Expression>)`                      | `FilteredSales = FILTER(Sales, Sales[SalesAmount] > 1000)`                                                     |
| **ALL**             | `ALL(<Table/Column>)`                                | `AllProducts = CALCULATE(SUM(Sales[SalesAmount]), ALL(Products))`                                              |
| **ALLEXCEPT**       | `ALLEXCEPT(<Table>, <Column1>, <Column2>, ...)`      | `SalesWithoutCategory = CALCULATE(SUM(Sales[SalesAmount]), ALLEXCEPT(Sales, Sales[Category]))`                 |
| **RELATED**         | `RELATED(<Column>)`                                  | `ProductName = RELATED(Products[ProductName])`                                                                 |
| **RELATEDTABLE**    | `RELATEDTABLE(<Table>)`                              | `TotalOrders = COUNTROWS(RELATEDTABLE(Orders))`                                                                |
| **DISTINCT**        | `DISTINCT(<Column>)`                                 | `DistinctRegions = DISTINCT(Sales[Region])`                                                                    |
| **VALUES**          | `VALUES(<Column>)`                                   | `RegionValues = VALUES(Sales[Region])`                                                                         |
| **EARLIER**         | `EARLIER(<Column>[, <Number>)`                       | `SalesRank = RANKX(FILTER(Sales, Sales[SalesAmount] < EARLIER(Sales[SalesAmount])), Sales[SalesAmount])`       |
| **EARLIEST**        | `EARLIEST(<Column>[, <Number>])`                     | `EarliestSaleDate = EARLIEST(Sales[SaleDate])`                                                                 |
| **HASONEVALUE**     | `HASONEVALUE(<Column>)`                              | `IsSingleRegion = IF(HASONEVALUE(Sales[Region]), "Yes", "No")`                                                 |
| **HASONEFILTER**    | `HASONEFILTER(<Column>)`                             | `IsFiltered = HASONEFILTER(Sales[Category])`                                                                   |
| **ISFILTERED**      | `ISFILTERED(<Column>)`                               | `CheckFilter = IF(ISFILTERED(Sales[Category]), "Filtered", "Not Filtered")`                                    |
| **USERELATIONSHIP** | `USERELATIONSHIP(<Column1>, <Column2>)`              | `TotalSalesWithAltRel = CALCULATE(SUM(Sales[SalesAmount]), USERELATIONSHIP(Sales[OrderDate], Calendar[Date]))` |

#### Date & Time function

Here’s a **table format** with the **syntax and example** for each **date and time function** based on **Power BI DAX functions**:

| **Function**      | **Syntax**                                                                   | **Example**                                                                                            |
| ----------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **DATEDIFF**      | `DATEDIFF(<StartDate>, <EndDate>, <Interval>)`                               | `DaysBetween = DATEDIFF(Orders[OrderDate], Orders[ShipDate], DAY)`                                     |
| **YEARFRAC**      | `YEARFRAC(<StartDate>, <EndDate>)`                                           | `FractionYear = YEARFRAC(Orders[StartDate], Orders[EndDate])`                                          |
| **YEAR**          | `YEAR(<Date>)`                                                               | `OrderYear = YEAR(Orders[OrderDate])`                                                                  |
| **MONTH**         | `MONTH(<Date>)`                                                              | `OrderMonth = MONTH(Orders[OrderDate])`                                                                |
| **DAY**           | `DAY(<Date>)`                                                                | `OrderDay = DAY(Orders[OrderDate])`                                                                    |
| **HOUR**          | `HOUR(<DateTime>)`                                                           | `OrderHour = HOUR(Orders[OrderDateTime])`                                                              |
| **MINUTE**        | `MINUTE(<DateTime>)`                                                         | `OrderMinute = MINUTE(Orders[OrderDateTime])`                                                          |
| **SECOND**        | `SECOND(<DateTime>)`                                                         | `OrderSecond = SECOND(Orders[OrderDateTime])`                                                          |
| **TODAY**         | `TODAY()`                                                                    | `CurrentDate = TODAY()`                                                                                |
| **NOW**           | `NOW()`                                                                      | `CurrentDateTime = NOW()`                                                                              |
| **WEEKDAY**       | `WEEKDAY(<Date>[, <ReturnType>])`                                            | `DayOfWeek = WEEKDAY(Orders[OrderDate], 1)`                                                            |
| **WEEKNUM**       | `WEEKNUM(<Date>[, <ReturnType>])`                                            | `OrderWeek = WEEKNUM(Orders[OrderDate], 1)`                                                            |
| **DATESYTD**      | `DATESYTD(<DatesColumn>[, <YearEndDate>])`                                   | `SalesYTD = CALCULATE(SUM(Sales[SalesAmount]), DATESYTD(Calendar[Date]))`                              |
| **DATESQTD**      | `DATESQTD(<DatesColumn>)`                                                    | `SalesQTD = CALCULATE(SUM(Sales[SalesAmount]), DATESQTD(Calendar[Date]))`                              |
| **DATESMTD**      | `DATESMTD(<DatesColumn>)`                                                    | `SalesMTD = CALCULATE(SUM(Sales[SalesAmount]), DATESMTD(Calendar[Date]))`                              |
| **DATEADD**       | `DATEADD(<DatesColumn>, <NumberOfIntervals>, <Interval>)`                    | `SalesLastYear = CALCULATE(SUM(Sales[SalesAmount]), DATEADD(Calendar[Date], -1, YEAR))`                |
| **DATESINPERIOD** | `DATESINPERIOD(<DatesColumn>, <StartDate>, <NumberOfIntervals>, <Interval>)` | `SalesInPeriod = CALCULATE(SUM(Sales[SalesAmount]), DATESINPERIOD(Calendar[Date], TODAY(), -30, DAY))` |

#### Calculated Column v/s Measure

| Feature                      | **Calculated Columns**                                                                                 | **Measures**                                                                                  |
| ---------------------------- | ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| **Definition**               | A column added to a table that contains values calculated row by row using DAX.                        | A dynamic calculation performed at the time of report viewing using DAX.                      |
| **Calculation Scope**        | Computed for each row in the table and stored in the data model.                                       | Computed dynamically based on the context of the visual or report.                            |
| **Storage**                  | Values are stored in the table as part of the data model.                                              | Not stored; recalculated each time they are used in a visual.                                 |
| **Performance Impact**       | Can impact performance, especially with large tables, as they increase the model size.                 | More efficient in large datasets, as they calculate only when needed.                         |
| **Row-Level or Aggregate**   | Works at the row level (e.g., row-by-row calculations).                                                | Works at an aggregate level based on the context (e.g., total sales, average quantity).       |
| **Usage in Filters/Slicers** | Can be used as fields in slicers and filters, just like any other column.                              | Cannot be used as slicers or filters directly; they can only be displayed in visuals.         |
| **Recalculation Frequency**  | Calculated once when the data model is refreshed or when the column is created.                        | Recalculated dynamically whenever a visual or report using the measure is refreshed.          |
| **Examples**                 | Concatenating `FirstName` & `LastName` into a `FullName` column.                                       | Summing up `SalesAmount` in a visual to calculate total sales.                                |
| **Memory Usage**             | Increases memory usage as calculated columns are stored in the model.                                  | Low memory usage since measures are not stored but recalculated.                              |
| **Best Use Case**            | Best for row-by-row calculations and adding extra fields to a table (e.g., `Profit = Revenue - Cost`). | Best for aggregate or summary calculations in visuals (e.g., `Total Sales`, `Average Price`). |
| **Examples of DAX**          | `Profit = [Revenue] - [Cost]` (row-by-row calculation)                                                 | `TotalSales = SUM([SalesAmount])` (aggregate calculation)                                     |

#### Filter Context v/s Row context

| Feature                  | **Filter Context**                                                                                                                                                           | **Row Context**                                                                                                                               |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**           | The set of filters applied to a data model, either through slicers, filters, or visuals, affecting the calculation results.                                                  | The context of a single row where calculations are evaluated for each row individually in a table.                                            |
| **Scope**                | Applies to multiple rows or the entire dataset, depending on how filters are applied.                                                                                        | Applies to one row at a time, performing calculations row by row.                                                                             |
| **Use Case**             | Used for aggregations and summarizations in visuals (e.g., calculating the total or average of a column for a subset of data).                                               | Used for row-by-row calculations, such as calculated columns or iterating over rows with functions like `SUMX` or `FILTER`.                   |
| **How It's Triggered**   | Triggered by slicers, filters, or groupings in Power BI visuals or DAX expressions like `CALCULATE`.                                                                         | Triggered when evaluating a DAX formula for each row in a table (e.g., when using iterators like `SUMX`, `FILTER`, or in calculated columns). |
| **Example of Use**       | When you filter a report to only show data for the year 2023, the filter context limits the data to that year, and calculations like `SUM(SalesAmount)` reflect this filter. | When calculating `Profit = [Revenue] - [Cost]` for each row in a table, the DAX formula uses row context to compute the value row by row.     |
| **DAX Functionality**    | Functions like `CALCULATE` can modify filter context by adding or removing filters.                                                                                          | Functions like `SUMX` or `FILTER` operate within row context, iterating over rows in a table.                                                 |
| **Key DAX Functions**    | `CALCULATE`, `FILTER`, `ALL`, `VALUES`, `REMOVEFILTERS`                                                                                                                      | `SUMX`, `AVERAGEX`, `FILTER`, `RELATED`, `EARLIER`                                                                                            |
| **Example DAX Formula**  | `CALCULATE(SUM(SalesAmount), Year = 2023)` sums `SalesAmount` but only for rows where `Year` equals 2023.                                                                    | `TotalProfit = SUMX(Sales, Sales[Revenue] - Sales[Cost])` calculates profit for each row in the `Sales` table and then sums the results.      |
| **Visualization Impact** | Filter context changes the data that appears in visuals based on user interaction (e.g., filtering by year, product category).                                               | Row context affects calculations within each row of a table (e.g., calculating row-level profit or discount).                                 |
| **Typical Scenario**     | Aggregating total sales for a specific year or region based on filters applied.                                                                                              | Calculating `Discount` for each individual sale by subtracting a percentage from `Price`.                                                     |
