# KubeCon 2024 Tuesday

# OpenTofu Day

## Atlantis and OpenTofu: The Future of Open-Source IaC

https://colocatedeventseu2024.sched.com/event/1YFdl/atlantis-and-opentofu-the-future-of-open-source-iac-pepe-amengual-slalom-dylan-daniel-page-lambda-labs

## OpenTofu Registry: The Low-Maintenance & Highly-Available Open Source SaaS

https://colocatedeventseu2024.sched.com/event/1YZuV/opentofu-registry-the-low-maintenance-highly-available-open-source-saas-james-humphries-spacelift-arel-rabinowitz-env0

# Platform Engineering Day

## Building a Platform Engineering API Layer with kcp - Marvin Beckers, Kubermatic GmbH

https://colocatedeventseu2024.sched.com/event/1YFfY/building-a-platform-engineering-api-layer-with-kcp-marvin-beckers-kubermatic-gmbh

KCP looks interesting

## Panel: The Platform Rock-Paper-Scissors: Build, Adopt, Buy - Jorge Lainfiesta, Independent Contributor; Leena Mooneeram, Chainalysis; Victor Araujo, Wolt; Jinhong Brejnholt, Saxo Bank; Edgaras Petovradžius, LEGO Group

https://colocatedeventseu2024.sched.com/event/1YFgB/panel-the-platform-rock-paper-scissors-build-adopt-buy-jorge-lainfiesta-independent-contributor-leena-mooneeram-chainalysis-victor-araujo-wolt-jinhong-brejnholt-saxo-bank-edgaras-petovradzius-lego-group

---

# DOK - Data on K8s

## Discover how to create your own metadata driven ML platform from scratch

https://colocatedeventseu2024.sched.com/event/1YFh7/discover-how-to-create-your-own-metadata-driven-ml-platform-from-scratch-ted-chang-yihong-wang-ibm

Outline:

- Open Lakehouse
  - Data warehouse + data lake
  - metadata store + sql engine
- metadata driven ml pipeline
  - kubeflow
  - training operator, katlib, kserve and more

ML lifecycele:

- use data
  - gather data
  - analyze data
- to build models
  - compose model
  - train model
- that automate decisions
  - deploy model
  - maintain model

feedback loops within each step, and from step to step

Two main challenges:

- data preparation
  - large data volume
  - different data types, structed vs unstructures vs semi
  - flexibility to work with data from different sources/types
  - storing data is expensive
  - what formats should data be stored in?
- ML lifecycle
  - ML is complex
  - it is error-prone ...
  - time consuming
  - how to automate effectively?

solution -> "open lakehouse"

- data lakehouse combine data warehouse and data lake
- leverage cloud objects storage (s3) to store broad range of data

> open lakehouse architecture stack on slide, look it up later.

Iceberg - open table format
https://iceberg.apache.org/

- table format designed for huge amounts of data
- data in s3
- use metadata files to keep track of data
- every table modification creates a new metadata file

Presto - processing engine
http://prestodb.io/

- open source sql query enging
- federated access to data from different sources
- one sql engine to rule them all
- python sdk
- UI/Notebook -> Zeppelin https://zeppelin.apache.org/docs/0.11.0/quickstart/sql_with_zeppelin.html

> They showed a demo of a jupyter notebook running in a UI and not in a browser, looked useful, check up on this.
> It's jupyterlab I think, looks cool: https://jupyter.org/
> Plugin for jupyterlab https://github.com/elyra-ai/elyra

Kubeflow pipelines

- containerized implementations of ML tasks
- DAG/pipeline of data/ML jobs
- reuse data
- compare different runs

Parameter tuning with Katib
https://www.kubeflow.org/docs/components/katib/overview/

Kubeflow training Operator
https://www.kubeflow.org/docs/components/training/

Kserver for deploying models
https://kserve.github.io/website/0.11/

---

## From Zero to Hero: Scaling Postgres in Kubernetes Using the Power of CloudNativePG - Gabriele Bartolini, EDB

https://colocatedeventseu2024.sched.com/event/1YFha/from-zero-to-hero-scaling-postgres-in-kubernetes-using-the-power-of-cloudnativepg-gabriele-bartolini-edb

"How to make the _world_ the single point of failure? (for your database)"

"Running postgres in k8s is superior to _traditional_ ways of running postgres"

Highly available postgres with CloudNativePG
https://cloudnative-pg.io/

- manages postgres clusters in k8s
- production ready
- install with helm
- declarative management with k8s api
- automatic failover, always one primary, and a number of redundant replicas, using pg to sync data between instances
- continuous backup feature
- failover from cluster to cluster

> I don't think we need to run our postgres in k8s right now, but if we need scaling in the future, or postgres caches, then this looks very interesting.

Temporary dev postgres cluster created for the day, and then torn down at the end of the day -> could we do a daily clone of production instead of dedicated dev dbs?

## Lightning Talks

