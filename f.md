# 操作系统原理
## PV 操作

### Semaphore
1. 不能直接读写，信号量S必须带上P或者V
2. Semaphore是一个整数队列，如果S为正值，表示有多少个可用的临界资源；如果S为负值，表示没有空闲，有多少个进程正在等待；如果S为0，表示没有可用也没有等待。
3. PV code

    - PV in sleep and wake up
   ```
   P (Semaphore s){
       s=s-1;
       if(s<0){
           added to semaphore'squeue and sleep;
       }
   }

   V(Semaphore s){
       s=s+1;
       if(s<=0)
            wakeup in the waiting process in the semaphore's queue;
       }
   }

   ```

   - PV  in busy waiting

   ```
   P  (Semaphore s){
       while(!s>0){
           yield the CPU;
       }
       s--;
   }

   V (Semaphore s){
       s++;
   }

   ```

### examples

1. The producer-consumer problem





