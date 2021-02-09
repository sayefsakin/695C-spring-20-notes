The following data is for generating the utilization histogram only:

| Dataset | [Small](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/profiling_tools/configSmall.json) | | | | [Big](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/profiling_tools/config.json) ||||
| ------- | ------ | ----- | ---- | ---- | --- | ---- | --- | --- |
| Implementation | Interval Tree | SAT | SAT1 | SAT2 | Interval Tree | SAT | SAT1 | SAT2 |  
| Runtime | [0.309s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/histogramSmall.txt) | [0.529s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallOlder.txt) |  [0.122s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallNewerWithoutOpt.txt) | [0.045s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesSmallNewerWithOpt.txt) | [1.403s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/histogramBig.txt) | [0.714s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigOlder.txt) | [1.138s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigNewerWithoutOpt.txt) | [0.048s](https://github.com/hdc-arizona/traveler-integrated/blob/36c150ea8eab33678476b98bc250fb33e325ebfa/drawValuesBigNewerWithOpt.txt) |
 
 
SAT - Basic Summed Area Table

SAT1 - SAT with some pre-calculation and numpy integration 

SAT2 - SAT1 with binary search in C language.