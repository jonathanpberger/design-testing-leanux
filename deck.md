class: center middle

# Hi :-)

---

# Towards a Theory and Methodology of Test-Driven Design
Jonathan Berger, 2015

Mobile Central Europe, Warsaw

---

## Who Am I?

- @jonathanpberger
- ~30 agile projects since 2008
- design, code, pm
- interested in agile practice for design

---

## Who are you?
Show of hands:

--

- Designer?

--

- Developer?

--

- What else?

---


## What it says on the tin

> Years ago, Developers had problems and devised Agile techniques to address them. Today, Designers face similar problems. Can we adopt similar techniques? In this talk, we’ll explore what automated testing might look like for design. What would it look like to have a more defined definition of “done” for design? What if designers could refactor with impunity? We’ll explore testing possibilities for Visual design, User Experience design, and front-end engineering, and try to build a testing pyramid for design.

---

class: center, middle

# WARNING: "Testing" is a messy word.

???

- In the design context, it usually means User Testing
- User Testing is a part of this, but we're talking about a lot more


---

# Hypotheses:

- Designers can learn from Agile Development
- It won't be an exact 1:1 mapping, so we have to adapt
- Tooling and practice (TDD and CI) is currently the biggest boulder in the road

---

# Goal of this Talk
- Suggest the possibilities of TDD for design
- Spread the word about the tools out there
- Make the case that we need more than automated tools: we need a theory and plan

---

# The Plan
- Agile and Design
- Theory of TDDesign: Why is it Useful?
- Methodology of TDDesign: How might it be done?
- What can you do?

---

class: center, middle, inverse
# Agile and Design

---
class: center, middle
name: problems
## Developers had problems

---
### Agile Manifesto Principles
--

> - Our highest priority is to *satisfy the customer* through early and continuous delivery of valuable software.
--

- *Welcome changing requirements*, even late in development. Agile processes harness change for the customer's competitive advantage.
--

- *Deliver working software frequently*, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
--

- Business people and developers must *work together daily* throughout the project.
--

- Build projects around motivated individuals. Give them the environment and support they need, and *trust them* to get the job done.
- The most efficient and effective method of conveying information to and within a development team is *face-to-face conversation*.
--

- *Working software* is the primary measure of progress.
- Agile processes promote *sustainable development*. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
- Continuous attention to *technical excellence* and good design enhances agility.
--

- *Simplicity*--the art of maximizing the amount of work not done--is essential.
- The best architectures, requirements, and designs emerge from *self-organizing teams*.
- At regular intervals, *the team reflects* on how to become more effective, then tunes and adjusts its behavior accordingly.

---

(Shorter) 

###[Principles Behind the Agile Manifesto](http://www.agilemanifesto.org/principles.html)

---

.smaller[
(Shorter) 

### [Principles Behind the Agile Manifesto](http://www.agilemanifesto.org/principles.html)
]

.left-column-equal[

### Things that hurt:

- Changing requirements
- Seagull management
- Low-fidelity (or lack of) communication
- Doing unnecessary work
- Infrequent delivery
- Sclerotic process
- Unsustainable pace

]

--

.right-column-equal[
### What "hurt" looks like:

- Backlog churn
- Changing requirements after the work is done
- Not knowing what to build
- Building the wrong thing
- Monthly or Quarterly releases
- broken process
- late nights, weekends

]

---

.smaller[
(Shorter) 

### [Principles Behind the Agile Manifesto](http://www.agilemanifesto.org/principles.html)
]

.left-column-equal[
### The Result:
- Time is wasted on distractions
- Motivation wanes
- High cost of change is bad for business
- Customers aren't satisfied

]

--

.right-column-equal[

### What Results look like:
- Business asking "What are they doing?!"
- Developers are bored and upset
- Software is unresponsive to business needs
- Customers aren't satisfied

]

---

class: center, middle, inverse

## SPOILER: Designers have many of the same problems today!

---

## Developers' Solution: The [Agile Manifesto](http://www.agilemanifesto.org/)

> 
- *Individuals and interactions* over processes and tools
- *Working software* over comprehensive documentation
- *Customer collaboration* over contract negotiation
- *Responding to change* over following a plan

> 
.small[That is, while there is value in the items on
the right, we value the items on the left more.]

---
layout: true
## What does Agile mean in practice?

---

### Continuously
- Outside-In Development
- Optimize for Low Cost Of Change
- Optimize for tight feedback loops

---

### Weekly Cadence
- Standups
- Retros
- IPMs => storywriting
- release planning => Big Design Refactor

---

### Daily Cadence
- Pairing
- TDD
- CI

---
layout: false
class: center, middle
## Designers have Problems

--

1. Brittle styles at the implementation layer (CSS)
2. Unintended design regressions (especially in cross-browser or responsive contexts)
3. trouble abstracting design decisions from design spandrels/affordances
4. Trouble defining "done" for a design

<!-- TODO: this is the core; link it up to the current work being done and what's missing

1. Brittle CSS could be linting
2. Regression-proofing could be wraith
3. Asserting decisions could be cactus
4. Defining done could be the missing bit. Automation? CI?

