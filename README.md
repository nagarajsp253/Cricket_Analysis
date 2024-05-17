# Cricket Player Analysis Dashboard

## Problem Statement

Creating a dashboard that will help us to select best 11 cricket players as per the different criteria given using 2022 t20 worlcup data as a source from espncricinfo website.

Using this dashboard anyone can findout who will be the best suit to play in the final 11.

## Selection Parameters
<img width="406" alt="Openers" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/e99bc8c9-b0c1-4d4b-ac5e-81873e3b967f">
<img width="406" alt="Anchors" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/48f0e621-75e9-4996-a67f-982330836382">
<img width="407" alt="Finishers" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/6e589d94-5a63-41f1-9066-465190350475">
<img width="405" alt="allrounders" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/a2d19c51-5ce5-4631-874f-059220711687">
<img width="405" alt="Bowlers" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/36a885c8-9339-4e94-8279-dcafee88026b">

### Steps followed 

- Step 1 : Data Collection: Web Scraping
  - Source data will be the following json format files downloaded from the espncricinfo website.
    - t20_wc_batting_summary
    - t20_wc_bowling_summary
    - t20_wc_match_results
    - t20_wc_player_info

- Step 2 : Data Preparation using Python Pandas
  - All the tricky json format data will be converted to easy format and exported as a CSV files.
  - Below mentioned transformations are done through pandas in each of the files.
    - Column name change
    - Addition of new column
    - Dropping existing column
    - Removing special characters
    - Linking columns between files

- Step 3: - Loading all four CSV data files into Power BI Desktop usinf files option

- Step 4 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 5: Data transformation in powerquery
  - Given names to all the four files.
  - Made first row as header.
  - Removed duplicate record from Player_Info table
  - Extracted (c)/(wk) from player name column
  - Added a "stage" column in Match_Summary table: if match_date is before or equal to 22 October then value will be qualifier else super 12
  - Split the overs column to [overs.2] based on (.) delimiter to create new column "balls"
  - Added new custom column "balls": [overs.1] * 6 + [overs.2]
  - In "out/not_out" column replaced out with "1" and not_out with "0" then changed column name to "out".
  - Made some column name changes in Batting _Summary and Bowling_Summary tables.

Step 6: Data modelling
  - Correcsponding columns will be matched between fact and dimension tables
  - Fact tables: Batting_Summary, Bowling_Summary
  - Dimension tables: Player_Info, Match_Summary

Step 7: Creating Measures and Calculated columns
<img width="890" alt="Measures" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/fdb8796b-3347-4213-8634-5ebb3ac8f28e">

Step 8: Building visuals and dashboard
  - Main Dashboard:
    - Gives the details of Power hitter/Opener batters in table format who are fulfilling the selection parameters.
    - Line chart: to show the Batting_Average, Strike_Rate, Average_Balls_Faced and Boundary percentage.
    - Scatter chart: to show the Strike_Rate Vs Batting_Average
    - Individual Performance: Hovering on player name shows their performance in each match they played.
    - Combined Performance: Cards are added to show the combined performance when any of the  player is selected from table.
<img width="716" alt="Main_Dashboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/7cea30c2-5208-4b51-978c-a9da778c92b6">

  - Anchors/Middle Order:
    - Gives the details of Anchors/Middle Order batters in table format who are fulfilling the selection parameters.
<img width="711" alt="Anchors_Dashboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/15741d20-4546-4da8-bf78-c01339569922">

  - Finisher/Lower Order:
    - Gives the details of Finishers/Lower Order batters in table format who are fulfilling the selection parameters.
<img width="710" alt="Finishers_Dahboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/66b9c6e3-1751-4382-bf9c-237ebfac7016">

  - All Rounders/Lower Middle Order:
    - Gives the details of All Rounders/Lower Middle Orders in table format who are fulfilling the selection parameters.
    - Line chart: to show the Batting_Average, Strike_Rate, Bowling_Strike_Rate and Economy.
    - Scatter chart: to show the Bowling_Strike_Rate Vs Economy
<img width="711" alt="Allrounders_Dashboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/0eb26e5e-b977-4287-9d4c-1193da80f688">

  - Specialist Fast Bowlers / Tail End:
    - Gives the details of Specialist Fast Bowlers / Tail End bowlers in table format who are fulfilling the selection parameters.
    - Line chart: to show the Bowling_Average, Dot Ball Percentage, Bowling_Strike_Rate and Economy.
    - Scatter chart: to show the Bowling_Strike_Rate Vs Economy
<img width="712" alt="Bowlers_Dashboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/601f3fc8-4ca6-42a8-8cac-37fb838b6335">

  - Final 11:
    - Based on the details shown we can select the final 11 players and see their every details including the Team Performance.
<img width="710" alt="Final11_Dashboard" src="https://github.com/nagarajsp253/Cricket_Analysis/assets/52107536/04539251-8614-4ff3-8cac-bc476dfc4847">

  - Common Slicres: Slicer is added with the values qualifier and super12

  - Navigation Options In Each Page: Final 11, Power Hitters, Anchors, Finishers, All Rounders, Specialit Fast Bowlers.
           
