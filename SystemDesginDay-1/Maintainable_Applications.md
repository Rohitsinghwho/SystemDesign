
# Reliable, Scalable and Maintainable Applications

## what is system design or designing a system ?
```
There are many tools like redis , mongo, postgres , aws etc. They all have different access patterns , different implemntation, different use case, different characterstics. But to develop a application all of those works as one unit. Figuring out which tool or access pattern or performance is best for our application according to the constraints is know is system design.

Also there are tools which have some similarities, for ex redis can be used as a data store and a messaging queue , kafka is messaging queue with database like durability guarantees.So when to use which is what system design is.

```

## Reliability

Reliability menas the system should continue to work correctly(correctly can mean a lot here) even when things go wrong.
The things that can go wrong are called <strong>Fault,</strong> and systems that can anticapte faults and can cope with them are called <strong>fault-tolerant or resilient.</strong>

<strong>Fault-tolerant</strong> systems does not mean we can tolerate every possible kind of faults, which in reality is not feasible.

### Difference between fault and failure.

- fault is when the component deviates from its spec(component behaves incorrectly).
- failure is when a system as a whole stops providing the required service to the user.for example User gets 500 Internal Server Error.


It is impossible to reduce the probability of fault to zero, therefore it is usually best to design for fault tolerance mechanisms that prevents faults from causing failures. for example
A fault occured in the database out of memory condition occurs now the database stops providing its intended service(which is a system level failure) and now application layer cannot access the database(application level failure) all caused from the fault in the database component. So that is what we do not want to do, we want to stop failures caused by the fault.



Prevention is better than cure, for example netflix used monkey chaos to randomly shut down there components in random availibiltiy zones and make sures there system can tolerate the failures.

### Hardware Fault

A hardware fault is when some physical component stops working correctly.For example hard disk dies, RAM becomes faulty, power goes out, CPU fails, server motherboard failed.

The more components you have, the more likely something will be failing at any given time.

#### Traditional approach(component level redundancy)

if hardware fails, lets make the hardware more reliable. so instead of a single disk lets have more disks with redundancy, for server(machine) keep additional power supply so basically keep other component available to take over when one component fails.
But the limitation was , what if the whole machine(server) dies ? then indiviual reduandant hardware components cannot save us. so we need machine level redundancy.


#### Machine level redundancy 

Now we have more servers , for example we have server A , server B ...server N. And a load balancer routes request to them. So if now the machine dies we have additional machine which can server the user and perform the intended task. That is called <strong>fault tolerance</strong>.
So modern distributed approach's goal is to survive the loss of a machine and that is <strong>software fault tolerance.</strong> 


The thing is that the more servers or machines we have the more hardware faults increase, so we should always design for them.

Another thing is maintenance. suppose we have a single server and we want to install a security patch now we only have single server so the user will experince downtime meanwhile we install the patch. But if we have multiple machines we can install patch on them one by one and meanwhile the user can interact with a same different machine. That is <strong>rolling deployment.</strong>






