or, more abstractly, the problems are:

1. consistency
    + code (addressed by linting)
    + elements (addressed by style guides)

2. unintended regressions - FE
    + this is fundamentally slippage between asserting design and implementing design

3. ontological design - UI, VxD
    - in different contexts
        + cross-browser
        + responsive
        + 
4. asking the right question - Product Design

 -->

---

<!-- EDIT: Not sure I need this -->

.smaller[
### The same things hurt Designers!
]

.left-column-equal[

### Things that hurt:

- Changing requirements
- Seagull management
- Low-fidelity (or lack of) communication
- Doing unnecessary work
- Infrequent delivery
- Sclerotic process
- Unsustainable pace
]

--

.right-column-equal[
### What "hurt" looks like for designers:

- Backlog churn
- Changing requirements after the work is done
- Not knowing what to design
- Designing the wrong thing
- Monthly or Quarterly releases
- broken process
- late nights, weekends

]

---

.left-column-equal[

### The Result:
- Time is wasted on distractions
- Motivation wanes
- High cost of change is bad for business
- Customers aren't satisfied

]

--

.right-column-equal[

### What Results look like:
- Business asking "What are they doing?!"
- Designers are bored and upset
- Design is unresponsive to business needs
- Customers aren't satisfied

]

---

layout: true
.left-column[
## What Could Agile Design mean in practice?
]

---

--

.right-column[
### Continuously
- √ Outside-In Development => User-Centered Design
- √ Optimize for Low Cost of Change => Design systems, not pages ([Atomic Design][])
- √ Optimize for Tight Feedback Loops => Research, User Testing
]

--

.right-column[
### Weekly Cadence
- √ Standups: doing it!
- √ Retros: doing it!
- √ IPMs => storywriting
- √ release planning => Big Design Refactor
]

--

.right-column[
### Daily Cadence
- √ Pairing: doing it!
- TDD: this talk
- CI: next talk
]

---
layout: true

.left-column[
## What might automated testing look like for design?
]

---

--

.right-column[
### Lots of people are working on this
CSSTe.st catalogs a number of techniques for testing CSS:

- Computed Style
- Frozen DOM
- House styleguide
- Image diff
- Project styleguide
- Reference browser comparison
- Syntax checks

]

--

.right-column[
### Tend to be focused on a few approaches

1. Brittle styles at the implementation layer (CSS)
2. Unintended design regressions (especially in cross-browser or responsive contexts)
3. trouble abstracting design decisions from design spandrels/affordances


- testing CSS
- screenshot diff'ing
- linting
]


--
.right-column[
## What's missing?
]

---

layout: false

## 4. Trouble defining "done" for a design


???
These are concerned with testing CSS rather than testing *design*.

---

Automated testing for CSS isn't enough
without automated testing for Design

---


???
What are the benefits of TDD?

---

- What would it look like to have a more defined definition of "done" for design?
- What if designers could refactor with impunity?

---

<!-- # Interlude: ontology

TODO: PUT ONTOLOGY HERE

---
 -->

# Theory of TDDesign

---

## How can adapting TDD for Design help?

- Force a conversation about what "done" means *before* starting work
- bias towards automation ~= bias towards repeatability (aka scientific method)

<!-- THIS COULD BE A GOOD PLACE FOR MVD or Sus/Obj -->


<!-- ---
class: interlude

# Interlude: Why Do I Care?

---

class: interlude
## origin story

---

class: interlude
## background on this talk: tried to give it before, but wasn't ready

---

class: interlude
## What is design?

(people ask "did you design that shirt?")

---

class: interlude
# </EndInterlude>

---

So...

# What is TDD?
 -->

---

layout: true
## Benefits of TDD

---

> - It gives me **confidence** that my code does what I think it does

> - It confers the **ability to refactor** code without the fear that I have broken something

> - It encourages a testable, and hence **modular, design**

> - The **tests describe the behaviour** of the code

