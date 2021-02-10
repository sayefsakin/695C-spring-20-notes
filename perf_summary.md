The following data is for generating the utilization histogram only:

| Dataset | [Small](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/profiling_tools/configSmall.json) | | | | [Big](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/profiling_tools/config.json) ||||
| ------- | ------ | ----- | ---- | ---- | --- | ---- | --- | --- |
| Implementation | Interval Tree | SAT | SAT1 | SAT2 | Interval Tree | SAT | SAT1 | SAT2 |  
| Runtime | [0.309s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/histogramSmall.txt) | [0.529s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallOlder.txt) |  [0.122s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallNewerWithoutOpt.txt) | [0.045s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallNewerWithOpt.txt) | [1.403s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/histogramBig.txt) | [0.714s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigOlder.txt) | [1.138s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigNewerWithoutOpt.txt) | [0.048s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigNewerWithOpt.txt) |
 
 
SAT - Basic Summed Area Table

SAT1 - SAT with some pre-calculation and numpy integration 

SAT2 - SAT1 with binary search in C language.



### View Loading

|                  | Scripting | Rendering | Painting | System | Idl | Total | Total-idl |
|------------------|-----------|-----------|----------|--------|-----|-------|-----------|
| Old (first load) | 801       | 165       | 37       | 116    | 225 | 1345  | 1120      |
| Old (Panning)    | 4420      | 876       | 148      | 726    | 22  | 6192  | 6170      |
| Old (Scrolling)  | 3330      | 1509      | 193      | 759    | 165 | 5955  | 5790      |
| New (first load) | 348       | 42        | 12       | 313    | 254 | 969   | 715       |
| New (Panning)    | 1111      | 57        | 16       | 1048   | 399 | 2631  | 2232      |
| New (Panning2)   | 388       | 21        | 5        | 482    | 392 | 1289  | 897       |
| New (Scrolling)  | 506       | 36        | 9        | 419    | 458 | 1427  | 969       |

### Data Loading

#### New Implementation

| Gantt                                                                   | Begin (ns) | End  (ns)  | End-Begin  (ns) | Time (ms) |
|-------------------------------------------------------------------------|------------|------------|-----------------|-----------|
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 416663000  | 1664725001 | 1248062001      | 197       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 750120855  | 809313398  | 59192543        | 386       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 769851702  | 789582551  | 19730849        | 461       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 773572422  | 778122039  | 4549617         | 378       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 773572422  | 778122039  | 4549617         | 353       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 774940744  | 779490361  | 4549617         | 269       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 776428284  | 777944823  | 1516539         | 274       |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/ganttChartValues?bins=4236 | 526536800  | 531086417  | 4549617         | 246       |


| Line Chart                                                           | Metric Type  | Begin  (ns) | End  (ns)  | End-Begin  (ns) | Time (ms) | Total (gantt+line) |
|----------------------------------------------------------------------|--------------|-------------|------------|-----------------|-----------|--------------------|
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 416663000   | 1664725001 | 1248062001      | 183       | 380                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 750120855   | 809313398  | 59192543        | 521       | 907                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 769851702   | 789582551  | 19730849        | 523       | 984                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 773572422   | 778122039  | 4549617         | 551       | 929                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 773572422   | 778122039  | 4549617         | 518       | 871                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 774940744   | 779490361  | 4549617         | 352       | 621                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 776428284   | 777944823  | 1516539         | 366       | 640                |
| http://127.0.0.1:8000/datasets/FIB23_15Oct20/newMetricData?bins=4236 | PAPI_TOT_CYC | 526536800   | 531086417  | 4549617         | 320       | 566                |

#### Old Implementation

|                                                      | Begin (ns)  | End (ns)    | End-Begin (ns) | Data Load (ms) |
|------------------------------------------------------|-------------|-------------|----------------|----------------|
| http://127.0.0.1:8000/datasets/FIB23/intervals?begin | 721875839.3 | 726309405.4 | 4433566.105    | 367            |
| http://127.0.0.1:8000/datasets/FIB23/intervals?begin | 718461343.8 | 722894909.9 | 4433566.105    | 240            |
| http://127.0.0.1:8000/datasets/FIB23/intervals?begin | 1412210093  | 1416643660  | 4433566.105    | 1120           |
| http://127.0.0.1:8000/datasets/FIB23/intervals?begin | 1196803146  | 1205559915  | 8756769.34     | 2080           |