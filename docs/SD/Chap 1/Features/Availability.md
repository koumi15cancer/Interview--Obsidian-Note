
Availability is the time a system remains operational to perform its required function in a specific period. It is a simple measure of the percentage of time that a system, service, or machine remains operational under normal conditions.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-the-nines-of-availability "Permalink")The Nine's of availability

Availability is often quantified by uptime (or downtime) as a percentage of time the service is available. It is generally measured in the number of 9s.

Availability=Uptime(Uptime+downtime)

If availability is 99.00% available, it is said to have "2 nines" of availability, and if it is 99.9%, it is called "3 nines", and so on.

|Availability %|Downtime (Year)|Downtime (Month)|Downtime (Week)|
|---|---|---|---|
|90% (one nine)|36.53 days|72 hours|16.8 hours|
|99% (two nines)|3.65 days|7.20 hours|1.68 hours|
|99.9% (three nines)|8.77 hours|43.8 minutes|10.1 minutes|
|99.99% (four nines)|52.6 minutes|4.32 minutes|1.01 minutes|
|99.999% (five nines)|5.25 minutes|25.9 seconds|6.05 seconds|
|99.9999% (six nines)|31.56 seconds|2.59 seconds|604.8 milliseconds|
|99.99999% (seven nines)|3.15 seconds|263 milliseconds|60.5 milliseconds|
|99.999999% (eight nines)|315.6 milliseconds|26.3 milliseconds|6 milliseconds|
|99.9999999% (nine nines)|31.6 milliseconds|2.6 milliseconds|0.6 milliseconds|

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-availability-in-sequence-vs-parallel "Permalink")Availability in Sequence vs Parallel

If a service consists of multiple components prone to failure, the service's overall availability depends on whether the components are in sequence or in parallel.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-sequence "Permalink")Sequence

Overall availability decreases when two components are in sequence.

Availability (Total)=Availability (Foo)∗Availability (Bar)

For example, if both `Foo` and `Bar` each had 99.9% availability, their total availability in sequence would be 99.8%.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-parallel "Permalink")Parallel

Overall availability increases when two components are in parallel.

Availability (Total)=1−(1−Availability (Foo))∗(1−Availability (Bar))

For example, if both `Foo` and `Bar` each had 99.9% availability, their total availability in parallel would be 99.9999%.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-availability-vs-reliability "Permalink")Availability vs Reliability

If a system is reliable, it is available. However, if it is available, it is not necessarily reliable. In other words, high reliability contributes to high availability, but it is possible to achieve high availability even with an unreliable system.

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-high-availability-vs-fault-tolerance "Permalink")High availability vs Fault Tolerance

Both high availability and fault tolerance apply to methods for providing high uptime levels. However, they accomplish the objective differently.

A fault-tolerant system has no service interruption but a significantly higher cost, while a highly available system has minimal service interruption. Fault-tolerance requires full hardware redundancy as if the main system fails, with no loss in uptime, another system should take over.