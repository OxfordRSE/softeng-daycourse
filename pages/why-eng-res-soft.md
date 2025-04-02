::centralise::

# Why <span v-mark.underline.orange="1">engineer</span> research software?

---

# Research is impossible without software

::centralise::

<img src="../img/why-engineer-software.png" alt="Classroom" style="width: 100%;"/>

From thrown-together scripts, through an abundance of complex spreadsheets, to the millions of lines of code behind large-scale infrastructure, there are few areas where software does not play a fundamental part in research

<!--
‘Not MY software’... ‘Doesnt affect my scripts on my desktop’ lets think about what the lifecycle of those scripts are…

Your software (experiments, analysis, meta analyses, visualisation) produces the results for articles from your lab

Articles are picked up by news agencies and government policy advisories to shape public opinion and government policy

Need to ensure transparency, reproducibility, potential for expansion and collaboration, correctness

Quite scary - suddenly a great emphasis on your code; you want it to be correct, you need it to be well documented.. Or even yourself in 6 months when your writing up

Make life easy for yourself NOW and strcutreu your code
-->

---
transition: "none"
---

# Idealised research software lifecycle

::centralise::

::center

<div class="relative h-90 w-140">

  <!-- Cascading boxes -->
  <div class="absolute top-0 left-0 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Research Questions
  </div>

  <div class="absolute top-16 left-16 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Develop Software
  </div>

  <div class="absolute top-32 left-32 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Run Software
  </div>

  <div class="absolute top-48 left-48 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Analyse Data
  </div>

  <div class="absolute top-64 left-64 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Publish Paper
  </div>

  <div class="absolute top-80 left-80 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Project Ends
  </div>

  <FancyArrow x1="20" y1="40" x2="60" y2="84" arc="-0.4" head-size="15" />
  <FancyArrow x1="85" y1="105" x2="125" y2="150" arc="-0.4" head-size="15" />
  <FancyArrow x1="150" y1="170" x2="190" y2="212" arc="-0.4" head-size="15" />
  <FancyArrow x1="210" y1="230" x2="255" y2="275" arc="-0.4" head-size="15" />
  <FancyArrow x1="270" y1="295" x2="320" y2="340" arc="-0.4" head-size="15" />

</div>

::

<!--
Highly unrealistic; also treats software developed as disposable; software increasingly DEMANDED to be open access published by journals, reproduce your results

Understandable… there has been a crisis in confidence of the publishing model - the reproducilbiity crisis;
-->

---

# In reality...

::centralise::

::center

<div class="relative h-90 w-140">

  <!-- Cascading boxes -->
  <div class="absolute top-0 left-0 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Research Questions
  </div>

  <div class="absolute top-16 left-16 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Develop Software
  </div>

  <div class="absolute top-32 left-32 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Run Software
  </div>

  <div class="absolute top-48 left-48 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Analyse Data
  </div>

  <div class="absolute top-64 left-64 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Publish Paper
  </div>

  <div class="absolute top-80 left-80 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Project Ends
  </div>
  
  <div class="absolute top-77 left-130 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Graceful Decline
  </div>

  <!-- Forward paths -->
  <FancyArrow x1="20" y1="40" x2="60" y2="84" arc="-0.4" head-size="15" />
  <FancyArrow x1="85" y1="105" x2="125" y2="150" arc="-0.4" head-size="15" />
  <FancyArrow x1="150" y1="170" x2="190" y2="212" arc="-0.4" head-size="15" />
  <FancyArrow x1="210" y1="230" x2="255" y2="275" arc="-0.4" head-size="15" />
  <FancyArrow x1="270" y1="295" x2="320" y2="340" arc="-0.4" head-size="15" />
  <FancyArrow x1="462" y1="340" x2="517" y2="340" head-size="15" />

  <div class="absolute top-40 left--40 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Project Partners
  </div>
  <div class="absolute top-60 left--10 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Industry
  </div>
  <div class="absolute top-80 left-10 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
    Other People
  </div>


  <!-- Project partners -->
  <FancyArrow x1="-70" y1="155" x2="-5" y2="15" arc="0.4" head-size="15" color="gray" />
  <FancyArrow x1="-40" y1="200" x2="125" y2="150" arc="-0.3" head-size="15" color="gray"/>
  <FancyArrow x1="-70" y1="155" x2="60" y2="84" arc="0.4" head-size="15" color="gray"/>
  <FancyArrow x1="-40" y1="200" x2="190" y2="212" arc="-0.2" head-size="15" color="gray"/>

  <!-- Industry -->
  <FancyArrow x1="0" y1="235" x2="-5" y2="15" arc="0.4" head-size="15" color="gray"/>
  <FancyArrow x1="0" y1="235" x2="125" y2="150" arc="-0.3" head-size="15" color="gray"/>
  <FancyArrow x1="0" y1="235" x2="60" y2="84" arc="0.4" head-size="15" color="gray"/>
  <FancyArrow x1="60" y1="260" x2="190" y2="212" arc="-0.2" head-size="15" color="gray"/>

  <!-- Other people -->
  <FancyArrow x1="120" y1="320" x2="-5" y2="15" arc="0.4" head-size="15" color="gray"/>
  <FancyArrow x1="120" y1="320" x2="125" y2="150" arc="-0.3" head-size="15" color="gray"/>
  <FancyArrow x1="120" y1="320" x2="60" y2="84" arc="0.4" head-size="15" color="gray"/>
  <FancyArrow x1="120" y1="320" x2="190" y2="212" arc="-0.2" head-size="15" color="gray"/>

  <!-- Backpaths -->
  <FancyArrow x1="430" y1="315" x2="205" y2="15" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="370" y1="250" x2="205" y2="15" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="370" y1="250" x2="250" y2="80" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="300" y1="190" x2="250" y2="80" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="300" y1="190" x2="205" y2="15" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="250" y1="125" x2="250" y2="80" arc="-0.4" head-size="15" color="gray"/>
  <FancyArrow x1="85" y1="105" x2="255" y2="275" arc="-0.4" head-size="15" color="gray"/>

</div>

<div v-click class="absolute top-30 left-130 text-left inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
  What happens when…
  <ul>
  <li>You have a follow-on project?</li>
  <li>Someone else wants to use your code?</li>
  <li>Someone wants to reproduce your results?</li>
  </ul>
</div>

<div v-click class="absolute top-10 left-80 inline-block border border-gray-400 bg-white px-3 py-1 rounded shadow">
  When should you have considered how to engineer your software?
</div>

::

<!--
Project partners: MSc, undergrad, different version of software

End of process of continual iteration we publish a paper; even then the software doesnt die, supports the lab for the next 5-10 years in various guises.
-->

---

# Legacy code

::center
<img src="../img/phdcomics-code.png" alt="Classroom" style="width: 80%;"/>
::

<v-clicks at="0" every="2">

- What are your experiences re-running or adjusting a script you created few months ago?
- Have you continued working from a previous student's code?
- Are you afraid to alter existing code for fear of it breaking?

</v-clicks>

---

# The software you write is important!

::centralise::

- Software inherently contains value
  - Produces results, contains lessons learnt, effort

- Difficult to gauge to what extent it might be used in the future
  - By who?
  - Which parts?
  - Which projects?
  - Reproducibility – from publications!

Can it / should it be reusable by others... including yourself?

<div class="absolute top-40 right-10 w-70">
  <img src="../img/usage-pyramid.png" alt="Classroom" style="width: 100%;"/>
</div>
