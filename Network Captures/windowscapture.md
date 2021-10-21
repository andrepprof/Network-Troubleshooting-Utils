## Take network captures on Windows clients using netsh

Sometimes we run into network connectivity problems and, just like ice cream (an undesired one), they come in different flavours. From failures to connect to our domain controllers and DNS servers to failures accessing a page on the web. In these circumstances, it would be great if we could look at the network packet flow and investigate what is going on. To this end, we can take network captures (aka traces) in our OS.  

Below you can find the steps on how to take a trace and open it on Windows clients. 

1. Open an elevated command prompt and run: 
```
netsh trace start scenario=netconnection capture=yes persistent=yes tracefile=c:\temp\nettrace.etl
```
>Make sure you have a \temp directory or choose another location.

![image](https://user-images.githubusercontent.com/92814106/138320668-781aa6ea-4c4b-4680-8575-ed0860335ee9.png)

2. Reproduce the connectivity problem
3. Stop the trace:
```	
netsh trace stop
```
![image](https://user-images.githubusercontent.com/92814106/138322069-77320706-dd20-449c-bebd-c384ddeec7a0.png)

4. Your trace will be stored in c:\temp\nettrace.etl

<img src="https://user-images.githubusercontent.com/92814106/138322242-6bea862d-6b90-4c0e-add0-796c8602476e.png" width=30%>

5. Open the nettrace.etl file with [Network Monitor](https://www.microsoft.com/en-us/download/details.aspx?id=4865) and good hunting! 

<img src="https://user-images.githubusercontent.com/92814106/138322766-4fe7f7c3-d4f8-40f4-ac93-1033f7bfa872.png" width=50%>

***Tip!***  Feel free to use the prebuilt filters to help you in your investigation.

<img src="https://user-images.githubusercontent.com/92814106/138324002-b30e1d2a-24b9-4803-99c9-4daf8d9b92cc.png" width=60%>

