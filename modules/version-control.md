---
layout: two-cols-header
rightClass: ""
---

# Code management & collaboration

::left::

- *Version control* provides a full history of your project's software and other assets
- Makes for easy:
  - Backups
  - Collaboration
  - Recovering from dead-ends
- What should be in version control?
  - Code, documentation, tests, test data, analysis scripts
  - Reports, papers, etc.
- Packaging and deployment

::right::

::center
<img src="../img/phd-final.gif" alt="PhD comic: 'Final Version'" width="75%" />
::

---

# Code management & collaboration

::centralise::

::center

<i>“If you’re not using version control,<br>
whatever else you might be doing with a computer,<br>
it’s not science."</i><br>
<br>
Greg Wilson, SWC

::

---

# Version Control

<div class="h-10" />

- These skills will save you time
- Always assume others will use and develop your software
- Be clear on requirements and assume they will change
- Funders are increasingly expecting software outputs to be sustainable and reusable

---

# Version Control Systems

::centralise::

::center
<img src="../img/git-logo.png" alt="Git logo" width="35%">
<div class="flex w-100% justify-center">
  <img src="../img/svn-logo.png" alt="SVN logo" width="20%">
  <img src="../img/mercurial-logo.png" alt="Mercurial logo" width="20%">
</div>
::

---
layout: two-cols-header
---

# Version Control

::left::

<div class="h-10" />

- **Backup**
- Reproducibility
- Collaboration

::right::

<img src="../img/version-control-backup.png" alt="Version control backup">

---
layout: two-cols-header
---

# Version Control

::left::

<div class="h-10" />

- Backup
- **Reproducibility**
- Collaboration

::right::

<img src="../img/version-control-reproducibility.png" alt="Version control reproducibility">

---
layout: two-cols-header
---

# Version Control

<div class="h-10" />

::left::

- Backup
- Reproducibility
- **Collaboration**

::right::

<img src="../img/version-control-collaboration.png" alt="Version control collaboration">

---

# How do version control tools work?

<div class="h-10" />

- Start by storing the base version of the file
- After that, only changes are stored
- Like instructions for building lego

::centralise::

::center

<img src="../img/commit-doc.png" alt="Version control collaboration">

::

---
layout: instruction
---

# Version control

::left::

::center
Making a commit
::

::right::

Instructor demo:
- Make change to a repository
- Stage, Commit using CLI
- Indicate git UI

---

# Git Branches + Feature Branch Workflow

<div class="flex flex-1 items-end justify-between h-64 w-100%">

<div class="flex flex-col justify-between items-center w-45 h-100% text-sm">
Commit to main branch
```mermaid {scale: 0.8}
gitGraph BT:
  commit id: "First"
  commit id: "Second"
```
</div>

<div v-click class="flex flex-col justify-between items-center w-45 h-100% text-sm">
Create a new branch, make commits to it
```mermaid {scale: 0.8}
gitGraph BT:
  commit id: "First"
  commit id: "Second"
  branch feature
  commit id: "New thing"
```
</div>

<div v-click class="flex flex-col justify-between items-center w-45 h-100% text-sm">
Changes independent of main branch
```mermaid {scale: 0.8}
gitGraph BT:
  commit id: "First"
  commit id: "Second"
  branch feature
  commit id: "New thing"
  checkout main
  commit id: "Other work"
```
</div>

<div v-click class="flex flex-col justify-between items-center w-45 h-100% text-sm">
Merge commit
```mermaid {scale: 0.8}
gitGraph BT:
  commit id: "First"
  commit id: "Second"
  branch feature
  commit id: "New thing"
  checkout main
  commit id: "Other work"
  merge feature
```
</div>

</div>


- Main branch for tested, stable code, feature branches for new, separate units of work
- Keeps main branch stable, allows independent work on features
- Easy to discard unwanted features

::center
<br>To change branches: `git checkout <branch_name>`
::

---

# Git Branches

::centralise::

::center
```mermaid
gitGraph
  commit id: "A"
  branch develop
  commit id: "B"
  branch big_feature
  commit id: "F"
  checkout develop
  commit id: "C"
  checkout main
  merge develop tag: "v1.1"
  checkout develop
  branch small_feature
  commit id: "D"
  commit id: "E"
  checkout big_feature
  commit id: "G"
  checkout develop
  merge small_feature
  checkout main
  merge develop tag: "v1.2"
  checkout big_feature
  commit id: "H"
```
::

---
layout: instruction
---

# Version Control

::left::

::center
```mermaid
gitGraph BT:
    commit id: 'Initial'
    branch feature
    commit id: 'Feature'
    checkout main
    merge feature tag: "v1.0"
```
::

::right::

- Make a change, stage and commit to the main branch directly
- Create a feature branch
- Make a change, stage and commit to the feature branch
- Merge your feature branch back into main
