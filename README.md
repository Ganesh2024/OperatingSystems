# Synchronisation Mechanisms
There are two types of Synchronisation Mechanisms
  1. Busy waiting
  2. Without Busy Waiting

### Busy Waiting:
![knocking-jamie-fine](https://github.com/Ganesh2024/OperatingSystems/assets/90674180/4e1464aa-71ec-40c9-a0ca-f30c91cbdd18)


  1. Lock variable
  2. Test_and_Set Lock
  3. Turn variable
  4. interested variable
  5. Peterson Solution

##### 1. Lock variable:

![closingDoor](https://github.com/Ganesh2024/OperatingSystems/assets/90674180/66823d31-8897-4dda-9a2f-8ad7a8288834)


``` C++
//lock variable common to all process
//Entry Section
while(lock!=0) ;    // 1

lock = 1;           // 2
// Critical Section // 3

//Exit Section      
lock = 0;           // 4

```
Scenario:
Two process P0 and P1 trying to access CS, then consider below order of execution

| -> indicates preemption

P0: 1 as initially lock = 0 , it comes out of loop, but preempted before locking the CS.

P1: 1 still lock = 0 , it will also comes out of loop .

Now both process may enter into CS simultaneously.

So it is not satisfiying even first requirement(mutual exculsion) to became Synchronisation Mech.

We can observe that by making step 1 and step 2 atomic then we can solve above problem. right? 

![idea2](https://github.com/Ganesh2024/OperatingSystems/assets/90674180/dca273fd-8862-4430-bdff-d1e86bae3929)




#### 2. Test_and_Set Lock:
``` C++

//Below function will be made atomic , for that requires help from OS
void test_and_set(int lock){
  int x = lock;
  lock = 1;
  return x;
}

// Entry Section
while(test_and_set(lock)) ;

// CS

// Exit Section 
lock = 0;

```











