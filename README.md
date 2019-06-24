# awesome_linux_data_processing_commands
awk, sed and other linux CLI-based commands for data processing


>Command to subtract from 356600 from each row of ABS_TIME column (using awk)

awk -F, '{$1=($1!="ABS_TIME")?$1-=356600:$1;}1' OFS=, col_only_AB_0.csv > final_col_only_AB_0.csv

>Command to subtract previous row value from current row of a column (using awk)

awk -F, '{$(NF+1)=$1-_n;_n=$1;}1' OFS=, full_col.csv > final_col.csv

>Command to convert hexadecimal to decimal of all values in a column (using awk)

awk -F, '{$2=($2!="ROW")?(strtonum("0x" $2)):$2}1' OFS=, row_only_AB_0.csv > row_dec_AB_0.csv

>Command to print values at 65538th line (using sed)

sed -n '65538p' < final_AB_0.csv

Install python using compiling from source code and create “venv” using this installed python
http://www.benhepworth.com/blog/2016/05/18/install-python-to-separate-directory-on-linux-in-5-easy-steps
mypython3/bin/python3 -m venv myenv (create “venv” using this installed python)
Command to check memory usage by a python script
pmap $(ps -ef | grep script.py | grep -v grep | awk '{print $2}')
Command to check the python processes running
ps -ef | grep python
Command to modify a specific cell in .csv file
awk -F, 'FNR==1,FNR==1{$3=”TIME_DIFF”}1' OFS=,  temp.csv > temp1.csv
