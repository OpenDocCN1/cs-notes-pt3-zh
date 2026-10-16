# Solution 1: allow at most 4 philosophers to be setting simultaneously at the table

```
semaphore chopstick[5]={1,1,1,1,1};
semaphore room=4;
int i;
void philosopher(int i)
{
  while(1){
    thinking;
    wait (room);
    wait (chopstick[i]);
    wait (chopstick[(i+1) % 5]);
    eating;
    signal (chopstick[(i+1) % 5]);
    signal (chopstick[i]);
    signal (room);
  }
}
```