## TrainTicketWorkflows

This page shares resources from our work in the ICSE 2022 NIER Track, titled, 'A Case for Microservice Orchestration Using Workflow Engines'. The preprint of the artifact can be acessed through arxiv, using this link: https://arxiv.org/abs/2204.07210

This work was enabled due to the work by FudanSE lab in their research:-

X. Zhou et al., "Fault Analysis and Debugging of Microservice Systems: Industrial Survey, Benchmark System, and Empirical Study," in IEEE Transactions on Software Engineering, vol. 47, no. 2, pp. 243-260, 1 Feb. 2021, doi: 10.1109/TSE.2018.2887384.

### Microservices

Microservices are independant, losely coupled services that allow practitioners to divide their applications into independant units.

This independant microservices, can then:-
- Be developed by different teams
- Be deployed onto lightweight containers
- Scaled up and down as per requirement

However, despite of these benifits, adopting microservices have certain associated challenges.
- Microservices need to communicate over the network, through APIs, which is unreliable could become unresponsive at any given time.
- As the size of the microservice-architecture based application grows, these microservices become harder to manage.
- The size of application also makes the microservices harder to debug.

Therefore, it is important to make critical decisions, in a timely manner.

A contentious decision is to decide whether to compose microservices using Orchestration or Choreography.

- Microservice Orchestration works with an 'orchestrator' that cordinates all the interactions of the business process, in a flow.
- Choreography is more losely coupled, every microservice may generate events which direct another microservice to perform its job.

While choreography sounds more appealing,
- It makes debugging relatively hard, as control is embedded in process flows.
- Teams (ref: https://netflix.github.io/conductor/) argue, that there is no way to answer how much we are done with a process

In our work:-
- We map a bench mark system implemented using choreography, to a system that is orchestrated.
- We study the time taken by a user, to debug this orchestrated system
- We compare the time taken in the original bench mark system case study

The findings of our study did leave considerable proof that orchestration does have an impact on debugging time. Additionally, we find that utilization of frameworks can speed up the processes even more by reliving the developer of low-level distributed tasks.


## Environmental Set up

### Pre-reqs
- Docker
- Temporal server (https://github.com/temporalio/temporal)
- The Temporal-orchestrated version of TrainTicket system (https://github.com/ansnadeem/temporalmicroservice)  (5/8/2022: Work in progress due to reported set up issues)


### Steps to Set up
1) Ensure that the Temporal server is up and running (see temporal docs for reference)
2) Navigate to the system with the respective fault number from the package
3) Use 'docker-compose up' from command line to load the system

### Steps to replicate faults
After loading the environment with the respective fault, follow the steps from the original bench mark system, in order to replicate the fault.
Follow the repository below for a details of the fault:-
https://github.com/FudanSELab/train-ticket/wiki/Fault-Description
