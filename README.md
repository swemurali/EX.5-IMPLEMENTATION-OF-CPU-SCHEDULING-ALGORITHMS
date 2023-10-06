# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS
## First-Come-First-Serve (FCFS) Scheduling
## AIM: To implement First-Come-First-Serve (FCFS) Scheduling
## ALGORITHM:
```
Start with a queue (or a list) to represent the ready queue of processes.
Initialize a timer or clock to 0.
Read the number of processes (n) and create a data structure to store process information, including arrival time (AT) and burst time (BT) for each process.
Read the arrival time and burst time for each process and store them in the data structure.
Sort the processes in the ready queue based on their arrival times in ascending order. This step ensures that processes are executed in the order they arrive.
Initialize the waiting time (WT) and turnaround time (TAT) for the first process to 0.
For each process in the ready queue (in the order of arrival): a. Calculate the start time (ST) as the maximum of the current time and the arrival time of the process. b. Calculate the finish time (FT) as the start time plus the burst time of the process. c. Calculate the waiting time (WT) for the process as the start time minus the arrival time. d. Calculate the turnaround time (TAT) for the process as the finish time minus the arrival time. e. Update the current time to the finish time.
Calculate the average waiting time (AWT) and average turnaround time (ATAT) for all processes by summing up the individual waiting times and turnaround times and dividing by the total number of processes.
Display the waiting time, turnaround time, and other relevant information for each process.
Display the average waiting time and average turnaround time for all processes.
End.
```
## PROGRAM:
```
#include<stdio.h>
int main()
{
int c=0,i,n,bt[10],at[10],wt[10],ft[10];
int st[10],tat[10];
float awt=0,atat=0,rr[10];
printf("Enter the number of process : ");
scanf("%d",&n);
for(i=1;i<=n;i++)
{
printf("Enter the arrival time and burst time for the process %d",i);
scanf("%d %d",&at[i],&bt[i]);


}
for(i=1;i<=n;i++)
{
st[i]=c;
c=c+bt[i];
wt[i]=st[i]-at[i];
ft[i]=st[i]+bt[i];
tat[i]=wt[i]+bt[i];
rr[i]=tat[i]/bt[i];
}
for(i=1;i<=n;i++)
{
awt=awt+wt[i];
atat=atat+tat[i];
}
awt=awt/n;
atat=atat/n;
printf("\n\t\t CPU SCHEDULING\n\t\t ***************");
printf("\n\t\t FIRST COME FIRST SERVE\n\t\t **********************");
printf("\n--------------------------------------------------------------\n");
printf("proc\t at\t bt\t st\t ft\t wt\t tat\t rr\t\n");
printf("--------------------------------------------------------------");
for(i=1;i<=n;i++)
{
printf("\n %d\t %d\t %d\t %d\t %d\t %d\t %d\t%5.2f",i,at[i],bt[i],st[i],ft[i],wt[i],tat[i],rr[i]);
}
printf("\n--------------------------------------------------------------");
printf("\n Average waiting time is %5.2f\n average tat is%5.2f",awt,atat); }
```
## OUTPUT:
![image](https://github.com/R-Guruprasad/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390308/3ea74df2-1441-4c29-a46b-787f7c0586b3)


## RESULT: First-Come-First-Serve Scheduling is implemented successfully.
Shortest Job First (SJF) Preemptive Scheduling
## AIM: To implement Shortest Job First (SJF) Preemptive Scheduling
ALGORITHM:
```
Initialize variables and arrays to store process information, such as process ID (p), arrival time (at), burst time (bt), start time (st), finish time (ft), waiting time (wt), turnaround time (tt), response ratio (rr), and a flag to mark completed processes (iscompleted).

Read the number of processes (n) from the user.

Read the process ID, arrival time, and burst time for each process and store them in respective arrays (p, at, bt).

Initialize variables, such as nextst (next start time) and counters.

Loop until all processes are completed: a. Find the process with the minimum burst time among the processes that have arrived and are not completed. b. Update the start time, finish time, waiting time, and turnaround time for the selected process. c. Calculate the response ratio (rr) for the selected process (rr = turnaround time / burst time). d. Mark the selected process as completed. e. Update the nextst to the finish time of the selected process.

Calculate the average waiting time (AWT) and average turnaround time (ATT) by summing up the individual waiting times and turnaround times and dividing by the total number of processes.

Display the process information, including process ID, arrival time, burst time, start time, finish time, waiting time, turnaround time, and response ratio.

Display the average waiting time and average turnaround time.
```
## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,n,p[10],st[10],at[10],bt[10],ft[10],wt[10],tt[10];
int nextst,count,minsrt,minpos;
static int  iscompleted[10];
float rr[10],awt=0,att=0;
printf("\n\t SHORTEST JOB FIRST\n\t ******************");
printf("\nEnter the no. of process to be executed :");
scanf("%d",&n);
printf("\nEnter the process,arrival time and burst time\n");
for(i=0;i<n;i++)
{
scanf("%d %d %d",&p[i],&at[i],&bt[i]);
}
nextst=0;
for(count=0;count<n;count++)
{
minsrt=100;
minpos=0;
for(i=0;i<n;i++)
{
if(at[i]<=nextst&&iscompleted[i]==0)
{
if(minsrt>bt[i])
{
minsrt=bt[i];
minpos=i;
}
}
}
i=minpos;
st[i]=nextst;
ft[i]=st[i]+bt[i];
wt[i]=st[i]-at[i];
tt[i]=wt[i]+bt[i];
rr[i]=tt[i]/bt[i];
iscompleted[i]=1;
nextst=ft[i];
}
printf("\n---------------------------------------");
printf("\nPRO AT bT ST FT WT TT RR \n");
printf("---------------------------------------\n");
for(i=0;i<n;i++)
{
printf("%3d %2d %2d",p[i],at[i],bt[i]);
printf(" %3d %2d %2d %2d %4.2f\n",st[i],ft[i],wt[i],tt[i],rr[i]);
}
printf("---------------------------------------");
for(i=0;i<n;i++)
{
awt=awt+wt[i];
att=att+tt[i];
}
awt=awt/n;
att=att/n;
printf("\nAverage waiting time is %5.2f",awt);
printf("\nAverage turn around time is %5.2f",att);
}
```
 ## OUTPUT:
![image](https://github.com/R-Guruprasad/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390308/76a4fd2c-c241-4aa2-a613-35eb3e9f38fe)


## RESULT: 
Shortest Job First (SJF) preemptive scheduling is implemented successfully.
## Round Robin (RR) Scheduling
## AIM: To implement Round Robin (RR) Scheduling
## PROGRAM:
```
#include<stdio.h>
int main()
{
int n,i,pro[10],at[10],srt[10],st[10],ft[10],wt[10],tt[10];
static int iscompleted[10],isstarted[10],isentered[10];
int queue[10],f,r,count,tq,j,timer,totalsrt,tempsrt[10];
float rr[10],awt=0,atat=0;
printf("\n\t ROUND ROBIN");
printf("\nEnter the no. of process :");
scanf("%d",&n);

printf("\nEnter the value for Time Quantum:");
scanf("%d",&tq);
printf("\nEnter the process id for n process:\n");
for(i=0;i<n;i++)
{
scanf("%d",&pro[i]);
}
printf("\nEnter the arrival time for n process :\n");
for(i=0;i<n;i++)
{
scanf("%d",&at[i]);
}
printf("\nEnter the Burst time for n process:\n");
for(i=0;i<n;i++)
{
scanf("%d",&srt[i]);
}
totalsrt=0;
for(i=0;i<n;i++)
{
totalsrt=totalsrt+srt[i];
tempsrt[i]=srt[i];
}
f=0;
r=-1;
count=0;
timer=0;
for(i=0;i<n;i++)
{
if(at[i]==0)
{
r=(r+1)%n;
queue[r]=i;
isentered[i]=1;
count=count+1;
}
}
while(timer<totalsrt)
{
j=queue[f];
f=(f+1)%n;
if(isstarted[j]==0)
{
st[j]=timer;
wt[j]=st[j]-at[j];
isstarted[j]=1;
}
if(srt[j]>=tq)

{
timer=timer+tq;
srt[j]=srt[j]-tq;
}
else
{
timer=timer+srt[j];
srt[j]=srt[j]-srt[j];
}
if(srt[j]==0)
{
ft[j]=timer;
wt[j]=wt[j]+(ft[j]-(st[j]+tempsrt[j]));
tt[j]=wt[j]+tempsrt[j];
rr[j]=(float)tt[j]/tempsrt[j];
iscompleted[j]=1;
}
for(i=0;i<n&&count<n;i++)
{
if(at[i]<=timer&&isentered[i]==0)
{
r=(r+1)%n;
queue[r]=i;
isentered[i]=1;
count=count+1;
}
}
if(iscompleted[j]==0)
{
r=(r+1)%n;
queue[r]=j;
}
}
printf("\n\t CPU SCHEDULING\n\t **************");
printf("\n\t ROUND ROBIN\n\t ***********\n");
printf("------------------------------------------- \n");
printf("PRO AT BUT ST FT WT TT RR");
printf("\n------------------------------------------- \n");
for(i=0;i<n;i++)
{
printf("%3d %2d %2d",pro[i],at[i],tempsrt[i]);
printf(" %3d %3d %2d",st[i],ft[i],wt[i]);
printf(" %3d %4.2f\n",tt[i],rr[i]);
}
printf("------------------------------------------ ");

for(i=0;i<n;i++)
{
awt=awt+wt[i];
atat=atat+tt[i];
}
awt=awt/n;
atat=atat/n;
printf("\nAvg waiting time is %5.2f ",awt );
printf("\nAvg turn around time is %5.2f",atat);
}
```
## OUTPUT:
![image](https://github.com/R-Guruprasad/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390308/76a4fd2c-c241-4aa2-a613-35eb3e9f38fe)

## RESULT: Round Robin (RR) Scheduling is implemented successfully.
### Priority Preemptive Scheduling
## AIM: To implement Priority Preemptive Scheduling
## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,n,pid[10],at[10],srt[10],st[10],ft[10],wt[10],tt[10],pri[10];
int timer,totalsrt,tempsrt[10],minsrt,minpos; static int iscompleted[10],isstarted[10];
float rr[10],awt,atat;
printf("\n\t PRIORITY PRE-EMPTIVE\n\t ********************");
printf("\nENTER THE NO.OF PROCESSES TO BE EXECUTED\n");
scanf("%d",&n);
printf("ENTER THE PROCESSES ID,ARRIVAL TIME,BURST TIME AND PRIORITY \n");
for(i=0;i<n;i++)
scanf("%d %d %d %d",&pid[i],&at[i],&srt[i],&pri[i]);

totalsrt=0;
for(i=0;i<n;i++)
{
totalsrt=totalsrt+srt[i];
tempsrt[i]=srt[i];
}
timer=0;
while(timer<totalsrt)
{
minsrt=100;
minpos=0;
for(i=0;i<n;i++)
{
if(at[i]<=timer && iscompleted[i]==0)
{
if(minsrt>pri[i])
{
minsrt=pri[i];
minpos=i;
}
}
}
i=minpos;
if(isstarted[i]==0)
{
st[i]=timer;
wt[i]=st[i]-at[i];
isstarted[i]=1;
}
srt[i]=srt[i]-1;
timer=timer+1;
if(srt[i]==0)
{
ft[i]=timer;
wt[i]=wt[i]+(ft[i]-(st[i]+tempsrt[i]));
tt[i]=wt[i]+tempsrt[i];
rr[i]=tt[i]/tempsrt[i];
iscompleted[i]=1;
}
}
printf("\n\t CPU SCHEDULING ALGORITHM\n\t ************************");
printf("\n\t PRIORITY PRE-EMPTIVE\n\t ********************");
printf("\n--------------------------------------------------");
printf("\nPID AT SRT ST FT WT TT RR PRIORITY\n");
printf("--------------------------------------------------\n");
for(i=0;i<n;i++)
{
printf("%2d %2d %2d ",pid[i],at[i],tempsrt[i]);
printf("%2d %2d %2d %2d %2.2f %3d\n",st[i],ft[i],wt[i],tt[i],rr[i],pri[i]);

}
printf("--------------------------------------------------\n");
for(i=0;i<n;i++)
{
awt=awt+wt[i];
atat=atat+tt[i];
}
atat=atat/n;
awt=awt/n;
printf("The average waiting time is: %5.2f\n",awt);
printf("The average turn around time is: %5.2f",atat);
}
```
## OUTPUT:
![image](https://github.com/R-Guruprasad/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390308/76a4fd2c-c241-4aa2-a613-35eb3e9f38fe)

## RESULT: Priority Non-preemptive scheduling is implemented successfully.
