---
layout: two-cols-header
---

# Versioning

::left::

```python
import numpy as np

def main():
    ...
```

::center
<br><br>
*<v-click>Which version of numpy?</v-click>*
::

::right::

<img src="../img/numpy-versions.png" alt="Numpy versions" />

---
layout: two-cols-header
leftClass: "items-center justify-center gap-10"
rightClass: "items-center justify-center gap-10"
---

# Versioning

::left::

<div class="flex flex-col items-center">
<b>Semantic versioning (SemVer)</b><br>
<small>API stability, communication, dependency management</small>
</div>

<div class="flex flex-col items-center">
<b>Calendar versioning (CalVer)</b><br>
<small>Regular releases, simplicity</small>
</div>

::right::

<div class="flex flex-col items-center">
<b>4.3.1</b><br>
<small>(major.minor.patch)</small>
</div>

<div class="flex flex-col items-center">
<b>2025.01</b><br>
<small>(year.month)</small>
</div>

---
layout: two-cols-header
---

# Versioning

::left::

```python
import numpy as np

def main():
    ...
```

::right::

<img src="../img/numpy-versions.png" alt="Numpy versions" />

<v-click>
  <FancyArrow
    x1="400"
    y1="270"
    x2="535"
    y2="324"
    arc="-0.2"
    head-size="20"
    v-click="1"
  />
</v-click>

---

# Versioning

<div style="position: absolute; top: 100, left: 100; width: 100; height: 100;">
<img src="../img/numpy-logo.svg" alt="Numpy logo" />
</div>

<div class="h-10"></div>

::center

**numpy** is a top-20 downloaded package on PyPI<br>
which in June 2024 released a new major version.

Numpy v1 and v2 were no longer entirely compatible.

The official release notes included the phrase:

_“This major release includes <span v-mark.circle.red="1">breaking changes</span>…<br>
including an ABI break …<br>
and API changes …”_

::

---
layout: "three-cols-header"
layoutClass: "gap-4"
leftClass: "items-center justify-center"
middleClass: "items-center justify-center"
rightClass: "items-center justify-center"
transition: "none"
---

# Version conflict

::left::

<div class="flex flex-col items-center gap-0 p-4">
  <p><b>Software A</b></p>
  <p>numpy v1</p>
  <p>Python 3.7</p>
</div>

::middle::

<img class="border border-black" src="../img/laptop.jpg" alt="Laptop dependencies" />

::right::

<div class="flex flex-col items-center gap-0 p-4">
  <p><b>Software B</b></p>
  <p>numpy v2</p>
  <p>Python 3.13</p>
</div>

---
layout: "three-cols-header"
layoutClass: "gap-4"
leftClass: "items-center justify-center"
middleClass: "items-center justify-center"
rightClass: "items-center justify-center"
---

# Version conflict

::left::

<div class="flex flex-col items-center gap-0 bg-blue-50 border border-black rounded-xl p-4">
  <p><b>Software A</b></p>
  <p>numpy v1</p>
  <p>Python 3.7</p>
</div>

::middle::

<img class="border border-black" src="../img/laptop.jpg" alt="Laptop dependencies" />

::right::

<div class="flex flex-col items-center gap-0 bg-green-50 border border-black rounded-xl p-4">
  <p><b>Software B</b></p>
  <p>numpy v2</p>
  <p>Python 3.13</p>
</div>

---

# Virtualisation

<div style="position: relative; top: 40px; width: 100%; height: auto; margin: auto;">

  <div class="flex flex-col items-center space-y-1">
    <div class="flex space-x-1">
      <div class="w-40 h-20 bg-yellow-500 text-white flex items-center justify-center rounded" v-click="0">venv</div>
    </div>
    <div class="flex space-x-1">
      <div class="w-80 h-20 bg-amber-500 text-white flex items-center justify-center rounded" v-click="2">conda</div>
    </div>
    <div class="flex space-x-1">
      <div class="w-120 h-20 bg-orange-500 text-white flex items-center justify-center rounded" v-click="4">Container</div>
    </div>
    <div class="flex space-x-1">
      <div class="w-160 h-20 bg-red-500 text-white flex items-center justify-center rounded" v-click="6">Virtual Machine</div>
    </div>
  </div>
  
  <div class="absolute top--10 right-25" v-click="1">
    Python & packages
  </div>
  
  <FancyArrow
    x1="673"
    y1="-10"
    x2="525"
    y2="40"
    arc="0.2"
    head-size="20"
    v-click="1"
  />
  
  <div class="absolute top-12 left-10" v-click="3">
    General software
  </div>
  
  <FancyArrow
    x1="110"
    y1="75"
    x2="265"
    y2="125"
    arc="-0.2"
    head-size="20"
    v-click="3"
  />
  
  <div class="absolute top-33 right--6" v-click="5">
    Environment
  </div>
  
  <FancyArrow
    x1="835"
    y1="160"
    x2="685"
    y2="210"
    arc="0.2"
    head-size="20"
    v-click="5"
  />
  
  <div class="absolute top-55 left--8.5" v-click="7">
    System
  </div>
  
  <FancyArrow
    x1="0"
    y1="245"
    x2="110"
    y2="295"
    arc="-0.2"
    head-size="20"
    v-click="7"
  />

</div>

---
layout: instruction
---

# Dependency management

::left::

::center
Numpy v1
::

::right::

Instructor demo / follow-along:
- Create a `venv`
- Activate the `venv`
- Install a dependency
- Run the software
- Deactivate the `venv`
- Run the software (should fail)

---
layout: instruction
---

# Dependency management

::left::

::center
Numpy v2
::

::right::

Task:
- Create a second `venv` named `venv2`
- Activate `venv2`
- Install numpy 2
- Run the software
- Deactivate the venv