### ⚡ Lightning Talk: Enabling Hot Restart of Stateful Applications Including GPU-Accelerate AI/ML Workloads - Bernie Wu, MemVerge

https://colocatedeventseu2024.sched.com/event/1YFiB/cl-lightning-talk-enabling-hot-restart-of-stateful-applications-including-gpu-accelerate-aiml-workloads-bernie-wu-memverge

Enable Data/AI/ML workloads to be k8s native - Rescheduled ad hoc, resilience, spot instances etc.

CRIU - https://criu.org/Main_Page
Freeze state of running container and persist to disk and allow restore to exactly same state, i.e. on a different node.

### ⚡ Lightning Talk: My Database Runs on Kubernetes. What's Next? Data Platforms! - Robert Hodges, Altinity

https://colocatedeventseu2024.sched.com/event/1aCb6/cl-lightning-talk-my-database-runs-on-kubernetes-whats-next-data-platforms-robert-hodges-altinity

"Data platform == custom stack to solve business problem"

"Kubernetes encourages app vs platform functions"

"Even in startups with 2 people, one person makes the app and one makes platform, b/c/ it's just easier"

'shims' as a interface between app and platform, enabled by k8s control-plane, example: PVC/PV - ig. AWS EBS CSI Driver

### ⚡ Lightning Talk: Ditching Data Pipelines: why treating Data as Assets is the best thing you can do - Andrea Giardini, Independent

https://colocatedeventseu2024.sched.com/event/1YFiG/cl-lightning-talk-ditching-data-pipelines-why-treating-data-as-assets-is-the-best-thing-you-can-do-andrea-giardini-independent

AirFlow is like Jenkins ... and is very good about how data is created ...

... but we care more about how data relates to each other.

We should treat data as assetes instead.

Dagster get's it right -> data is assetes with relations to other data.

Cloud Native first, integrates with things we use.

## Lessons Learned from Building a Database Operator - Rajdeep Das & Sebastian Łaskawiec, MongoDB

https://colocatedeventseu2024.sched.com/event/1YFiZ/lessons-learned-from-building-a-database-operator-rajdeep-das-sebastian-laskawiec-mongodb

MongoDB ...

- document database
- transactional
- flexible and scalable
- streams and vector search

Using kubernetes operator for self hosted mongodb

- data plane and control plane running in k8s

## Advanced CSI-FUSE Filesystem for AI/ML Data Management in Kubernetes - Lu Qiu, Alluxio

https://colocatedeventseu2024.sched.com/event/1YFj3/advanced-csi-fuse-filesystem-for-aiml-data-management-in-kubernetes-lu-qiu-alluxio

FUSE - Turn cloud storage into local filesystem

- S3 FUSE - https://github.com/s3fs-fuse/s3fs-fuse

Performance can be improved by using local caches - S3FS has cache feature

Apache Arrow is useful for transmitting data between technologies

FSSpec can be used for interfacing arrow data with files.
https://filesystem-spec.readthedocs.io/en/latest/

Ray - framework for scheduling ML jobs/workloads - https://docs.ray.io/en/latest/index.html

## Cloud-Native Dataspaces: Experiences from the German Research Data Ecosystem - Sebastian Beyvers, Justus Liebig University Giessen

https://colocatedeventseu2024.sched.com/event/1YFjZ/cloud-native-dataspaces-experiences-from-the-german-research-data-ecosystem-sebastian-beyvers-justus-liebig-university-giessen

FAIR data principle, data should be ...

- Findable
- Accessible
- Interoperable
- Reusable

Using Cloud Native tools to build data spaces:

Status quo -> domains with different data formates / technologies -> each domain in it's own silo, with it's own practices.

New -> k8s based with FAIR:

Metadata:

- Dublin core based
- title, author, description, lables, relations
- techincal: size, location, acl

Data exchange -> s3 compatible interface
OIDC for auth
Distributed metada storage with centralized search interface

Multiple clusters, cluster per domain, linked with Istio

Powered by event driven architecture with NATS and Argo Events
Argo workflows for compute

WIP reference implementation:
https://aruna-storage.org/

## Released From the Cage: Apache Kafka Without Its ZooKeeper - Jakub Scholz, Red Hat

https://colocatedeventseu2024.sched.com/event/1YFk0/released-from-the-cage-apache-kafka-without-its-zookeeper-jakub-scholz-red-hat

Strimzi is now a CNCF incubating project

Goal is to get rid of zookeeper to make operations easier and more scalable.

# KubeCon Day 1

## Advanced Resource Management for Running AI/ML Workloads with Kueue - Michał Woźniak, Google & Yuki Iwai, CyberAgent, Inc.

https://kccnceu2024.sched.com/event/1YeLj/advanced-resource-management-for-running-aiml-workloads-with-kueue-michal-wozniak-google-yuki-iwai-cyberagent-inc?iframe=no&w=100%&sidebar=yes&bg=no

https://kueue.sigs.k8s.io/

Kueue:

