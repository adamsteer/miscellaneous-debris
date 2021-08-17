# notes on getting to dd.ddddd from NMEA

NMEA is logged as `ddmm.mmmmm N` and `dddmm.mmmmmm E`, which is kind of useless for anyone. We want it to be ddd.dddddd, so we can map stuff.

This AWK one liner translates from a two column space delimited NMEA format file to a two column space delimited file with coordinates in ddd.ddddd format:

`awk '{printf "%.6f %.6f\n", substr($1,1,2) + substr($1,3)/60, substr($2,1,3) + substr($2,4)/60}' stupid-nmea-file.txt > sanefile.txt`
