# MAC-SCHEDULER-UL-and-DL-

There is a finite set of time and frequency resources. These resources are dynamically allocated to the different connected devices (UE) that are accessing the 5G network, in such a manner that they will efficiently serve the network. This is known as shared channel transmission. The main function of scheduling is to decide which devices can use which time-frequency and antenna resources. Suppose there are three UE users and there is downlink data to be sent to these users. Then there should be a different amount of data that was supposed to be transmitted with these three devices and the priority was also different between the three devices. So, the scheduler takes the frequency resources and for each time slot, it will schedule where and how much data can be used by the device at a given time interval. This process will be done in the subsequent time slot by updating each slot for making the efficient allocation of resources between the devices.

There are different parameters on which scheduler make decisions, such as<br />
i) channel condition<br />
ii) buffer status<br />
iii) priority of data flow<br />

Scheduler controls the following things such as 

i) devices that are going to be transmitted or received in a given time slot<br />
ii) resource blocks that are going to be used by the devices<br />
iii) modulation, antenna resources, transport block size<br />