- job-level scheduler
- works on jobs, not pods
- delay pod creation, off-load api-server and kube-scheduler
- support 'all-or-nothing' processing (as linked jobs could deadlock)
- resource quota management

Kueue is 'kube-native', all state is in etcd, no external dbs
Compatibel with other k8s components

pods creation is gated by job admission
integrates with other things?

useful for scheduling batch workloads in an organized/resource-efficient way, using queues of workloads instead of 'pod-soup'

workloads can have different priority

kubeflow for training models
kserve for deploying models

---

## Bloomberg's Journey to a Multi-Cluster Workflow Orchestration Platform - Yao Lin & Reinhard Tartler, Bloomberg

https://kccnceu2024.sched.com/event/1YeLy?iframe=no

Users provide:

- code in containers
- an execution plan: ordering, fan-out, synchronization
- a triggering schedule

they use argo workflows:

- has a nice UI
- ml orchestration
- CI/CD
- data processing pipelines

what users expect:

- non-functional:
  - bookkeeping
  - observability
  - debuggability
- functional:
  - where is it running?
  - approval guard
  - scheduling events
  - resiliency across datacenters

A workflow consists of several parts:

- the domain workflows - the "thing" you want to do
- some config
- some secrets
- some "default" workflows, e.g. send a message to slack on workflow completion

workflows have to run, even if one of the datacenters is not available

they have better experience running multiple small clusters than fewer large clusters, b/c of better scalability and minimal 'noisy-neighbor' issues

https://github.com/k3s-io/kine

They use kine to distribute their workloads across the different clusters, with extra api-servers in each cluster that share their state using kine, and the actual state is then synced from the kine-backed api-server to the 'real' api-server in each cluster

multi-cluster federation is an increasingly important need

## A Cilium Introduction: Back to Bee-Sics - Nico Vibert & Dan Finneran, Isovalent

https://kccnceu2024.sched.com/event/1YeMX/a-cilium-introduction-back-to-bee-sics-nico-vibert-dan-finneran-isovalent?iframe=no&w=100%&sidebar=yes&bg=no

---

Chat at AWS booth:

https://awslabs.github.io/data-on-eks/

https://datahubproject.io/

Data mesh ?

Look up talks from previous KubeCons

---

## State of Platform Maturity in the Norwegian Public Sector - Hans Kristian Flaatten, Norwegian Labor and Welfare Administration

https://kccnceu2024.sched.com/event/1YeMj/state-of-platform-maturity-in-the-norwegian-public-sector-hans-kristian-flaatten-norwegian-labor-and-welfare-administration?iframe=no&w=100%&sidebar=yes&bg=no

https://offentlig-paas.no/

---

## Dungeons and Deployments V2: The Clusters of Chaos - Kat Cosgrove, Dell Technologies; Noah Abrahams, Oracle; Seth McCombs, AcuityMD; Ian Coldwater, Independent; Natali Vlatko, Cisco

https://kccnceu2024.sched.com/event/1YeMv/dungeons-and-deployments-v2-the-clusters-of-chaos-kat-cosgrove-dell-technologies-noah-abrahams-oracle-seth-mccombs-acuitymd-ian-coldwater-independent-natali-vlatko-cisco?iframe=no&w=100%&sidebar=yes&bg=no

This was fun, good reminder to check up on the security of our cluster.

TODO: watch the first session.

https://www.youtube.com/watch?v=-CPrDLFM1Aw

---

## How to Save Millions Over Years Using KEDA? - Solene Butruille, BlackRock

https://kccnceu2024.sched.com/event/1YeNo/how-to-save-millions-over-years-using-keda-solene-butruille-blackrock?iframe=no&w=100%&sidebar=yes&bg=no

Aladdin compute - product for creating cloud workstations: jupyter notbooks and vscode-server instances.

Scaling customers pods running workstations sessions, challenge is to know when to scale the pods up and down
HPA is not very useful for this usecase ...

KEDA seems a better fit by scaling on events

KEDA needs an event source, could be prometheus

KEDA has too permissive default RBAC permissions

---

# KubeCon Day 2

## To Infinity and Beyond: Seamless Autoscaling with in-Place Resource Resize for Kubernetes Pods - Aya Ozawa, CloudNatix Inc. & Kohei Ota, Apple

https://kccnceu2024.sched.com/event/1YePO/to-infinity-and-beyond-seamless-autoscaling-with-in-place-resource-resize-for-kubernetes-pods-aya-ozawa-cloudnatix-inc-kohei-ota-apple?iframe=no&w=100%&sidebar=yes&bg=no

This talk was full but sounds very interesting, TODO: watch later

---

## Kubernetes Controllers in Rust: Fast, Safe, Sane - Matei David, Buoyant

https://kccnceu2024.sched.com/event/1YeOR/kubernetes-controllers-in-rust-fast-safe-sane-matei-david-buoyant?iframe=no&w=100%&sidebar=yes&bg=no

`kube-rs` rust lib for interacting with k8s api.