[Paul Wilson](http://www.neo.com/2014/03/20/the-many-faces-of-test-driven-development)

---
`s/code/product`

> - It gives me **confidence** that my product does what I think it does

> - It confers the **ability to refactor** product without the fear that I have broken something

> - It encourages a testable, and hence **modular, design**

> - The **tests describe the behavior** of the product

---
layout: false
## TDD: History

<!-- TODO: EXPAND THIS -->

> Kent Beck, who is credited with having developed or 'rediscovered'[1] the technique, stated in 2003 that TDD encourages simple designs and inspires confidence.[2] -<http://en.wikipedia.org/wiki/Test-driven_development>

???

- "rediscovered" by Kent Beck
-  mainframe era
- XP Explained - modern history

<http://www.quora.com/Why-does-Kent-Beck-refer-to-the-rediscovery-of-test-driven-development>
<http://derekbarber.ca/blog/2012/03/27/why-test-driven-development/>

---

# A TDD example: Hamazon.com

---

<!-- !["images/hamazon_item_page.png"]

---
 -->

**Let's say we're Pair Programming...**

---

Our story is

**`User should be able to add Item to Shopping Cart`**

---

## Gherkin

looks a lot like regular English, but with a few magic words:

- **"Given",** 
- **"When",** 
- **"And",** 
- **"Then".**

---

### The Test

    Given I'm a logged-in User
    
    When I go to the Item Page
    
    And I tap the "Add Item to Cart" button
    
    Then I should see the Cart Inventory increment
    
    And I should see the Cart Sub-Total increment
    
    And I should see the Warehouse Inventory decrement

---

- readable by the computer
- each line will fail or pass individually.

---

### run the test. Red! What happens?
.right-column[
.green[`Given I'm a logged-in User`]


.green[`When I go to the Item Page`]


.red[`And I tap the "Add Item to Cart" button`]
]

???

- (Let's say by this point we've already written the User login system, so that line goes green.) 
- (...And let's say we've already written the Item Page, so that line goes green.) 
- (there is no "Add Item to Cart" button, so that should fail.) 

---
# make it green
- go into the part of the codebase which has front-end HTML views, 
- find the Item Page, and 
- add `<button>Add Item to Cart</button>`. 

---

*That's it.* 

???
No mucking with the database. The button isn't hooked up to anything. All we're trying to do is make the test pass, line by line.

---

run the test again:
`Given I'm a logged-in User`...GREEN!
`When I go to the Item Page`...GREEN!
`And I tap the "Add Item to Cart" button`...now that'll be green too!
`Then I should see the Cart Inventory increment` will fail. 

---

wire the `<button>` you just made in the front-end view up to the database, so that the Cart Inventory increments. 
  
---
  
Then we'll run the test again, the `Cart Inventory` line will pass, then next line (`Cart Sub-Total`) will fail, you'll make it pass, etc. etc. 

---

In this manner, the whole feature will be written according to a plain-Engish User Story that anyone can read—including a non-technical Product Manager or client stakeholder—without any over-engineering or extra work.

---

### Running Suite


???
Now here's the fun part. Remember how we said we already built the User Login system and the Item Page? Those features will have tests too. In fact, close to 100% of the codebase is under test. So now that we've TDD'd a new feature and it's test is green, we'll run the entire Test Suite—every test that's been written to date. We already know that our feature works on its own, but now we'll get to see whether it integrates with the rest of the software.


---

### We broke suite!

???
We'll kick off the full test run, and it'll take a few minutes to run all the tests. Now's a great time to get up, stretch our legs, grab a drink, maybe play a game of ping pong. When we return, the test suite is red! It turns out that when we decremented Warehouse Inventory, we broke part of the warehouse management system that had already been written. Now we'll go fix our code (writing additional tests as necessary) and repeat the process until the test suite is green. Once suite is green, we can push our code to production with confidence that the software will act as expected. In this manner, we mitigate technical risks and let deployment be a purely business decision.
---

Fix it, run again, go green: Red, Green, Refactor.

---

I didn't go into detail here, but the Cuke tests drive out the Unit tests! Colud design testing do the same?

---
class: interlude
# <Interlude>: TDD & Pairing

---

class: interlude
## Ping Pong Pairing
- How does it work?
- how would TDD help Design Pairing?

---

class: interlude
# </End Interlude>

---

# Methodology of TDDesign

???

How might it be done?

---

## Tools being experimented with now

### 1. Consistency
- Code: CSSLint, JSLint, etc.
- Elements: StyleCop, others

---

### 2. Unintended Regressions

Screenshot diff tools:

- [Wraith][]
- [Green Onion][]
- [CSSCritic][]
- Frozen DOM: Hardy / Ghoststory


---

### 3. Ontological Design

- [Atomic Design][]
- [Cactus][]

---

class: center, middle
# Pyramid Scheming

???

- test pyramid history: from QA, inverted
- for our purposes: a model of how different tests fit into the picture

what is it?, what do we usually call it?, how do we usually deliver it?, how could we test it?
concept / visual language / metaphor (IA?)
UX / wires

CSS
expression: final app

---

## Dev Testing Pyramid
- 1 ("Functional") Acceptance test
- 10 Integration tests
- 100 Unit tests

???

or

UI
Service
Unit

---

## Design Testing Pyramid

- traditional user testing
<!-- todo: bring in list from UX Recipes -->

- Assert Design Decisions (cactus)
- Control Regressions (green_onion)
- Safely refactor bloated CSS (CSS Racionator)
- Enforce Code Conventions (CSS Lint)
- Enforce personas (persona_dot_yml)
- Enforce Styleguide-Driven Development (style_cop)


---

# Automation is important

???

It lets us build CI
we can start w/ something trivial, and add to it as we learn

---

# recap
- foo 
- bar
- baz

---

# ways forward
- CI for design
- Design Testing Pyramid
- Gherkin-driven mockups
- style-guide driven design


---

# Thanks!

- <http://jonathanpberger.com/talks>
- Say hi on twitter at `@jonathanpberger`
- or `jonathanpberger` on github, gmail, forrst, etc...

---

