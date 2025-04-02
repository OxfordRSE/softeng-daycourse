# Workflow Managers

- Manage larger pipelines
- Maintains the **Recording Computational Steps** philosophy
- Workflow managers encapsulate complex pipelines
- Can speed up analyses by preventing redundant computation

---

# Workflow managers

(pics)

---

# Workflow managers

A tool to create **reproducible** and **scalable** data analyses.

Workflows are described via a human **readable, Python based language**.

They can be **seamlessly scaled** to server, cluster, grid and cloud environments, without the need to modify the workflow definition.

Workflows can entail a **description of required software**, which will be automatically deployed to any execution environment.

<div class="h-8" />

::center
<img src="../img/snakemake-logo.png" width="400">
::

---

(example rule)

---

Scheduling heuristic is applied to
Maximise parallelization
Prefer high priority jobs
Subject to resource constraints

Disjoint paths in DAG can be executed in parallel
snakemake –-cores 8

---

# Workflow managers

::left::

::right::

- Clone repository with three well-defined functions / packages, and a scaffolded Snakefile (enter static filename, explore dag, execution, etc; then switch to wildcards to process the full set)
- Note how reprocessing only impacts out-of-date files / scripts
