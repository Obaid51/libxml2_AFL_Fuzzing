# libxml2_AFL_Fuzzing
Libxml2 fuzzing by passing xml fragments at runtime to AFL <br /> 
Clone this repository using <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git clone https://github.com/Obaid51/libxml2_AFL_Fuzzing.git<br /> 
Place the files in a separate folder.<br /> 
Open terminal and type following command to instrument the binary file <br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;afl-g++ -I /usr/include/libxml2 parse3.c -lm -lxml2<br /> 
This command will create an instrumented binary file named a.out<br /> 
Now type in terminal <br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;./a.out<br /> 
This would take you to the next line. In this line enter the xml fragment which you want to Fuzz. Don't press ENTER KEY, unless you are completed (Write the xml fragment in a single line)<br /> 
After pressing ENTER key, the xml fragment would be stored in binary file. <br /> 
Now for AFL-Fuzzing, use the command <br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;afl-fuzz -i test -o output -- a.out<br /> 
this should start AFL.<br /> 
If this shows some error like<br />  
&nbsp;&nbsp;&nbsp;&nbsp;PROGRAM ABORT : Pipe at the beginning of 'core_pattern'<br /> 
&nbsp;&nbsp;&nbsp;&nbsp;Location : check_crash_handling(), afl-fuzz.c:7347<br /> 
or anything like this simply type in terminal <br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sudo su<br /> 
//Type command written above PROGRAM ABORT (If there are multiple, run them step by step. After that type<br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;exit<br /> 
and then again use the AFL command <br /> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;afl-fuzz -i test -o output -- a.out<br /> 
This would start fuzzing. Scroll down in the terminal to view the Fuzzing process.<br /> 
The directory /output/crashes has all the crashes log and everything.<br /> 

P.s: You can also use the following command to pass the input using Stdin, if you don't want to pass it in binary file by 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;afl-fuzz -i test -o output -- a.out [commnad line input]<br /> 
