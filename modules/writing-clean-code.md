---
layout: two-cols-header
leftClass: m-1
rightClass: m-1
routeAlias: writing-clean-code
---

# Writing Clean Code
### Organise your files

::left::

```
Flat
├─ script.py
├─ image_1.jpg
├─ script_2.py
├─ utils.py
├─ image_1.png
├─ README.md
├─ image_2.png
├─ test_utils.py
├─ pyproject.toml
├─ notes.docx
├─ .gitignore
:
:
:
:
└─
```

::right::

<v-click>
```
Structured
├─ README.md
├─ pyproject.toml
├─ .gitignore
├─ src
│  ├─ script.py
│  ├─ script_2.py
│  └─ utils.py
├─ tests
│  └─ test_utils.py
├─ images
│  ├─ image_1.png
│  ├─ image_1.jpg
│  └─ image_2.png
├─ docs
│  └─ notes.docx
└─ dist
```
</v-click>

<!--
Software projects often start as a collection of scripts and assorted files, but will soon grow and become unwieldy. Structuring your projects will not only help you keep track of your files, but also make it easier for others to understand your project.

- Organise files into directories
- Structuring projects will help you convert your 'collection of scripts' into an installable Python package later on.
- Mention special files (e.g. pyproject.toml, .gitignore)
-->

---
layout: two-cols-header
class: gap-4
---

# Writing Clean Code
### Use meaningful names

::left::

```python
def convert(x):
	...
```

::right::

<v-click>
```python
def celsius_to_fahrenheit(celsius):
    ...
```
</v-click>

---
layout: two-cols-header
class: gap-4
---

# Writing Clean Code
### Use meaningful names - _provides context for AI..._

::left::

```python
def convert(x):
	if isinstance(x, str):
        return x.upper()
    elif isinstance(x, int):
        return x * 2
    elif isinstance(x, list):
        return [convert(i) for i in x]
    else:
        return None
```

::right::

```python
def celsius_to_fahrenheit(celsius):
    """Convert Celsius to Fahrenheit."""
    return (celsius * 9/5) + 32
```

<v-click>

- Meaningful names help *us* understand the code
- But they also provide context to AI models
- Thus, AI models can provide better suggestions

</v-click>

---
layout: two-cols-header
class: gap-4
---

# Writing Clean Code
### But context can also be a constraint for AI...

::left::

```python
def levenshtein(a, b):
```

produces

```python {*}{maxHeight:'280px'}
def levenshtein(a, b):
    """Compute the Levenshtein distance
       between two strings."""

    if len(a) < len(b):
        return levenshtein(b, a)

    if len(b) == 0:
        return len(a)

    previous_row = range(len(b) + 1)
    for i, c1 in enumerate(a):
        current_row = [i + 1]
        for j, c2 in enumerate(b):
            insertions = previous_row[j + 1] + 1
            deletions = current_row[j] + 1
            substitutions = previous_row[j] \
                + (c1 != c2)
            current_row.append(
                min(
                    insertions,
                    deletions,
                    substitutions
                )
            )
        previous_row = current_row

    return previous_row[-1]
```

::right::

<v-click>

```python
from Levenshtein import distance

def levenshtein(a, b):
```

</v-click>

<v-click>

makes appropriate use of the imported library:

```python
def levenshtein(a, b):
    return distance(a, b)
```

</v-click>

<v-click>

_AI (re)-invented the algorithm because it was constrained to the script context_

</v-click>

---

# Writing Clean Code
### Use consistent naming conventions

<div class="h-10" />

