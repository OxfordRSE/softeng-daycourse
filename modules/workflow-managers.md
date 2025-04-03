# Workflow Managers

- Manage larger pipelines
- Maintains the **Recording Computational Steps** philosophy
- Workflow managers encapsulate complex pipelines
- Can speed up analyses by preventing redundant computation

---

# Snakemake

A tool to create **reproducible** and **scalable** data analyses.

Workflows are described via a human **readable, Python based language**.

They can be **seamlessly scaled** to server, cluster, grid and cloud environments, without the need to modify the workflow definition.

Workflows can entail a **description of required software**, which will be automatically deployed to any execution environment.

<div class="h-8" />

::center
<img src="../img/snakemake-logo.png" width="400">
::

---
layout: instruction
---

# Install Snakemake

::left::

::right::

Snakemake can be installed via `pip`:
```bash
pip install snakemake
```

---
layout: instruction
---

# A simple workflow

::left::

::center
Run a workflow by hand...

<br />

<div class="text-sm">
Before you start, generate a file with random words:
```bash
python generate.sh
```
Let's create a frequency plot of the words in that file.
</div>
::

::right::

<p>
Use another script to count the frequency of words in the file and output the results:
<span v-mark.underline.orange="1">
```bash
python count_words.py -in data/file.txt -out output/wc.txt
```
</span>
</p>

Form a bar chart of the word frequencies, and save it to `word_chart.txt`:
```bash
python words_chart.py
```

Finally, you can view the results by opening `word_chart.txt`.

---
transition: "none"
---

# Snakemake

```bash
python count_words.py -in data/file.txt -out output/wc.txt
```

<v-click>
```python
rule count_words:
    input:
        "data/file.txt"
    output:
        "output/file.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """
```
</v-click>

<div class="h-10" />

<v-click>
```mermaid
graph LR
    A[ ]:::hidden --"data/file.txt"--> B[count_words]
    B --"output/file.txt"--> C[words_chart]
    C --"word_count.txt"--> D([ ]):::hidden
    style A stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
    style D stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
```
</v-click>

---

# Snakemake

```bash
python words_chart.py
```

```python
rule words_chart:
    input:
        "output/file.txt"
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

---
layout: two-cols-header
class: "gap-4"
---

# Snakemake

::left::

```python
rule all:
    input:
        "words_chart.txt"

rule count_words:
    input:
        "data/file.txt"
    output:
        "output/file.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """

rule words_chart:
    input:
        "output/file.txt"
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

::right::

<v-click>
```bash
snakemake --snakefile onefile.smk
```

Open `words_chart.txt` to see the results.

</v-click>

---

# Snakemake

What if we have more than one file?

```bash
python generate.py -n 100 -w 1000
```

<div class="h-8" />

::center
```mermaid {scale: 0.8}
graph TD
    A[ ] --"data/file1.txt"--> A2[count_words]
    B[ ] --"data/file2.txt"--> B2[count_words]
    C[ ] --"data/file3.txt"--> C2[count_words]
    E[ ] --"data/file100.txt"--> E2[count_words]
    AGGREGATE[words_chart]
    A2 --> AGGREGATE
    B2 --> AGGREGATE
    C2 --> AGGREGATE
    E2 --> AGGREGATE

    style A stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
    style B stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
    style C stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
    style E stroke-dasharray: 5 5, fill-opacity:0, stroke-opacity:0;
```
::

---
layout: two-cols-header
class: "gap-4"
transition: "none"
---

# Adapt to multiple files

::left::

```python {all|7,9,17}
rule all:
    input:
        "words_chart.txt"

rule count_words:
    input:
        "data/file.txt"
    output:
        "output/file.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """

rule words_chart:
    input:
        "output/file.txt"
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

---
layout: two-cols-header
class: "gap-4"
transition: "none"
---

# Adapt to multiple files

::left::

```python {7,9,17}
rule all:
    input:
        "words_chart.txt"

rule count_words:
    input:
        "data/file.txt"
    output:
        "output/file.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """

rule words_chart:
    input:
        "output/file.txt"
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

::right::

```python {7,9,17}
rule all:
    input:
        "words_chart.txt"

rule count_words:
    input:
        "data/file{n}.txt"
    output:
        "output/file{n}.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """

rule words_chart:
    input:
        [f"output/file{n}.txt" for n in range(1, 100)]
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

---
layout: two-cols-header
class: "gap-4"
---

# Adapt to multiple files

::left::

```bash
snakemake --snakefile multiplefiles.smk
```

<div class="h-10" />

::center
<v-click>
<img src="../img/snakemake-words-dag.png" width="80%">
</v-click>
::

::right::

```python
rule all:
    input:
        "words_chart.txt"

rule count_words:
    input:
        "data/file{n}.txt"
    output:
        "output/file{n}.txt"
    shell:
        """
        python count_words.py -in {input} -out {output}
        """

rule words_chart:
    input:
        [f"output/file{n}.txt" for n in range(1, 100)]
    output:
        "words_chart.txt"
    script:
        "words_chart.py"
```

---

Scheduling heuristic is applied to
- Maximise parallelization
- Prefer high priority jobs
- Subject to resource constraints
- Disjoint paths in DAG can be executed in parallel
  ```
  snakemake –-cores 8
  ```
