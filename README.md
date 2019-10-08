# Cloud-Computing-and-Serverless-Architecture
Notes 
## 1. Key Conception
----------------------------------------------
| Conception | Definition | Link |
|----------------|--------------------------------------------------------------|----------------------|
|API	|Application Programming Interface, like the waitor connecting and communicating between customers and kitchen	| [YouTube](https://www.youtube.com/watch?v=s7wmiS2mSXY&list=LL5YPuNk4OqeQ1uHDlVNR0lQ&index=2&t=0s)	|
|FaaS	|Function-as-a-Service, a category of cloud computing services that provides a platform allowing customers to develop, run, and manage application functionalities without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app.	| [wiki](https://en.wikipedia.org/wiki/Function_as_a_service) and [medium](https://medium.com/@BoweiHan/an-introduction-to-serverless-and-faas-functions-as-a-service-fb5cec0417b2) |
|IaaS | Infrastructure-as-a-Service, online services that provide high-level APIs used to dereference various low-level details of underlying network infrastructure like physical computing resources, location, data partitioning, scaling, security, backup etc. A hypervisor, such as Xen, Oracle VirtualBox, Oracle VM, KVM, VMware ESX/ESXi, or Hyper-V, LXD, runs the virtual machines as guests. Pools of hypervisors within the cloud operational system can support large numbers of virtual machines and the ability to scale services up and down according to customers' varying requirements.|[wiki](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)|
| Pipeline | a set of data processing elements connected in series, where the output of one element is the input of the next one. |[wiki](https://en.wikipedia.org/wiki/Pipeline_(computing)) |
|Prefetch|Cache prefetching is a technique used by computer processors to boost execution performance by fetching instructions or data from their original storage in slower memory to a faster local memory before it is actually needed (hence the term 'prefetch')|[wiki](https://en.wikipedia.org/wiki/Cache_prefetching)|


## 2. Key Paper
----------------------------------------------
| Category | Name | Existing Method or System Challenge| Key Idea |
|----------------|-----------------------------------------|---------------------|----------------------|
| Serverless System | [SAND: Towards High-Performance Serverless Computing](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=SAND%3A+Towards+High-Performance+Serverless+Computing&btnG=) | 1. Long-latency: trade-off between 'cold start' and 'warm start'  <br> 2. Huge overhead Consumption | 1. lighter isolation for different functions under a same application;<br> 2. introduce local message bus|
|Serverless Machine learning | A Case for Serverless Machine Learning | wait | wait|

## 3. Key Conference Resources
 - [ACT2018](https://www.usenix.org/conference/atc18/technical-sessions)
 - [ACT2019](https://www.usenix.org/conference/atc19/technical-sessions)
