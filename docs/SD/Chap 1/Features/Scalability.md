Scalability is the measure of how well a system responds to changes by adding or removing resources to meet demands.

![scalability](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/scalability/scalability.png)

Let's discuss different types of scaling:

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-vertical-scaling "Permalink")Vertical scaling

Vertical scaling (also known as scaling up) expands a system's scalability by adding more power to an existing machine. In other words, vertical scaling refers to improving an application's capability via increasing hardware capacity.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-advantages "Permalink")Advantages

- Simple to implement
- Easier to manage
- Data consistent

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-disadvantages "Permalink")Disadvantages

- Risk of high downtime
- Harder to upgrade
- Can be a single point of failure

## [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-horizontal-scaling "Permalink")Horizontal scaling

Horizontal scaling (also known as scaling out) expands a system's scale by adding more machines. It improves the performance of the server by adding more instances to the existing pool of servers, allowing the load to be distributed more evenly.

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-advantages "Permalink")Advantages

- Increased redundancy
- Better fault tolerance
- Flexible and efficient
- Easier to upgrade

### [](https://kps.hashnode.dev/system-design-the-complete-course?ref=dailydev#heading-disadvantages "Permalink")Disadvantages

- Increases complexity
- Data inconsistency
- Increased load on downstream services