class: center middle

# Hi :-)

---

# Towards a Theory & Methodology of <br/> Test-Driven Design

Jonathan Berger, 2015

Lean UX NYC

---

# Who Am I?

- [@jonathanpberger](http://jonathanpberger.com)
- design, code, pm
- ~30 agile projects since 2008
- interested in agile practice for design

---


<!-- - trim "why" intro around "designers have a problem too"
 -->

# What hurts in Design?

- Changing requirements
- "Seagull" management
- Low-fidelity communication => not knowing/agreeing on what to design
- Doing unnecessary work / designing the wrong thing
- broken process
- Unsustainable pace
- working working working and then NEVER releasing

---
class: center, middle

# Origin Story

???

- started as a self-taught designer,
- found Agile and fell in love,
- because it addressed a lot of these problems

---

class: center, middle

# I witnessed Agile making engineers happy

???

- productive too

---
class: inverse, center, middle
# how does that work?

---

# Pairing enables happiness

--

- because we're social mammals
---

# Testing enables pairing

--

- because it answers "what should we do now?"
--

- and "why should a client pay for two people to work on this?"
---

# so...

--

- if agile enables happiness,
--

- and pairing enables agile,
--

- and test-driven development ("TDD") enables pairing,
---

class: center, middle, greenbg

# How do we enable TDD for Design?


???

LET THIS QUESTION HANG

---

# Agenda

I. What are the benefits of TDD?


II. How does TDD work?


III. How could we Test-Drive Design?

---

class: center, middle, warning

## WARNING: "Testing" is a messy word.

???

- In the design context, it usually means User Testing
- User Testing is a part of this, but we're talking about a lot more

---

class: center, middle

.f2[Testing vs. Test-Driving vs. User Testing]

---

class: center, middle, inverse

# I. The Benefits of TDD

---

class: de-em-list

## Benefits of TDD (for product)

- **Allows "done" to be defined** by non-programmers (e.g. using Gherkin "Given/When/Then" stories)
- **Fights scope creep** by preventing over-engineering. You're just trying to make this test pass.
- **Allows a constant health-check**, (i.e., Continuous integration) so you know when the app is broken. Business (not technology) decides when to ship.
- **Lowers the cost of change** so product decisions can iterated on quickly and safely

???

# These are all critical to lean practice

---

class: de-em-list

##  Benefits of TDD (for teams)
- **Standardizes workflow** so as to lower bus-count risk, the cost of training, and the cost of learning new things
- **Helps any teammember quickly understand** what's going on (including new teammembers or Future You)
- **Provides live documentation** that never lies (c.f. "Comments are lies waiting to happen")
- **Allows for refactoring** (implementation changes, outcome doesn't)
- **Improves (API) interfaces and software design**, enforcing SOLID principles, Law of Demeter, etc.

???

- # get away from Ninja Rock Star, towards repeatable empirical scientific methods
- # "Improves design" is analogous to consistnancy, using a grid, etc.


---

class: center, middle, inverse

# II. How does TDD work?

---
class: middle
.f3[A TDD example: ]

# Hamazon.com

---

background-image: url(images/hamazon.png)

---

## Our User Story

.f2[`User should be able to add Item to Shopping Cart`]

---

### Write in Gherkin

Gherkin looks a lot like regular English, but with a few magic words:

- **"Given",**
- **"When",**
- **"And",**
- **"Then".**

---

### Write the Test

```ruby
Given I am a loggedin User
When I go to the Item Page
And I tap the "Add Item to Cart" button
Then I should see the Cart Inventory increment
And I should see the Cart Sub-Total increment
And I should see the Warehouse Inventory decrement
```

---

### Rules of Testing

- Test is readable by the computer
- Each line will fail or pass individually

---
class: center, middle
## TDD Credo: ".red[Red], .green[Green], Refactor"

---

### Write a .red[Red] Test

.green[`Given I'm a logged-in User`]

.green[`When I go to the Item Page`]

.red[`And I tap the "Add Item to Cart" button`]

???

- for this example let's say...
- we've already written the User login
- we've already written the Item Page
- there is no button

---

### Now make it .green[Green!]
- Go into the part of the codebase which has front-end HTML views
- find the `Item Page`
- add a `<button>Add Item to Cart</button>`

---
class: center, middle, inverse
.f3[That's it.]

???
- No mucking with the database.
- The button isn't hooked up to anything.
- just trying to make the test pass, line by line.

---
### Run the test again:

.green[`Given I'm a logged-in User`]

.green[`When I go to the Item Page`]

.green[`And I tap the "Add Item to Cart" button`]

.red[`Then I should see the Cart Inventory increment`]

---

.f3[What next?]

- connect the `<button>` to the database
- `Cart Inventory` should increment
- run the test again

---
layout:true
### Run until done

.green[`Given I'm a logged-in User`]

.green[`When I go to the Item Page`]

.green[`And I tap the "Add Item to Cart" button`]

---

.green[`Then I should see the Cart Inventory increment`]

---

.green[`Then I should see the Cart Inventory increment`]

.red[`And I should see the Cart Sub-Total increment`]

---

.green[`Then I should see the Cart Inventory increment`]

.green[`And I should see the Cart Sub-Total increment`]

.red[`And I should see the Warehouse Inventory decrement`]

---
layout: false
class: middle
# Story is Done!

\* Refactor as necessary

---
class: center, middle

# Running Suite

---

## Now run ALL our tests, together
- All features (e.g. Login, Item Page) have tests
- This test is .green[green], but run the Test Suite
- Did this feature break anything?

???

- take a few minutes, stretch our legs

---
class: center, middle, warning

## We broke suite!

???

- we broke part of the warehouse management system

---

### Refactor!

- Fix (refactor) our code
- (Write additional tests as necessary)
- Repeat until green.
- Push to production

---

### <s>F**k it,</s> Ship It!

- Mitigate technical risks
- Deployment is a purely business decision

---

class: interlude, center, middle

.f1[A note on types of tests]


???

- GUI, integration, unit
- tests can drive out other tests
- testing pyramid describes ratio
- more later on Pyramid

---

class: center, middle, inverse

# III. How could we <br/> Test-drive design?

???

- TODO: Tighten this up. Don't need such an exhaustive catalog of what's going on out there.

---
name: csstest
### People are working on CSS Testing
<http://CSSTe.st> catalogs a number of techniques for testing CSS:

- Computed Style
- Frozen DOM
- House styleguide
- Image diff
- Project styleguide
- Reference browser comparison
- Syntax checks

???

This is their list

---

### Tend to be focused on a few approaches

- Screenshot Diff'ing
- Unit Testing CSS
- Linting

---

### Screenshot Diff'ing

.de-em[Examples using [Wraith][wraith] and [CSS Critic][csscritic]]

.left-column[![](images/wraith.png)]
.right-column[
![](images/css-critic.png)
]

---

### Unit Testing CSS
.de-em[example using [Hardy.io][hardy]]

```ruby
Feature: Website layout test
As a user I want visual consistency on the http://csste.st/ website

Scenario: Content layout
Given I visit "http://csste.st/"
Then "section > p" should have "color" of "rgb(68, 68, 68)"
```

---

### Linting
.de-em[example using [CSS Lint][csslint]]

![](images/csslint.png)

---

### What're the goals here?

1. Catch CSS regressions (especially cross-browser, responsive)
2. Unit-test CSS as proxy for design decisions
3. Ensure code style is consistent

---
class: center, middle
### These are all very practical and tactical

---

class: center, middle
### What's missing?

---

class: middle, center, inverse

.f1[Design!]

???

- These are concerned with testing CSS rather than testing *design*.

---
class: center, middle, greenbg

# Test *DESIGN*, not just implementation
???

- these steps are crucial
- necessary but not sufficient

---
name:methodology
class: center, middle, inverse

# Methodology of TDDesign

<!-- this could be a place for# <Interlude>: TDD & Pairing -->
<!-- this could be a place for# <Interlude>: Ping Pong Pairing -->

???

.f1[So what's the design equivalent?]

---
class: center, middle

## Literal Interpretation for TDDesign

???

- .f2[we looked at Automated design testing tools earlier]
- .f2[can we test-DRIVE with them?]

---
class: center, middle
## KILL? Test-Driving the Technology

---

### Image Diff test-driving

- Red Test: Mockup vs. Screenshot of implementation
- Green Test: Image diff passes

Worth it? Maybe for responsive or X-browser? Style-Guide Driven Design?

???

---

### Unit-Testing CSS test-driving

- Hardy, Quixote, Cactus, etc. could do this
- Tedious to write the tests
- what's the correlation between Design Decisions and CSS rules?

Worth it? Sometimes, especially to protect against regressions

---

### Linting

- Not sure that test-driving applies at all

---

class: middle
.f2[“Everyone is describing the one little piece they’ve created, but don’t explain (or even reference!) the larger concepts of how all of these elements link together.”]

<br/>

— [Frank Chimero, July 2014 Designer News AMA](https://news.layervault.com/comments/74344)

---

class: middle
.f2["Process changes are much more profound then the technology that enables them."]

<br/>

—[John Albin Wilkins, Style-Guide-Driven Development: the new web development](https://www.previousnext.com.au/blog/style-guide-driven-development-new-web-development)

---
class: center, middle
## Test-Driving the Technique

???

# practical examples of TDD thinking improving design today


---
class: center, middle
## What might TDD Design look like across different types {FE, VxD, UI, UX} of design?

<!-- interlude: types of design -->

---
### Visual Design: BDD-Driven Mock Flows

```ruby
As a User
When I go to...
Then I should see...
```

![](images/bdd-driven-mocks.png)

???

# see also Google Ventures' [Story-Centered Design][scd]

---

### UI: Live Style Guides & Compliance

Style-Guide-Driven Design, Style Cop

![](images/patternlab.io.png)

???
- ## style-guide driven design
- ## Stylecop will ensure compliance with hologram
- ## Pattern.io, styleguides.io tackle this area

---

### UX
- Persona.yml
- UserTesting.com, Ethn.io
- Lean Hypotheses

???

- Persona.yml makes personae AC
- UserTesting.com, Ethn.io could be ways to automate via machine
- Hypotheses set up acceptance crit


---
name: automation
class: center, middle
## Automation & Continuous Integration

---
class: middle, center
### To go from "Testing" to "Test Driving", ask

.f3["(How) can this plug into CI?"]

---

### Benefits of CI

- Automation relieves monotony
- Perpetual healthcheck on design, visible to whole team
- Compels team to agree on Definition of Done

---

class: center, middle, inverse
# (Testing) Pyramid Scheme

???

- different kinds of tests
- test pyramid history: from QA, inverted
- for our purposes: a model of how different tests fit into the picture

---
background-image: url(images/testing-pyramid.png)
class: center, middle
.f1[The Testing Pyramid]

<!-- ![](images/testing-pyramid.png) -->

---

name:dev-pyramid

### Development Testing Pyramid
| Strategy Name     | Typical Tool | Testing What? | How Many? |
| ----------------- | ------------ | ------------- | --------- |
| Acceptance Tests  | Cucumber     | GUI           | 1         |
| Integration Tests | Rspec        | API           | 10        |
| Unit Tests        | Rspec        | Methods       | 100       |

---

name:design-pyramid

### Design Testing Pyramid

| Type   | Strategy Name                   | Possible Tool                  | Testing What?            | For every&hellip; | Order of Magnitude |
| -----  | ----------------------------    | ------------------------------ | ------------------------ | ----------------- | -----              |
| UX     | Test Testing                    | [Persona.yml][yml]             | Persona/TDD Integrity    | Persona           | •                  |
| UX     | User Research                   | [Ethn.io][ethnio]              | Product-market fit       | Persona           | ••                 |
| FE     | Cross-Viewport Testing          | [Browserstack][browserstack]   | Responsive Consistency   | Viewport          | ••                 |
| FE     | Screenshot Diff'ing             | [Wraith][wraith]               | Styleguide Compliance    | Component         | ••                 |
| VxD    | Computed Style Unit Testing     | [Hardy][hardy]                 | Ontological Integrity    | Decision          | ••                 |
| VxD    | CSS Unit Testing                | [Quixote][q]                   | Ontological Integrity    | Decision          | ••                 |
| UI,VxD | Styleguide-Driven Dev't         | [Stylecop][stylecop]           | Ontological Integrity    | Decision          | ••                 |
| UI     | Usability Testing               | [Usertesting][usertesting]     | Usability                | Interaction       | ••                 |
| UX     | [Story-Centered Design][scd] CI | **[BUILD ME! :-)][red-ci]**    | Flow Coverage            | User Flow         | ••                 |
| FE     | Cross-Browser Testing           | [Browsershots][browsershots]   | X-browser Consistency    | Browser           | •••                |
| ALL    | BDR Testing                     | **[BUILD ME! :-)][red-ci]**    | Defining 'Done'          | Story             | •••                |
| FE     | Screenshot Diff'ing             | [Wraith][wraith]               | Screen Regressions       | Screen            | •••                |
| FE     | Linting                         | [CSSLint][csslint]             | Code Consistency         | Line              | •••                |


---
name: next
class: inverse
# What's Next?
- Continue to improve testing tools
- Socialize the idea of Design Health Check in CI
- Explore where TDD ideas can help design practice as well as tooling




---

# Thanks!

- <http://jonathanpberger.com/talks>
- Say hi on twitter at `@jonathanpberger`
- or `jonathanpberger` on github, gmail, forrst, etc...

---
class: center, middle

# Bonus!

---
name: resources
## Resources

| Concept                   | Resource                                                                             |
| ---------------           | ----------------------------------------------------                             |
| Atomic Design             | <http://bradfrost.com/blog/post/atomic-web-design/>                              |
| Big Design Refactor       | <http://pivotallabs.com/big-design-refactor>                                     |
| CSS Testing               | <http://csste.st>                                                                |
| Design Backlog            | <http://pivotallabs.com/manage-design-backlog/>                                                                |
| Pattern Lab               | <http://patternlab.io/>                                                          |
| Story-Centered Design     | <https://www.gv.com/lib/story-centered-design-hacking-your-brain-to-think-like-a-user>|
| Style Guides              | <http://styleguides.io/>                                                         |
| Style-Guide Driven Design | <http://uxmag.com/articles/anchoring-your-design-language-in-a-live-style-guide> |
| Towards a Theory & Methodology of Test-Driven Design | <http://jonathanpberger.com/talks> |

[boulder]: https://twitter.com/jonathanpberger/status/562926708949803010
[atomic]: http://bradfrost.com/blog/post/atomic-web-design/
[bdr]: http://pivotallabs.com/big-design-refactor
[fixtures]:http://en.wikipedia.org/wiki/Test_fixture
[csscritic]:http://cburgmer.github.io/csscritic/
[phantomcss]: https://github.com/Huddle/PhantomCSS
[hologram]: http://trulia.github.io/hologram/
[browsershots]:http://browsershots.org/
[usertesting]:http://www.usertesting.com/
[ethnio]: http://ethn.io/
[browserstack]: http://browserstack.com
[yml]:https://github.com/jonathanpberger/persona_dot_yml
[stylecop]: https://github.com/pivotal/style_cop
[wraith]: https://github.com/BBC-News/wraith
[csslint]:https://github.com/CSSLint/csslint
[hardy]:http://hardy.io/
[q]:https://github.com/jamesshore/quixote
[red-ci]: https://twitter.com/jonathanpberger/status/563123069435535361
[scd]: https://www.gv.com/lib/story-centered-design-hacking-your-brain-to-think-like-a-user
[design backlog]: http://pivotallabs.com/manage-design-backlog/
[spandrels]:http://en.wikipedia.org/wiki/Spandrel_%28biology%29
[cargo cult design]:https://twitter.com/hashtag/CargoCultDesign?src=hash
[xp-explained]:http://www.amazon.com/Extreme-Programming-Explained-Embrace-Edition/dp/0321278658
