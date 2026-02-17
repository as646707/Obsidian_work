

# Chapter 1

**summary** --
1. How data is equally as important as hardware resources and how data is needed for every aspect in the world of applications and how crutial it is to make datasystems .
2. what are data systems ? --  well data systems are the architectural model of how different types of databases work together to maintain three different aspects that are necessary for the working of an application . namely- "Reliability ", "scalability ", "maintainability "
3. reliability - to work even if there is an error in the system either harware or software error that is reliablity 
4. things that can be a problem for  reliability - 
     1. **hardware backup method** - to maintain backup systems so that in an event of a faliure the system can save and load back its data and work like normal again .this is done by many systems engineers that have many many backup systems to maintain the flow of their applications in case of failure.  so even if failure  happens you can quickly recover from and still give the performance .
     2. fault vs failure - the system has to be resilient of the faults that occur in it , these are inevitable and cannot be stopped so the system should work despite of these to maintain reliability .
     3. software failures - so software failiure is important to understand cause a bug can cause massive problems that can hamper reliabliity of a system these included the following -- 
          1. one component can fail and cause a domino effect and can crash a the whole system .
          2. one component can make a certain assumption like a special case and the code is written with that in mind but that may become the source of the problem later on as that constraint might now always be that relavent .
    4. the human error - the most common type of error found is the human error and its necessary to fix or prevent this to make the application reliable here are a few ways that human errors can be prevented -
         1. creeate a sandbox for the engineers to experiment and to try out their ideas 
         2. maintain proper documentations for monitoring the system and futre problem diagnosis .
         3. fater roll back 
         4. testing - unit testing and integration testing and all that 
5. Scalability - ability to handle all types of increased loads of any type 
6. Things to know in scalability --  
         1. know what to scale - you dont have to scale everything so scale only the things that are necessary that is it and nothing else understand what the users needs are and only scale the things that are becomming a bottle neck or would become a bottle neck in the future .
         2. Example -- twitter - 
          twitter has less posts as compared to the amount of people that are there to look at the post and so the scalabitlity should happen only to make the sytem handle updating the peoples inboxes faster and more effective . 
	          here is what they do now .
          ![[Screenshot 2026-02-17 at 3.12.08 PM.png]]
7. Q. How do you describe performance in something like the data intensive stuff ? how do you know how effecient is the system and how well it can handle load ?
    ans. there are two things to keep in mind while doing this and these are a. while keeping the resorces the same and increasing the load how much is the **change in in the performance**  and b. how much resources are needed to **keep the performance unchanged** . 
8. Time latency percentile - the time latency percentile is a way of monitoring the working of the latency and to study the different patterns of the latency . its written in the percentile method as a way of stating how many people are either above or below the percentile provided something if you know the most time taken and you know the percentile of that you know how many people take more than that amount of time . ![[Screenshot 2026-02-17 at 11.55.18 PM.png]]
        1.  In this example of the percentile model you can see that you know the response time of the person that has the highest time taken as compared to all of the other people then you know that everyone else is lower than this and also that this is the person that has the biggest data heavy thing . 
        2. **Q**. **define tail latency** -- tail latency is the time taken by the highest percentile request or in other words this is the time taken by the 99th percentile person .
        3. how is this helpful ? 
        4. not only that it tells you about the i percent of the 1 percent of the time taken but it also tells you about how much time is of the 50 th percentile person and so on 
        5. 