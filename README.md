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

### DOWNLINK SCHEDULING

Here, the scheduler is located at the RAN. To make it work, it first needs to understand how the channel looks for the devices. So, the scheduler gets feedback on the channel state information(CSI) from the device, to decide on the scheduling. Second, it also gets buffer status from the different RLC buffers which gives brief information about how much data is left to send. Then using this information, the scheduler decides what should be the time slot and what modulation and coding the scheduled data are going to use. 

The device needs some referencing signal to measure the channel condition. For that purpose, the RAN transmits, CSI-RS or channel state information reference signal. RAN also transmits the SSB or synchronization signal block, which is used when the device is entering for the first time in the coverage area i.e. initial access. Either device can use CSI-RS or SSB to measure the channel condition. It measured the received signal power (RSPR), that the UE received from the RAN. This provides information related to the signal strength. 

The other information it measures is CSI. It includes a few different information such as measures the channel quality (CQI), precoding metrics indicator for deciding which preprocessing to be used for multiple antenna systems, rank indicators to measure the amount of data stream that can receive in parallel for the given precoding metrics indicator. These parameters are going to measure on either CSR-RS or SSB. 

There are different scenarios when the devices will measure the channel condition as follows<br />
a) periodic measurement <br />
b) aperiodic measurement <br />
c) semi-persistent measurement <br />

**i) Dynamic scheduling**

(In the context of message exchange)

In this scenario, the device is monitoring the control channel to check whether there was data it has to receive or not. While downlink-data, the scheduler at RAN will indicate using Downlink control information (DCI), which is a part of PDCCH which indicates the UE to fetch the data that it has to be received and the other resources. Now the actual data is communicated through PDSCH or a physical downlink shared channel. Or the device can read the actual data from the PDSCH. This scheduling happens whenever it's necessary and is known as dynamic scheduling.

ii) Configured Scheduling

(In the context of message exchange)

For low latency devices, configured scheduling is used and it has a mechanism known as semi-persistent scheduling or SPS. Let us take an example of a robot. In this scenario, the remote control information is reaching the robot very frequently. And the resources are scheduled with a certain time interval or periodicity. In every millisecond, the information was supposed to go from the remote control to the robot. In this case, it will send the downlink control information or DCI every time because it repeats itself frequently.

First, the periodicity should be defined for the device. After that, the device looks periodicity which is now activated and ready to receive the information periodically. Now in subsequent transmission, there is no control information transmission taking place. After that, when there is no periodic data to be sent then the periodicity gets deactivated by sending the information through DCI. So when there is the periodic transmission of control information with the feature of activating and deactivating whenever necessary is known as semi-persistent scheduling.
