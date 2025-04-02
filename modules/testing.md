# All Software has Issues

<div class="h-10" />

Code will always have issues
- e.g. bugs, things we want to add or improve


It's not enough to know about them, we need to **manage them**
- Identify, record, prioritise

---

# Testing

Humans are fallible! Our software will contain defects
  - In requirements, design, as well as code
  - 1-10-150 hours to fix in design/development/production
  - Microsoft Study estimated 10-20 defects per 1000 lines of code

**Validation**: are we building the right product?

**Verification**: are we building the product right?
  - Manual testing, unit testing, automated testing, code reviews

---
layout: two-cols-header
---

# Repercussions of Software Bugs
### Basic science

::left::

<div class="h-10"></div>

- Highly-cited papers published on multidrug resistance transporters (2001 - 2010)
- Results couldn't be reproduced - 5 retractions
- Caused by error in an internal software utility
- Flipped two columns of data, inverting electron-density map used to derive protein structure

::right::

::center

<div class="h-10"></div>

<img src="../img/chem.png" alt="Chemistry" width="60%" />

*“I didn't question it then. Obviously now I check it all the time."* - Geoffrey Chang

::

---
layout: two-cols-header
---

# Repercussions of Software Bugs
### Mars Climate Orbiter

::left::

<div class="h-10"></div>

In 1999 orbiter was lost in space due to a simple unit conversion error (mix-up between metric and imperial units) in its navigation software, costing NASA **$125 million**.
- Communication lost as it entered orbit
- Root cause was unit conversion error
- No proper "checks and tests" on the software responsible were conducted!

::right::

<div class="h-10"></div>

::center

<img src="../img/lunar-lander.png" alt="Lunar lander" width="80%" />

::

---
layout: two-cols-header
---

# Repercussions of Software Bugs
### Knight Capital

::left::

In 2012 a software glitch in the trading system of Knight Capital, one of the largest U.S. trading firms, led to a loss of **$440 million** in just 30 minutes.
- New code changes up until it went live
- Changes activated old test code
- Old code on single server produced thousands of incorrect stock purchase orders very rapidly

::right::

::center

<img src="../img/knight-capital.png" alt="Lunar lander" width="90%" />

::

---

# The Role of Automation in Software Testing

<div class="h-10" />

Manual testing is necessary
However…
- Prone to error
- Can be time-consuming, expensive

Automated testing involves writing code to test software
- Computers are great at repetitive tasks!
- Define complex, repeatable processes with fewer errors
- Saves effort in the long run

Automated testing should supplement, but not replace, all manual testing

---

# Automated Testing

**Unit tests**: Test specific units of functionality, ensuring expected outputs from given inputs.

<v-click>
```python
def celsius_to_fahrenheit(celsius):
    return 32 + 1.8 * celsius

celsius_to_fahrenheit(1.0)
> 33.8

celsius_to_fahrenheit(12.34)
> 54.212
```
</v-click>

---

# Automated Testing

**Unit tests**: Test specific units of functionality, ensuring expected outputs from given inputs.

```python
def celsius_to_fahrenheit(celsius):
    return 32 + 1.8 * celsius

def test_celsius_to_fahrenheit():
	assert celsius_to_fahrenheit(1.0) == 33.8
    assert celsius_to_fahrenheit(12.34) == 54.212
```

---
layout: two-cols-header
class: "gap-4"
leftClass: "justify-center"
rightClass: "justify-center ml-10"
---

#  Code breakdown

::left::

```python {all|1|2-11|12|14-16}
def add3(a, b, c):
	”””Add three numbers

	This code adds three numbers together

	Parameters:
		a, b, c: numbers to add

	Returns:
		Sum of three numbers
	”””
	...

def test_add3(a, b, c):
	assert add3(1, 2, 3) == 6
	assert add3(1, 2, None) == None
```

::right::

<v-click at="1">
<h3>Code signature</h3>
<div class="text-sm">How to run the function</div>
<div class="h-5"></div>
</v-click>

<v-click at="2">
<h3>Documentation</h3>
<div class="text-sm">What the function does and how to use it</div>
<div class="h-5"></div>
</v-click>

<v-click at="3">
<h3>Implementation</h3>
<div class="text-sm">User does not need to know this</div>
<div class="h-5"></div>
</v-click>

<v-click at="4">
<h3>Test</h3>
<div class="text-sm">Defines behaviour</div>
</v-click>

---

# Test Drive Development (TDD)

<style>
.default {
  background-color: #eef9ff;
}
</style>

::centralise::

::center
<img src="../img/tdd.png" alt="Test driven development" width="90%" />
::

---
transition: "none"
---

# Automated Testing

<div class="text-gray-400">
<b>Unit tests</b>: Test specific units of functionality, ensuring expected outputs from given inputs.
</div>

<b>Integration (functional) tests</b>: Test functional paths through the code, especially useful for exposing faults in inter-unit interactions.

---

# Automated Testing

<div class="text-gray-400">
<b>Unit tests</b>: Test specific units of functionality, ensuring expected outputs from given inputs.

<b>Integration (functional) tests</b>: Test functional paths through the code, especially useful for exposing faults in unit interactions.
</div>

<b>Regression tests</b>: Ensure unchanged program output despite code modifications.

---

# PyTest

pytest: a framework for automated testing
- Automatically finds any function starting in `test_` or ends in `_test`
- Produces a report indicating test status
- Many advanced features (e.g. mocks, fixtures)
- Install with `pip install pytest`
- Run with `pytest` (or `pytest -v` for an itemised view)

Testing investment should match the software's complexity and usage

---
layout: instruction
---

# Unit testing

::left::

::center
Write some unit tests
::

::right::

- Instructor: demo pytest install and running the test suite
- Write tests for the smoothie function (tip: read the docstring and try out the function to see how it behaves)
- Run the test suite
- Write a test that fails (to see the output)
- Think of edge cases that can be added to the test suite (e.g. negative numbers, etc.)
- Can the function be improved?