- Makes code more consistent (hence readable)
- Conventions are usually language-specific
    - [PEP 8](https://peps.python.org/pep-0008/) - Style Guide for Python Code
    - Python typically uses `snake_case` for function and variable names
- Conventions can provide context
    - Python typically uses `PascalCase` for class names
- Conventions reduce arbitrary decision-making in code
- Conventions make code from different projects feel familiar
- Linters can help us adhere to language standards

<div class="absolute right-5 top-35 w-[20%] text-xl">
<pre><code>
camelCase
PascalCase
kebab-case
snake_case
</code></pre>
</div>

---
layout: two-cols-header
---

# Writing Clean Code

### Linters
- Compares your code to a standard (e.g. PEP)
- Identifies programming errors, bugs, stylistic errors

<div class="h-5" />

::left::

<style>
code {
    font-size: 1.2rem;
    line-height: 2.0;
}
</style>

```python
import os

def hello():
    print(name)
```

::right::

<div class="h-2" />

<div class="twoslash lsp">
  <div class="twoslash-error-line twoslash-error-level-warning">
    <div class="twoslash-popup">
      <div class="twoslash-popup-content">
        <div>'os' imported but unused</div>
      </div>
    </div>
  </div>
</div>

<div class="h-7" />

<div class="twoslash lsp">
  <div class="twoslash-error-line">
    <div class="twoslash-popup">
      <div class="twoslash-popup-content">
        <div>expected 2 blank lines, found 1</div>
      </div>
    </div>
  </div>
</div>

<div class="twoslash lsp">
  <div class="twoslash-error-line">
    <div class="twoslash-popup">
      <div class="twoslash-popup-content">
        <div>undefined name 'name'</div>
      </div>
    </div>
  </div>
</div>

---

# Writing Clean Code

### Auto-formatters
- Applies stylistic conventions

<div class="flex justify-center">
<div class="w-1/2 p-4">
```python
def calc(a,b,c=2):
 x=a+b+c
 y=( a+b+c)/ 3 
 return  { "sum":x ,"avg":y }

nums=[1,2,3]
out=calc(   nums [0],nums [1] ,c = 5  )
print( out )
```
</div>
<div class="w-1/2 p-4">
```python
def calc(a, b, c=2):
    x = a + b + c
    y = (a + b + c) / 3 
    return {"sum": x, "avg": y}


nums = [1, 2, 3]
out = calc(nums[0], nums[1], c=5)
print(out)
```
</div>
</div>


<v-clicks>

- Saves time
- You don’t have to worry about remembering all of the rules
- Reduces decision making

</v-clicks>

---
layout: two-cols-header
class: items-center
---

# Writing Clean Code
### Documentation

::left::

Instructions (README.md):
- Brief description of project
- How to install
- Preferably provide a minimal example

In code:
- Docstrings
- Annotations

::right::

<img src="../img/grapevne-py.png" alt="GRAPEVNE" width="80%" />

---

# Writing Clean Code
### Documentation

<div class="h-10" />

Docstrings ([PEP-257](https://peps.python.org/pep-0257/))
- Single or multiline
- Can be applied to functions and classes
- Forms self-documenting code (`help(function_name)`)
- Often used to create (automatic) online documentation

---
layout: "two-cols-header"
---

# Writing Clean Code
### Documentation - docstrings

::left::

<div class="p-4">
```python
def celsius_to_fahrenheit(celsius):
	"""Convert celsius to Fahrenheit"""
	return 32 + 1.8 * celsius
```
</div>

::right::

<div class="p-4">
```python
> help(celsius_to_fahrenheit)

celsius_to_fahrenheit(celsius)
    Convert celsius to Fahrenheit
```
</div>

---
layout: "two-cols-header"
---

# Writing Clean Code
### Documentation - docstrings

::left::

<div class="p-4">
```python
def add3(a, b, c):
	"""Add three numbers

    A longer description of the
    function, if one is necessary.

	Params:
		a, b, c: numbers to add

	Returns:
		Sum of three numbers
	"""
	...
```
</div>

<small><i>A potential use for AI</i></small>

::right::

<div class="p-4">
```python
> help(add3)

add3(a, b, c)
	Add three numbers

    A longer description of the
    function, if one is necessary.

	Params:
		a, b, c: numbers to add

	Returns:
		Sum of three numbers
```
</div>

---
transition: none
---

# Writing Clean Code
### Documentation - scaffolding


<br>

<div class="flex justify-center">
    <div class="w-3/4 p-4">
Using annotations to scaffold code:

```python
# Read data from file
...

# Calculate word count and add 10
...


# Print final word count
...
```
    </div>
</div>

---
transition: none
---

# Writing Clean Code
### Documentation - scaffolding


<br>

<div class="flex justify-center">
    <div class="w-3/4 p-4">
Using annotations to scaffold code:

```python
# Read data from file
data = read_data(filename)

# Calculate word count and add 10
word_count = calculate_word_count(data)
word_count = word_count + 10

# Print final word count
print(word_count)
```
<i><small>AI can use this scaffolding to suggest code</small></i>
    </div>
</div>


---

# Writing Clean Code
### Documentation - scaffolding



<br>

<div class="flex justify-center">
    <div class="w-3/4 p-4">
Tidy-up - <small><i>consolidate comments:</i></small>

```python
# Report word count
data = read_data(filename)
word_count = calculate_word_count(data)
word_count = word_count + 10
print(word_count)
```
</div></div>

---

# Writing Clean Code
### Documentation - annotations

<div class="flex justify-center">
    <div class="w-3/4 p-4">
<br>
Real world example (useful):

```python
# we don't use path.splitext to also handle extensions like .cdt.dpa
filename, ext = filepath.split(".", maxsplit=1)
```
    </div>
</div>

<br>

::: center

<v-click>
Don’t state <b>what</b> <i>(the code already tells us that)</i><br>
explain <b>why</b> <i>(provide context)</i>
</v-click>

:::

---

# Writing Clean Code
### Single responsibility principle

<div class="h-10" />

- Long functions conflate purpose, can easily introduce bugs
- Break long functions into smaller functions
- Easier to replace smaller functions when new methods become available
- Rule of thumb: functions should not be too long

---
layout: "two-cols-header"
---

# Writing Clean Code
### Single responsibility principle

::left::

<div class="p-4 pt-0" >

One large script

```python {*}{maxHeight:'340px'}
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.decomposition import PCA
from scipy.stats import ttest_ind

# 1. Load data
df = pd.read_csv("gene_expression.csv")

# 2. Preprocess
df = df.dropna()
df = df[df['quality'] > 0.8]

# 3. Perform PCA
pca = PCA(n_components=2)
pca_result = pca.fit_transform(df.iloc[:, 2:])

# 4. Statistical test
group1 = df[df['condition'] == 'treated']
group2 = df[df['condition'] == 'control']
p_value = ttest_ind(group1['geneX'], group2['geneX'])[1]

# 5. Plot results
sns.scatterplot(x=pca_result[:, 0], y=pca_result[:, 1])
plt.title("PCA of Gene Expression")
plt.show()

# 6. Save report
with open("report.txt", "w") as f:
    f.write(f"P-value for geneX: {p_value}")
```

</div>

::right::

<div class="p-4 pt-0">

Re-focus on logic (not implementation)

```python
df = load_and_clean("gene_expression.csv")
pca_result = run_pca(df)
p_value = run_ttest(df, "geneX")
plot_pca(pca_result)
write_report(p_value)
```

```python
def load_and_clean(filename)
def run_pca(df)
def run_ttest(df, gene)
def plot_pca(pca_result)
def write_report(p_value)
```

<div class="list-disc space-y-0 leading-tight">
<ul>
  <li v-click>Easier to read</li>
  <li v-click>Implementation can be updated without affecting core logic</li>
  <li v-click>Promotes re-use of code</li>
</ul>
</div>

</div>

---

# Writing Clean Code

### Coding with AI:

<div class="h-4" />

- AI _can_ be very helpful in checking the logic, consistency and overall correctness of your code
- AI _can_ help to restructure long scripts into shorter, more modular functions
- AI _can_ help spot (and fix) bugs in your code
- **BUT** AI _does not have your understanding of the problem_, and may just as easily introduce bugs
- AI can restructure your code, but in-so-doing change the logic in subtle ways that prevent it from working as intended

---

# Writing Clean Code

### Coding with AI:

<div class="h-4" />

::center

**Professional Software Developers Don’t Vibe, They Control:<br />
AI Agent Use for Coding in 2025**

Through field observations (N=13) and qualitative surveys (N=99), we find that while<br/><b>experienced developers value agents as a productivity boost,<br />they retain their agency in software design and implementation</b><br/>out of insistence on fundamental software quality attributes, employing<br/>strategies for controlling agent behavior leveraging their expertise.

[Huang et al. 2025](https://arxiv.org/html/2512.14012v1)

::

<v-clicks>

- Always review AI-generated code carefully
- Test thoroughly!

</v-clicks>

---

# Recording computational steps

<div class="h-10" />

**A comment on workspaces in JuPyter / Matlab / R:**
- A script / program records a series of computational steps
- Workspaces are designed to resume previous sessions (persistent state)
- This can introduce manual steps that are <span v-mark.underline.orange="1">not recorded</span>, making it <span v-mark.underline.red="2">impossible to reproduce</span> the previous result(s)

**Regularly 'run from the top'**
- Select 'Rull All' cells or the equivalent when you start work for the day
- Fix any problems before you continue creating
- If it doesn't take long to run, _always_ run all cells

---
layout: instruction
---

# Instructor follow-along...

::left::
::center
Get up and running with Codespaces
::

::right::
Navigate to the project:<br />
<small>
<a href="https://github.com/OxfordRSE/softeng-daycourse-cleancode">github.com/OxfordRSE/softeng-daycourse-cleancode</a>
</small>

- Open in Codespaces
- Select **New File** and name it `main.py`
- Populate the file with:
::center
```python
print(“Hello World”)
```
::
- Run from the terminal:
::center
```bash
python main.py
```
::

---
layout: instruction
---

# Linting and auto-formatters

::left::

::center
Explore and organise the repository
::

::right::

Install the linter:
::small
- Install linter: ```pip install pylint```
- Run linter on `fixme.py`: ```pylint fixme.py```
::

Get the linter to pass!
::small
- Try to resolve a few linting errors by hand
- Run an auto-formatter on the file to provide style consistency
  - `pip install black`
  - `black fixme.py`
  - Compare the file before (`fixme_orig.py`) and after
- Organise the file structure
::

<!--
Instructor comment: ruff is faster, but the defaults are not as strict as pylint, and turning all rules on is too verbose.
-->
