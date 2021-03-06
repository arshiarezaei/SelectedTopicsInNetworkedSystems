## Background
  1. [Survey of Consistent Software-Defined Network Updates](https://ieeexplore.ieee.org/document/8500100)


## Survey Papers
  1. [Survey of Consistent Software-Defined Network Updates](https://ieeexplore.ieee.org/document/8500100)


## Related works
  1. [Achieving High Utilization with Software-Driven WAN](https://dl.acm.org/doi/abs/10.1145/2486001.2486012) [PDF](https://dl.acm.org/doi/pdf/10.1145/2486001.2486012) <!-- ,[Summary](summaries/Achieving_High_Utilization_with_Software-Driven_WAN.md) -->
  2. [ReversePTP: A clock synchronization scheme for software‐defined networks](https://onlinelibrary.wiley.com/doi/10.1002/nem.1942)
  3. [ReversePTP: A Software Defined Networking Approach to Clock Synchronization](https://dl.acm.org/doi/10.1145/2620728.2620764), [PDF](https://dl.acm.org/doi/pdf/10.1145/2620728.2620764)
  4. [Software defined networks: It's about time](https://ieeexplore.ieee.org/document/7524418) [technical report](https://arxiv.org/pdf/1505.03421.pdf)
  5. [Dynamic Scheduling of Network Updates](https://dl.acm.org/doi/10.1145/2740070.2626307), [PDF](https://dl.acm.org/doi/pdf/10.1145/2740070.2626307?casa_token=E2ajcxVkElIAAAAA:gmOgIACyHqQiqAKQRVejbP1K_37KreR4_TyuzYMTCH-P0M_GdNYnz7-K6x0YCF9Ns_SWFaE26VMp), [extended version](papers/SIGCOMM14_Dionysus_extended.pdf), [Slides](slides/SIGCOMM14_Dionysus_slides.pptx)
  6. [Cupid: Congestion-free Consistent Data Plane Update In Software Defined Networks](https://ieeexplore.ieee.org/document/7524420)
  7. [Update Algebra: Toward Continuous, Non-Blocking Composition of Network Updates in SDN](https://ieeexplore.ieee.org/document/8737618)
  8. [Coeus: Consistent and Continuous Network Update in Software-Defined Networks](https://ieeexplore.ieee.org/document/9155392)



  ## Summary of major works in network update problem in SDN <br>



  No.|Year|Description|Advantage|Limitation| Summary | Evaluation Results |
  -|:------:|:--------------------------------:|:-------------:|:--------: |:---------:|:----:|
  1|2018|[Survey of Consistent Software-Defined Network Updates](https://ieeexplore.ieee.org/document/8500100/)| - | - | a survey and comparison of works of Consistent network update in SDN | -
  2| 2013 | [Achieving high utilization with software-driven wan](https://dl.acm.org/doi/pdf/10.1145/2486001.2486012) | Minimizes number of communication rounds between the controller and switches | Does not optimize within update rounds, makes no assumption for timing of updates and runtime differences | Leverages the link slack capacity (s) to perform update in multiple rounds, e.g., s=10% (0.1) ==> ceil(1/0.1)-1=9 rounds of update.
  3|2014|[ReversePTP: A clock synchronization scheme for software‐defined networks](https://onlinelibrary.wiley.com/doi/10.1002/nem.1942), [ReversePTP](https://dl.acm.org/doi/pdf/10.1145/2620728.2620764)| Eliminates message passing between Switches In PTP| Overhead in the controller causes from running many instances of the Slave algorithms (I am not sure)|The direction of clocks are from switches (masters) to Controller (Slave).| # of messages per second is twice comparing with PTP. No significant CPU utilization difference between PTP and REVERSEPTP.
  4|2016|[Software Defined Networks: It's About Time](https://ieeexplore.ieee.org/document/7524418), [technical report](https://arxiv.org/pdf/1505.03421.pdf)| Open Source, fast| Can't preserve per-packet consistency and congestion avoidance. Huge packet loss|  - | #Of switches does not affect Packet loss. Packet loss is greater than B4 and SWAN. Time4+B4 and Time4+SWAN (hybrid mode) result the same level of packet loss comparing with SWAN & B4.
  5|2014|**[Dynamic Scheduling of Network Updates](https://xinjin.github.io/files/SIGCOMM14_Dionysus.pdf)**, [Slides](https://xinjin.github.io/files/SIGCOMM14_Dionysus_slides.pptx)| Leverages runtime differences among switches to perform fast and Consistent update | It is not congestion-free | Multiple ordering of operations may exist for the same network update, Dionysus uses runtime properties of the switches to perform fast network update.  | Dionysus was compared with SWAN and OneShot. Dionysus has less over subscription and update time than SWAN and acts better in failure recovery.
  6 | 2016 | [Cupid: Congestion-free Consistent Data Plane Update In Software Defined Networks](https://ieeexplore.ieee.org/document/7524420)| Speeds up the network update by dividing the flow path into multiple segments| Can not preserve per-packet consistency. The flow path segmentation algorithm does not work well when migration from old to new path has excessive loops.| Introduces a flow path segmentation algorithm| Faster than [Dionysus](https://xinjin.github.io/files/SIGCOMM14_Dionysus.pdf). It seems the segmentation algorithm does not produce maximum number of segments (fig 7).
  7 | 2019 | **[Update Algebra: Toward Continuous, Non-Blocking Composition of Network Updates in SDN](https://ieeexplore.ieee.org/document/8737618)**| Introduces continuous network update, i.e., executing updates as they arrive. | Does not guarantee congestion-free update. The notion of the framework is complicated. |Merges unexecuted operations with the operations of the newly arrived update to change the network forwarding state from the current state to the target state.| Reduces update time and number of update operations.
  8 | 2020 | [Coeus: Consistent and Continuous Network Update in Software-Defined Networks](https://ieeexplore.ieee.org/document/9155392)| Partitions the flow path into multiple segments. Performs continuous and consistent network update. | Constant switch update time (does not consider runtime differences) | Partitioning algorithm is based on [Cupid](https://ieeexplore.ieee.org/document/7524420)| Less update time and executed operations than [Cupid](https://ieeexplore.ieee.org/document/7524420).
