# Cloud-Computing-and-Serverless-Architecture
Notes 
## 1. Key Conception and Platform

### 1.1 Key Conception
----------------------------------------------
| Conception | Definition | Link |
|----------------|--------------------------------------------------------------|----------------------|
|API	|Application Programming Interface, like the waitor connecting and communicating between customers and kitchen	| [YouTube](https://www.youtube.com/watch?v=s7wmiS2mSXY&list=LL5YPuNk4OqeQ1uHDlVNR0lQ&index=2&t=0s)	|
|FaaS	|Function-as-a-Service, a category of cloud computing services that provides a platform allowing customers to develop, run, and manage application functionalities without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app.	| [wiki](https://en.wikipedia.org/wiki/Function_as_a_service) and [medium](https://medium.com/@BoweiHan/an-introduction-to-serverless-and-faas-functions-as-a-service-fb5cec0417b2) |
|IaaS | Infrastructure-as-a-Service, online services that provide high-level APIs used to dereference various low-level details of underlying network infrastructure like physical computing resources, location, data partitioning, scaling, security, backup etc. A hypervisor, such as Xen, Oracle VirtualBox, Oracle VM, KVM, VMware ESX/ESXi, or Hyper-V, LXD, runs the virtual machines as guests. Pools of hypervisors within the cloud operational system can support large numbers of virtual machines and the ability to scale services up and down according to customers' varying requirements.|[wiki](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)|
|parameter server|A parameter server is a shared, multi-variate dictionary that is accessible via network APIs. Nodes use this server to store and retrieve parameters at runtime. As it is not designed for high-performance, it is best used for static, non-binary data such as configuration parameters. It is meant to be globally viewable so that tools can easily inspect the configuration state of the system and modify if necessary.|[wiki](http://wiki.ros.org/Parameter%20Server), [medium](https://medium.com/coinmonks/parameter-server-for-distributed-machine-learning-fd79d99f84c3) and [paper](http://www.cs.cmu.edu/~muli/file/parameter_server_osdi14.pdf)|
| Pipeline | a set of data processing elements connected in series, where the output of one element is the input of the next one. |[wiki](https://en.wikipedia.org/wiki/Pipeline_(computing)) |
|Prefetch|Cache prefetching is a technique used by computer processors to boost execution performance by fetching instructions or data from their original storage in slower memory to a faster local memory before it is actually needed (hence the term 'prefetch')|[wiki](https://en.wikipedia.org/wiki/Cache_prefetching)|
|runtime|can be understood as **'runtime'**: In computer science, run time, runtime or execution time is the time during which a program is running (executing), in contrast to other program lifecycle phases such as compile time, link time and load time.| [wiki](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase))|

### 1.2 Major Platform

#### AWS Lambda
(1) Key Feature & Facts
- Can be triggered by different events (e.g. HTTP request)
- Automatically scaled, stateless, fault-tolerant
- Basically all you neeed to start is to upload your function code to the cloud (AWS S3 Bucket)
- Function Code and its dependencies should'd be greater than 250MB (deployment package .zip file)
- Runs on Amazon Linux OS, inside a runtime container
- It should be "warmed" - cold start vs. warm start

(2) Components
- **AWS Lambda**: Executes function code
- **AWS S3**: Stores trained ML Model; Stores Lamnda function code
- **Amazon API Gateway**: Accepts HTTP request; Formats HTTP response
![alt text](https://github.com/bonaldli/Cloud-Computing-and-Serverless-Architecture/blob/master/figs/AWS%20ML.png)
- **Boto3**: Boto3 is the Amazon Web Services (AWS) Software Development Kit (SDK) for Python, which allows Python developers to write software that makes use of services like Amazon S3 and Amazon EC2. [Github](https://github.com/boto/boto3)

## 2. Key Paper
----------------------------------------------
| Category | Name | Existing Method or System Challenge| Key Idea |
|----------------|-----------------------------------------|---------------------|----------------------|
| Serverless System | [SAND: Towards High-Performance Serverless Computing](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=SAND%3A+Towards+High-Performance+Serverless+Computing&btnG=) | 1. Long-latency: trade-off between 'cold start' and 'warm start'  <br> 2. Huge overhead Consumption | 1. lighter isolation for different functions under a same application;<br> 2. introduce local message bus|
|Serverless Machine learning | A Case for Serverless Machine Learning | wait | wait|
|Serverless Machine Learning (Inference) | [MArk: Exploiting Cloud Services for Cost-Effective, SLO-Aware Machine Learning Inference Serving](https://www.cse.ust.hk/~weiwa/papers/mark-atc19.pdf)| Provision for inference (perform in real-time on dynamic queries), hard yo actualize low-latency, cost-effective inference at scale| IaaS (High performance-cost ratio) for predictive work load, FaaS (High Scalability) for unpredicted load spikes|
-------------------------------
Paper Mindmap: http://www.xmind.net/m/ZDEpEa
## 3. Key Conference Resources
 - [ACT2018](https://www.usenix.org/conference/atc18/technical-sessions)
 - [ACT2019](https://www.usenix.org/conference/atc19/technical-sessions)

## 4. Experiments based on AWS and Bell Labs 
### 4.1 Introductionary Examples
|Platform|Included Functions|Link|
|--|--|--|
|AWS|(1) hello<br>(2) palindrome<br>(3) basicmath | [click](https://eu-central-1.console.aws.amazon.com/lambda/home?region=eu-central-1#/functions)|

### 4.2 Function Flows
(1) How to define the workflow: [AWS Lambda and Step Function](https://aws.amazon.com/getting-started/tutorials/create-a-serverless-workflow-step-functions-lambda/).

(2) The [states](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-states.html) in AWS Step Functions: Pass, Task, Choice, Wait, Succeed, Fail, Parallel, Map

(3) Workflow Examples: 

|Name|Workflow|Structure|Platform|link|
|----|--------|---------|--------|----|
|one_fourth| numberx0.5x0.5 |![alt text](https://github.com/bonaldli/Cloud-Computing-and-Serverless-Architecture/blob/master/figs/one_fourth.jpg?raw=true)|Bell Labs Microfunction| [value="10"](https://sand-1.cloud.brlab.nsn-rdnet.net/workflow/d3275b8e415b5248d347fb7e1f2db1e9/ef7ce47c6321ec7d04b5fdf2fe2ade06/first_half?value=)|
|data_tansmission| data: data layer--> F1 --> F2 | image | Bell Labs Microfunction | N/A |

### 4.3 Serverless Machine Learning Examples
| name | platform | mechanism | link |
|------|----------|-----------|------|
| serverless machine learning inference | AWS | tba | [medium](https://medium.com/merapar/pure-serverless-machine-learning-inference-with-aws-lambda-and-layers-979702d9ae49) |
| serverless ML training & model | google cloud | tba | [codelabs](https://codelabs.developers.google.com/codelabs/dataeng-machine-learning/index.html?index=..%2F..index#0)|
|deep learning model with AWS lambda | AWS | tba | [AWS](https://aws.amazon.com/blogs/machine-learning/how-to-deploy-deep-learning-models-with-aws-lambda-and-tensorflow/) |
| \[Udemy] Deploy Serverless Machine Learning Models to AWS Lambda | AWS | (1) Virtual Box <br> (2) Ubuntu <br> (3)AWS IAM |no|
| Concurrency | AWS | tba | [amazon](https://aws.amazon.com/blogs/compute/managing-aws-lambda-function-concurrency/)|
| California Housing Price Prediction | AWS and SAND | locally trained model + inference | tba |
| NLP Text Contextual Learning | AWS and SAND | locally trained model + inference | tba |

### 4.4 Performance Measurement and Profiling
| Metrics | Explanation | Details |
|---------|-------------|---------|
| Latency | how long (ms or s) does it take | ```import time``` <br> ```timestamp = int(time.time())``` <br> ```print(f'it takes {timestamp}')``` |
| CPU Info | the hardware provisioning | ```pip install py-cpuinfo # in anaconda prompt```, see in [github](https://pypi.org/project/py-cpuinfo/) <br> ```from cpuinfo import get_cpu_info``` <br> ```for key, value in get_cpu_info().items():``` <br>```    print("{0}: {1}".format(key, value))```|


## Reference Articles
(1) [Content Replication Using AWS Lambda and Amazon S3](https://aws.amazon.com/blogs/compute/content-replication-using-aws-lambda-and-amazon-s3/)<br>
(2) [Passing data between Lambdas with AWS Step Functions](https://medium.com/@tturnbull/passing-data-between-lambdas-with-aws-step-functions-6f8d45f717c3)<br>
(3) [AWS Lambda with Pandas and NumPy](https://medium.com/@korniichuk/lambda-with-pandas-fd81aa2ff25e)



