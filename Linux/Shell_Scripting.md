
## Shell Scripting

```shell
#!/bin/bash
# Add two numeric value
((sum=25+35))

#Print the result
echo -n "sum is "
echo $sum


echo -n " share number "
read number
echo $number


# Basics
ls
pwd
echo -n "Please write folder name to be created "
read dirname
mkdir $dirname
ls

#  Conddition 



echo -n "Enter a number: "
read num

if [[ $num -gt 10 ]]
then
echo "Number is greater than 10."
elif [[ $num -eq 10 ]]
then
echo "Number is equal to 10."
else
echo "Number is less than 10."
fi

# date
#!/bin/bash
year=$(date +%Y)
month=$(date +%B)
day=$(date +%d)
minute=$(date +%M)
echo $date
echo "Current Date is  $day-$month-$year"
touch myfile-$year-$month-$day--$minute



```
