# SelectedTopicsInNetworkedSystems

## Summary of major works in network update problem in SDN <br>
<span style="color:red"> Over one year, I worked on the network update problem in SDN.
I created multiple tables to compare works in that field in a private repository.
Now, I am trying to merge the tables and make them public.
Possibly, there are some mistakes until completion. </span> <br>

No.|Year|Description|Advantage|Limitation| Summary | Evaluation Results |
-|:------:|:--------------------------------:|:-------------:|:--------: |:---------:|:----:|
1|2018|[Survey of Consistent Software-Defined Network Updates](RelatedWork/2019-Survey-.pdf)| - | - | - | -
2|2014|[ReversePTP](RelatedWork/reverseptp.pdf)| eliminates message passing between Switches| ?|direction of clocks are from switches (masters) to Controller (Slave).  [ReversePTP-HOTSDN](RelatedWork/2014-HotSDN-ReversePTP.pdf) | # of messages per second is twice in comparison with PTP. No significant CPU utilization difference between PTP and REVERSEPTP.
3|2016|[Software Defined Networks: It's About Time](RelatedWork/Software Defined Networks It's About Time.pdf)| Open Source, fast| can't preserve per-packet consistency and congestion avoidance. links have equal latency|  presents flow swaps, lossless flow Allocation problem, Time4 | #Of switches does not affect Packet loss. packet loss is greater than B4 and SWAN. Time4+B4 and Time4+SWAN (hybrid mode) result in the same level of packet loss in comparison with SWAN & B4.[technical report](RelatedWork/ time 4 time for SDN.pdf)
4|2014|**[Dynamic Scheduling of Network Updates](RelatedWork/2014-SIGCOMM_Dionysus.pdf)**|considers runtime properties | is not congestion-free |[Slides](Presentation/2014_SIGCOMM-Dionysus.pptx) | Dionysus was compared with SWAN and OneShot. Dionysus has less oversubscription and update-time than SWAN. acts better in failure recovery
5 | 2020 | **[Coeus: Consistent and Continuous Network Update in Software-Defined Networks](RelatedWork/Coeus.pdf)**| eliminates redundant operations in Continuous update events. blackhole-, loop- and congestion-free  | constant switch update time | based on [Update Algebra](RelatedWork/update algebra.pdf), strives to update the network in a congestion-free manner. | Less maximum link utilization than "Update Algebra". less update time and changed roles than Cupid.
6 | 2018 | [Update Algebra: Toward Continuous, Non-Blocking Composition of Network Updates in SDN](RelatedWork/update algebra.pdf)| introduces continuous updates || does not guarantee congestion-free update | reduced update time, reduced number of command sent to switches
7 | 2016 | [Cupid: Congestion-free Consistent Data Plane Update In Software Defined Networks](RelatedWork/cupid.pdf). [INFOCOM 2016]
8 | 2014 | [ESPRES Transparent SDN Update Scheduling](RelatedWork/ESPRES_Transparent_SDN_Upate_Scheduling_2014_EN.pdf).[Presentation](Presentation/ESPRES Transparent SDN Update Scheduling.pdf) [HotSDN 2014]
