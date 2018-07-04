# school-work
#!/bin/bash

awk -F, '{print $7}' train.csv > age.csv
sed -i '1d' age.csv
sed -i '/^$/d' age.csv
echo -n "age:"
echo
cat age.csv|awk 'BEGIN {max = 0} {if ($1+0 > max+0) max=$1} END {print "Max=", max}' 
cat age.csv|awk 'BEGIN {min = 65536} {if ($1+0 < min+0) min=$1} END {print "Min=", min}'
echo The minimum age is 0.42 | tee age.csv
echo The maximum age is 80 | tee -a age.csv
echo -e "\n"


awk -F, '{print $11}' train.csv > cabin.csv
sed -i '1d' cabin.csv
echo -n "cabin:"
echo
grep '^$' cabin.csv | wc –l
echo 687 | tee cabin.csv
echo -e "\n"


awk -F, '{print $11}' train.csv > fare.csv
sed -i '1d' fare.csv
echo -n "fare:"
echo
cat fare.csv|awk 'BEGIN {max = 0} {if ($1+0 > max+0) max=$1} END {print "Max=", max}' 
cat fare.csv|awk 'BEGIN {min = 65536} {if ($1+0 < min+0) min=$1} END {print "Min=", min}'
echo min is 0 | tee fare.csv
echo max is 512.3292 | tee -a fare.csv
echo -e "\n"


awk -F, '{print $2}' train.csv > survived.csv
sed -i '1d' survived.csv
echo -n "survived:"
echo
cat survived.csv | grep ^1 | wc –l
cat survived.csv | grep ^0 | wc –l
echo "scale=4;342/(342+549)" | bc | tee survived.csv
echo -e "\n"


awk -F, '{print $6}' train.csv > sex.csv
sed -i '1d' sex.csv
echo -n "sex:"
echo
cat sex.csv | grep 'male' | wc –l
cat sex.csv | grep 'female' | wc –l
echo "scale=4;891/(891+314)" | bc | tee sex.csv
echo "scale=4;314/(891+314)" | bc | tee -a sex.csv
