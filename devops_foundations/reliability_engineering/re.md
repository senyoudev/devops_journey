## Engineering doesn't end with deployment

In simple terms, "Engineering Doesn't End with Deployment" means that the job of software development and system maintenance doesn't finish once the code is deployed and running in production. Instead, it emphasizes that there's ongoing work and responsibility involved in maintaining, monitoring, and improving the software even after it's live.

### Why it's Important:

- **Maintenance**: Software needs to be regularly updated and patched to fix bugs, address security vulnerabilities, and incorporate new features or improvements.

- **Monitoring**: Continuous monitoring of the deployed software is crucial to ensure it performs as expected, detect and address any issues or failures promptly, and optimize performance.

- **Feedback**: It's essential to gather feedback from users and stakeholders to identify areas for improvement, address usability issues, and prioritize feature requests or bug fixes.


## Design for operation : Theory

When discussing operations, it's crucial to understand that success in production stems from decisions made early in the development pipeline. Designing your application to function effectively even in adverse conditions is key. This involves considering software architecture and stability patterns.

**Software Architecture**:
Traditional design patterns (like those in the Gang of Four book) are valuable, but for stability, consider Michael Nygard's "Release It." This book delves into understanding failure causes, patterns, and techniques to make applications resistant to failures.

Integration points are a significant source of issues in architectures. Cascading failures, triggered by issues with integration points, are a primary threat to stability.

**Stability Patterns**:
One example is the "circuit breaker" pattern, which detects failures when calling integration points and stops making calls if an unusual number of failures occur. This prevents spreading outages.

Netflix's Hystrix library is an example of implementing the circuit breaker pattern. It wraps calls to integration points, providing automatic circuit breaker functionality.

**12 Factor App**:
The "12 factor app" manifesto provides guidelines for producing service-ready software. Separating runtime configuration from app code and storing it in environment variables improves portability and avoids fragility.

I. Codebase
One codebase tracked in revision control, many deploys
II. Dependencies
Explicitly declare and isolate dependencies
III. Config
Store config in the environment
IV. Backing services
Treat backing services as attached resources
V. Build, release, run
Strictly separate build and run stages
VI. Processes
Execute the app as one or more stateless processes
VII. Port binding
Export services via port binding
VIII. Concurrency
Scale out via the process model
IX. Disposability
Maximize robustness with fast startup and graceful shutdown
X. Dev/prod parity
Keep development, staging, and production as similar as possible
XI. Logs
Treat logs as event streams
XII. Admin processes
Run admin/management tasks as one-off processes


## Design for operation : Practice


### Embracing Failure:

- Acknowledge that all systems fail; relying solely on highly available systems without planning for failure is ineffective.

- Deliberate adversity, exemplified by tools like Chaos Monkey, challenges assumptions about system reliability and drives innovative approaches to design.

### Designing for Resilience:

- Implement deliberate adversity practices to build resilient systems, such as replicating data and services to mitigate single points of failure.

- Emphasize the importance of operational processes that minimize dependencies and maintain functionality even when components fail.

### Performance Considerations:

- Performance is heavily influenced by code quality and design decisions rather than hardware alone.

- Prioritize code optimization over hardware upgrades to improve performance and resource utilization.

### Performance Testing and Profiling:

- Utilize performance testing and profiling tools during development to identify and address performance bottlenecks.

- Application Performance Management (APM) tools provide insights into system-wide performance and facilitate proactive monitoring and troubleshooting.

### Maintenance and Monitoring:

- Incorporate monitoring, metrics, and logging as first-order requirements during system design and implementation.

- Plan and implement maintenance processes upfront to ensure long-term system health and stability.

Incorporating operational expertise into the development phase and designing for performance and availability from the beginning are essential for building robust and maintainable systems.

## SRE (Site Reliability Engineering) Toolchain

Site Reliability Engineering (SRE) is a discipline that applies software engineering principles to the operations and maintenance of large-scale, distributed systems. The SRE toolchain comprises a set of tools and practices aimed at achieving reliability, scalability, and efficiency in managing complex infrastructure and services.

### 1. Monitoring and Alerting:

- **Tool**: Prometheus
  - **Description**: Prometheus is an open-source monitoring and alerting toolkit designed for reliability and scalability. It collects metrics from monitored targets, stores them in a time-series database, and provides flexible querying and alerting capabilities.

### 2. Incident Management:

- **Tool**: PagerDuty
  - **Description**: PagerDuty is an incident management platform that centralizes alerts from monitoring tools, notifies on-call responders, and facilitates collaboration and resolution of incidents through automated workflows and communication channels.

### 3. Automation and Orchestration:

- **Tool**: Kubernetes
  - **Description**: Kubernetes is an open-source container orchestration platform that automates deployment, scaling, and management of containerized applications. It provides features for service discovery, load balancing, and resource allocation, improving reliability and scalability.

### 4. Logging and Log Management:

- **Tool**: ELK Stack (Elasticsearch, Logstash, Kibana)
  - **Description**: ELK Stack is a popular open-source log management solution. Elasticsearch stores and indexes log data, Logstash collects and processes logs from various sources, and Kibana provides visualization and analysis capabilities for log data.

### 5. Configuration Management:

- **Tool**: Ansible
  - **Description**: Ansible is an open-source automation tool used for configuration management, application deployment, and orchestration. It allows infrastructure as code (IaC) practices, ensuring consistency and reliability in managing infrastructure configuration.

### 6. Continuous Integration and Deployment (CI/CD):

- **Tool**: Jenkins
  - **Description**: Jenkins is an open-source automation server used for building, testing, and deploying software projects continuously. It integrates with version control systems, automates CI/CD pipelines, and facilitates collaboration among development and operations teams.

### 7. Performance Monitoring and Optimization:

- **Tool**: New Relic
  - **Description**: New Relic is a performance monitoring and optimization platform for web applications, mobile apps, and infrastructure. It provides real-time insights into application performance, identifies bottlenecks, and helps optimize resource usage for improved reliability and scalability.

### 8. Incident Analysis and Postmortems:

- **Tool**: Honeycomb
  - **Description**: Honeycomb is an observability platform that enables deep analysis of system behavior during incidents. It provides high-cardinality data exploration, distributed tracing, and collaborative postmortems to understand and mitigate the impact of incidents.

The SRE toolchain encompasses a range of tools and practices tailored to the unique challenges of managing large-scale, distributed systems with a focus on reliability, scalability, and efficiency.

