

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
         # The twitter problem and its solution 
        **key players** -  the person who post something - " **tweeter  " and the person who recieves the post -" the **tweete**" and the things that got posted - " **the tweet** "
        **early approach** -- a tweeter posts a tweet and the tweet goes to the main database that contains all the tweets and and followers of that person fetches the tweets from the global database and sorts them with respect to the time at which they have posted the tweet.- this is the relational database method 
        
         the problem - the main worker in this method is the tweeter timeline               feed software meaning it is the key player in the working of this                system it checks the whole database and then sorts all of the tweets              everytime you refresh .and the readers are way way more than the                  people who are posting so it became a hastle .
         
         the solution - the solution was the every user will have a cashe for              their timeline and from the sender all of his tweets will be send to               the cashe of all of his followers this way the method become form                reciever heavy to sender heavy . as the amount of reciever are far                more than the sender .
         
         ## The "Lady Gaga" Problem (The Hybrid Model)

     The "Push" model works beautifully for most of us, but it breaks when you have accounts with tens of millions of followers. If a celebrity tweets, the system has to update 50+ million caches instantly, which creates a massive spike in lag.

    **The Solution:** Twitter uses a **hybrid approach**.

     1. **For regular users:** They use the **Push Model** (Approach 2). Your tweets are pushed to your friends' feeds.
    
     2. **For celebrities:** They use the **Pull Model** (Approach 1). Their tweets aren't pushed. Instead, when you load your feed, the system fetches the celebrity’s tweets separately and merges them into your timeline.

 .   3. Q. How do you describe performance in something like the data intensive stuff ? how do you know how effecient is the system and how well it can handle load ?
    ans. there are two things to keep in mind while doing this and these are a. while keeping the resorces the same and increasing the load how much is the **change in in the performance**  and b. how much resources are needed to **keep the performance unchanged** . 
4. Time latency percentile - the time latency percentile is a way of monitoring the working of the latency and to study the different patterns of the latency . its written in the percentile method as a way of stating how many processes are either above or below the percentile provided something if you know the most time taken and you know the percentile of that you know how many people take more than that amount of time . ![[Screenshot 2026-02-17 at 11.55.18 PM.png]]
        1.  In this example of the percentile model you can see that you know the response time of the person that has the highest time taken as compared to all of the other people then you know that everyone else is lower than this and also that this is the person that has the biggest data heavy thing . 
        2. **Q**. **define tail latency** -- tail latency is the time taken by the highest percentile request or in other words this is the time taken by the 99th percentile person .
        3. how is this helpful ? 
        4. not only that it tells you about the i percent of the 1 percent of the time taken but it also tells you about how much time is of the 50 th percentile person and so on 
        5. the tail latency also helps us make aggreements something like one person can write in the contract like the latency should be under 200 ms ( average ) and the 99th percentile should have latency less than 1s and that its should be maintained .
        6. **Q. define the term** -- **tail latency amplification** -- if there is a request queue and there is a request that has a high tail latency for that user something that has data then because of that all the other requests can get slower or are answered with delay because of that first or bigger request .
        7. this is the AI summary if problems arrise in comprehention -```
     Great question. Kleppmann emphasizes **percentiles** because, in the world of data-intensive systems, "averages" are almost always a lie.

      If you have an average response time of 200ms, it sounds great—until you realize that 10% of your users are waiting 30 seconds and staring at a loading spinner.

---

           ## Why "Average" is Misleading

        In engineering, we usually see a **Long Tail** distribution of latency.         Most requests are fast, but a few are very slow due to background                 processes, network hiccups, or "garbage collection" in the code.

         - **The Mean (Average):** If you have 9 people getting their data in             100ms and 1 person getting it in 10 seconds, the "average" is about 1            second. That 1 second doesn't represent _anyone's_ actual experience.
    
        - **The Median (p50):** This is the halfway point. If your p50 is 100ms, it means exactly 50% of your requests are faster than 100ms, and 50% are slower.
    

---

## The "Tail Latencies" (p95, p99, and p99.9)

To understand the experience of the users who are actually having a bad time, we use high percentiles.

- **p95 (95th Percentile):** 95% of requests are faster than this. If your p95 is 500ms, 1 out of every 20 users is experiencing a delay longer than half a second.
    
- **p99 (99th Percentile):** This is the standard for "good" performance. Only 1 in 100 requests is slower than this value.
    
- **p99.9 (The "Three Nines"):** This targets the slowest 1 in 1,000 requests.
    

---

## Why should we care about the 1%?

You might think, "If 99% of people are happy, why worry about the last 1%?" Kleppmann points out a few critical business reasons:

1. **The "Big Spenders":** Often, the users with the most data (like a customer who has made thousands of purchases) are the ones who trigger the slowest responses because their requests are the most complex. You don't want to frustrate your most valuable customers.
    
2. **Chained Requests:** If one webpage needs to make 100 different API calls to load, and each call has a 1% chance of being slow (p99), then statistically, **most users** will experience a slow page load because they are likely to hit at least one of those slow "tail" requests.
    

---

## Summary Table

|**Metric**|**What it tells you**|
|---|---|
|**Median (p50)**|The "typical" user experience.|
|**p95 / p99**|The "tail latency"—how bad it gets for the unlucky few.|
|**p99.9**|Often used for Service Level Objectives (SLOs) in high-scale systems (like Amazon).|

A common mistake is thinking you can average percentiles together (e.g., averaging the p95 of two different servers). **You can't.** To get an accurate percentile across a whole cluster, you need to look at the raw distribution of all response times.

Would you like to see how these percentiles relate to **SLAs (Service Level Agreements)**, or perhaps look at how "head-of-line blocking" creates these slow tails?




Chapter 2
- every data engeneer deal with the lower level of abstraction like an application dev deals with the file system like json or xml and the even lower engineer deals with the lower level of abstraction like hardware and so on .
- my sql is widely used from the mid 1980s and its often sited as the best database for the general use , its a relational database and it is basically just a table with columns and rows that you can search from and use .
- no sql is another form of database model that is used as contrary to the standard sql model and that is basically just json file being spitted out when we query . 