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

### UPLINK SCHEDULING

Here, the scheduler was again located at the RAN. For the uplink, it needs to know the channel characteristic. For that purpose, the device starts transmitting the reference signal. So based on this reference signal, the channel quality can be estimated by the RAN. In the uplink, the UE knows the buffer status, so it was shared with the RAN. First, based on this information, the RAN scheduler will send the scheduling information to the various devices. It contains information about the device's transmission timing and the resources that the device can use for transmission.

This scheduling information is known as schedule grants. In Uplink, the device uses a reference signal known as SRS or sounding reference signal. It was sent during the uplink by different devices. Based on the information coming from SRS, the RAN can estimate the channel quality. It will make the decision based on the SRS information. In SRS, it can support 4 antenna ports while during downlink, the CSI-RS use up to 30 antenna port. 

**i) Dynamic scheduling**

The device will send the scheduling request having the information that the uplink data to be shared with the RAN. After that, the RAN provides the scheduling grant (which we have discussed previously) to the device. Now, after receiving the scheduling grant the device will send the uplink data through the PUSCH by utilizing the resources allocated for this particular transmission. After that, if there is a needs to send more uplink data, then the device will reallocate all the resources for uplink transmission. 

**ii) Configured scheduling**

**Type 1**

In starting step, on getting the scheduling requests, the RAN sends the scheduling grants with periodicity. Therefore, the device in this case can send the uplink data frequently for a given periodic time interval. When the transmission is complete, the RAN will send a scheduling grant to stop the periodic transmission.

**Type 2**

It is also known as Semi-Persistent Scheduling. Here also the periodicity is defined. After that, the set of information is sent to the device using the DCI, which will help in activating and deactivating the periodicity. When it is activated, the device can transmit the data send and in the subsequent transmission is not required to send the DCI. After that when the uplink data is sent successfully. Then the RAN send the information to stop or deactivate the periodicity through the DCI. 

So in type 1, when there is a need to do periodicity again then it has to reconfigure it again. While in type 2, the previous configuration is kept. Due to this they only need to activate or deactivate the periodicity without reconfiguring it again.
