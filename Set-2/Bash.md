``` REVERSE ```
we have given a reverse.me so we need to the ascii dump so just use strings command and search you can find a long string as flag but in reverse 
or you can write a script to reverse the each line in the file 
``` file=open("revers.me","r")
a=file.readlines()

fileo=open("8.txt","w+")
for i in a:
	fileo.write(i[::-1])

file.close()
fileo.close()
```

``` Stringer things ```
use grep -i to get the 2 flags in the ascii dump(strings). so basically if we see the ascii in the hex editor it consists of non-printable values and those are represented by "."
so as we have the flag format as inctf just do ```.i.n.c.t.f``` which didn't work since the precceding byte is in next offset so search for the offset of i.n.c. and go to the 
next offset and get the flag by removing "."

 ``` Twins ```
 as the question suggest both should be same but we can find difference using a python package ``` filecmp``` or some bash ```diff``` and can find that "binary files differ"
 so use the command ```diff   <(xxd Twin1) <(xxd Twin2) ``` and check the values where hex-dump is present 
 ![terminal](https://github.com/abhishekbharawaj/forensics/blob/main/pictures/Screenshot%20from%202021-02-22%2001-24-43.png) so if we consider the lines above hex dump each line consists of one character like i(146403c146403)... combinig all those gives flag
 
``` Loop1```
#!/bin/bash
num=6
for((i=0;i<num;i++))
do
	for((j=i;j<num-1;j++))
	do
		echo -ne " "
	done
	for((p=0;p<=i;p++))
	do
		echo -ne "#"
	done
	echo;
done
``` LOOP 2``` 
num=6;
 
for((i=1; i<=num; i++))
do
    for((j=i; j<=num; j++))
    do
      echo -ne " ";
    done
     for((n=1; n<=i; n++))
    do
      echo -ne "#";
    done
    for((k=1; k<i; k++))
    do
      echo -ne "#";
    done
 
   echo;
done


