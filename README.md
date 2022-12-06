# exp1

### CPU SCHEDULING ALGORITHMS FCFS:
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p % d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
wt[0]=0; 
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n; 
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n; 
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}

```

### IMPLEMENTATION OF SHORTEST JOB FIRST SCHEDULING
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1; 
}
for(i=0;i<n;i++)
{
pos=i;
for(j=i+1;j<n;j++)
{
if(bt[j]<bt[pos])
pos=j;
}
temp=bt[i];
bt[i]=bt[pos];
bt[pos]=temp;
temp=p[i];
p[i]=p[pos];
p[pos]=temp;
}
wt[0]=0;
//calculate waiting time
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n;
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n; //average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}

```

### IMPLEMENTATION OF PRIORITY SCHEDULING:
```
#include<stdio.h>
int main()  {
int bt[20],p[20],wt[20],tat[20],pri[20],i,j,k,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++) 
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
printf(" enter priority of the process ");
for(i=0;i<n;i++) {
p[i] = i;
printf("p%d ",i+1);
scanf("%d",&pri[i]);  }
for(i=0;i<n;i++)
for(k=i+1;k<n;k++)
if(pri[i] > pri[k])  {
temp=p[i];
p[i]=p[k];
p[k]=temp;
temp=bt[i];
bt[i]=bt[k];
bt[k]=temp;
temp=pri[i];
pri[i]=pri[k];
pri[k]=temp;  }
wt[0]=0; 
for(i=1;i<n;i++)  {
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];  }
avg_wt=(float)total/n; 
total=0;
printf("\nProcess\t Burst Time \tPriority \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)  {
tat[i]=bt[i]+wt[i]; 
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],pri[i],wt[i],tat[i]);   }
avg_tat=(float)total/n; //average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}



```

### IMPLEMENTATION OF ROUND-ROBIN SCHEDULING:
```
#include<stdio.h>
main() {
int st[10],bt[10],wt[10],tat[10],n,tq; int
i,count=0,swt=0,stat=0,temp,sq=0;
float awt,atat;
printf("enter the number of processes");
scanf("%d",&n);
printf("enter the burst time of each process /n");
for(i=0;i<n;i++) {
printf(("p%d",i+1);
scanf("%d",&bt[i]);
st[i]=bt[i]; }
printf("enter the time quantum");
scanf("%d",&tq);
while(1) {
for(i=0,count=0;i<n;i++) {
temp=tq;
if(st[i]==0) {
count++;
continue; }
if(st[i]>tq)
st[i]=st[i]-tq;
else
if(st[i]>=0)  {
temp=st[i];
st[i]=0;  }
sq=sq+temp;
tat[i]=sq;  }
if(n==count)
break; }
for(i=0;i<n;i++)  {
wt[i]=tat[i]-bt[i];
swt=swt+wt[i];
stat=stat+tat[i];  }
awt=(float)swt/n;
atat=(float)stat/n;
printf("process no\t burst time\t waiting time\t turnaround time\n");
for(i=0;i<n;i++)
printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); printf("avg
wt time=%f,avg turn around time=%f",awt,atat); }

```

