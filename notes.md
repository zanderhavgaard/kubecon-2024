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
