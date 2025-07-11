---
routeAlias: "continuous-integration"
---

# Continuous Integration (CI)

- **Definition**: Continuous Integration (CI) is an automated process for verifying and integrating code changes.
- **Objective**: To detect and resolve issues early by frequently testing and integrating code changes.
- **Importance**: Ensures compatibility, functionality, and reduces the introduction of unexpected problems.

---

# Continuous Integration (CI)

<div class="h-6" />

## Challenges Without CI

- **Compatibility**: Ensuring code works across various OS, software versions, and hardware.
- **Consistency**: Avoiding dependencies on specific user data or development machine configurations.
- **Collaboration**: Managing code changes in tandem with other developers without conflict.

<div class="h-6" />

## Benefits of Implementing CI

- **Efficiency**: Swift detection and resolution of integration issues.
- **Quality Assurance**: Automated tests and builds ensure code quality and functionality.
- **Reproducibility**: Standardised and automated build/deploy processes ensure consistent output.

---

# Continuous Integration (CI)

<div class="h-6" />

## Key Principles

- **Single Source Repository**: Maintain all code and dependencies in a shared repository.
- **Automate the Build**: Automatically compile, package, and create installers for code.
- **Self-testing Builds**: Employ automated tests to validate code functionality post-build.

---

# Continuous Integration Tools

<div class="h-12" />

<div class="grid grid-cols-[50px_auto] gap-4 items-center" v-mark.box.red="1">
  <img src="../img/github.png" width="50px" />
  <div>
    <h2 class="text-xl font-semibold">GitHub Actions</h2>
    A CI/CD tool within GitHub’s platform.
  </div>
</div>
<div class="h-6" />

<div class="grid grid-cols-[50px_auto] gap-4 items-center">
  <img src="../img/travis-logo.png" width="50px" />
  <div>
    <h2 class="text-xl font-semibold">Travis</h2>
    A popular CI service used in various open-source projects.
  </div>
</div>
<div class="h-6" />

<div class="grid grid-cols-[50px_auto] gap-4 items-center">
  <img src="../img/appveyor-logo.png" width="50px" />
  <div>
    <h2 class="text-xl font-semibold">AppVeyor</h2>
    CI/CD tool that allows building, testing, and deploying applications.
  </div>
</div>
<div class="h-6" />

*Note*: Each tool has unique and common features. Exploring multiple options is advised.

---
layout: instruction
---

# Continuous Integration

::left::

::center
<div class="border border-color-black">
<img src="../img/github-action-pytest.png" width="100%" />
</div>
::

<div class="absolute top-43 left-70 w-47 border border-color-black">
<img src="../img/github-issues.png" />
</div>

::right::

Follow-along:
- Add continuous integration to your repository (*Action: “Python Application” [flake8, pytest]*)
- Push changes to your repository
- (Optional) Make a change that breaks your tests, then fix them

---
layout: two-cols-header
class: "gap-4"
---

# Platform support?

::left::

::center
“… density functional theory nuclear magnetic resonance calculations established the relative configurations of compounds 1 and 2 and revealed that the calculated shifts **depended on the operating system** when using the “Willoughby–Hoye” Python scripts to streamline the processing of the output files, a previously unrecognized flaw that could lead to incorrect conclusions.”
::

<div class="absolute border border-color-black top-95 left-27 w-80 p-4 text-center">
The issue was due to
<b>different sorting of file names</b>
on <b>different operating systems</b>
</div>

::right::

::center
<img src="../img/neupane2019.png" width="80%"/>
::

<div class="h-4" />

::center
<div class="text-sm">
Organic Letters, October 8 2019<br>
https://doi.org/10.1021/acs.orglett.9b03216
</div>
::

---
layout: instruction
---

# Continuous Integration

::left::

<div class="text-sm">
<i>Example:</i>
</div>

<div class="text-sm w-full max-w-[80%] mx-auto leading-none table-tight">

| | ubuntu | windows | macos |
|--|:--:|:--:|:--:|
| python 3.9 | ❌ | ❌ | ❌ |
| python 3.10 | ✅ | ❌ | ✅ |
| python 3.11 | ✅ | ❌ | ✅ |
| python 3.12 | ✅ | ❌ | ✅ |

<div class="h-5" />

</div>

```yaml
jobs:
  build:
    runs-on: ${{ matrix.os }}
    strategy:
        matrix:
            os: [ubuntu-latest, windows-latest, macos-latest]
            python-version: [3.9, 3.10, 3.11, 3.12]
```

<div class="absolute border border-gray-400 left-85 top-90">
```yaml
on:
  workflow_dispatch:
```
</div>

::right::

Task:
- Add test matrix
- Add `workflow_dispatch` trigger to your workflow (this allows you to run the action manually)
- Re-run your tests

<!-- You now have the foundation of any Python package! -->

---

# Documentation

**Sphinx** - Build HTML documents from structured text (e.g. markdown, reST)

**ReadTheDocs** - Hosts HTML documents

<div class="h-4" />

:: center
For example:

https://github.com/globaldothealth/InsightBoard
::

<div class="h-4" />

Changes to the documentation (or code) can trigger documentation builds

---

# Documents

**GitHub Pages** - Host static HTML documents

Host documents on GitHub and publish them on GitHub Pages

<div class="h-8" />

:: center
These slides are hosted on GitHub Pages!

https://github.com/OxfordRSE/softeng-daycourse
::

---


# Publish Python packages

Automatically publish to the Python Package Index (PyPI)
<br /><br /><br />

<div class="h-4" />

:: center
For example:

https://github.com/pybamm-team/PyBaMM
::

---

# Application builds

Triggered builds of Windows / MacOS / Linux applications
<br /><br /><br />

<div class="h-4" />

:: center
For example:

https://github.com/kraemer-lab/GRAPEVNE/releases
::
