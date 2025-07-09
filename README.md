# SummerAnalytics_Capstone
The primary objective of this code is to simulate and visualize dynamic pricing for urban parking lots based on occupancy patterns observed over time. This model adjusts prices in half-hourly intervals from 8:00 AM to 4:30 PM, considering the average occupancy during a ±5-minute window around each time slot.

Flow of the Code
1. Data Loading and Preprocessing
Dataset: dataset.csv
Columns used:
     1. 'LastUpdatedDate' and 'LastUpdatedTime' are combined to create a full Timestamp.
     2. 'SystemCodeNumber' identifies the parking location.
     3. 'Occupancy' and 'Capacity' are used for dynamic pricing logic.
        
2. Location Selection
The code extracts unique parking locations and prompts the user to enter a location.

3. Time Slot Generation
     1. Time intervals are set from 8:00 AM to 4:30 PM, broken into 18 half-hour slots.
     2. For each slot, the code considers a ±5-minute tolerance window to calculate occupancy averages
        
4. Dynamic Pricing Algorithm
   For each time slot:
     1. Data within the ±5 minute window is filtered.
     2. Average Occupancy and Average Capacity are calculated.
     3. Based on whether occupancy increased or decreased compared to the previous time slot, the pricing adjustment factor α (alpha) determined.
  
5. Output Results
    A new DataFrame result_df is created with:
    1. Location ID
    2. Time Slot
    3. Average Occupancy
    4. Capacity
    5. Alpha
    6. Calculated Price
    7. Data is saved to a CSV file
6. Bokeh Visualization
   A Bokeh line plot visualizes the price fluctuations over time.
   1. X-axis: Time Slots (from 8:00 to 4:30)
   2. Y-axis: Price
   3. Tooltip shows
   4. Time Slot
   5. Price
   6. Alpha
   7. Occupancy
   8. Capacity
  
Heuristics and Assumptions Used
 1. Time Smoothing: ±5-minute buffer ensures more stable averages even with sparse data.
 2. Baseline Reset: Each day starts with a price of $10.
 3. Linear Scaling of Alpha: Ensures proportional pricing change depending on congestion.
 4. No abrupt jumps: Gradual price change due to occupancy deltas.
