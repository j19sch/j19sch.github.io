<!--
.. title: Test strategy primer
.. slug: test-strategy-primer
.. date: 2019-01-29 21:34:19 UTC+01:00
.. tags: test strategy, test management, context-driven testing
.. category: test strategy
.. link: 
.. description:
.. type: text
-->

*I originally wrote this primer to share with people at work. The first section is intended to be generally applicable; the second not necessarily so. The main influences on this primer are:*  
*- Rapid Software Testing's [Heuristic Test Strategy Model](https://www.satisfice.com/tools/htsm.pdf)*  
*- James Lyndsay's [Why Exploration has a place in any Strategy](http://www.workroom-productions.com/papers/Exploration%20and%20Strategy.pdf)*  
*- Rikard Edgren's [Little Black Book on Test Design](http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf)*

This document contains two sections:

- Why have a test strategy? - what is a test strategy and what's its purpose
- Test strategy checklist - checklist for describing your test strategy


## Why have a test strategy?
The purpose of a test strategy is to answer the question: "How do we know that what we are building, is good enough?" As such, every team has a test strategy, even if it's only implicitly defined through the actions of the team members.

<!-- TEASER_END -->

The value of documenting your test strategy is to create an explicit shared understanding of your strategy among your stakeholders (that includes you as team members) . So your test strategy document should be a living document, a tool that helps you deliver software better.

A good test strategy is characterized by diverse half-measures: diversity is often more important than depth.

### "How do we know that what we are building, is good enough?"

#### "what we are building"
You can look at what we are building from different perspectives:

- a piece of code
- one or more components
- a feature
- a capability
- a product

#### "good"
A good way to approach this is to split up "good" in different quality attributes such as capability, security, maintainability. Two good checklists with quality attributes are:

- The Test Eye's [Software Quality Characteristics](http://thetesteye.com/posters/TheTestEye_SoftwareQualityCharacteristics.pdf)
- The Heuristic Test Strategy Model's [Quality Criteria Categories](https://www.satisfice.com/tools/htsm.pdf) (page 5)

#### "good enough"
Something is good enough when it provides sufficient value at low enough risk. Exactly where to draw that line, is a decision for the team's stakeholders.

Evaluating value starts from our expectations, e.g. acceptance criteria. It's about showing that something works, that it provides the value we want it to provide. Scripted approaches, i.e. the test is largely or completely defined beforehand, work well in this area - especially when you can define these in code instead of manual instructions.

Evaluating risk starts from the thing we are building. It's about looking for problems, that what we're building is not doing things we don't want it to do. Exploratory approaches work well in this area, because you don't know beforehand what exactly you are looking for.

A few important things to note:

- The two approaches (scripted versus exploratory) exist in a continuum. When testing, you move within this continuum.
- Both approaches can be applied to any level or across levels of your stack.
- Both approaches benefit greatly from using different kinds of tools.

#### "how do we know"
What are the things we do?

- static testing (code does not need to run), examples: code review, code analysis.
- dynamic testing (code needs to run), examples: unit testing, system testing, performance testing.
- monitoring (product is used by customers), examples: log alerts, server monitoring, support tickets dashboard.

## Test strategy checklist

### Products & components
- What product(s) do we contribute to?
- Why would our company want to have these products?
- What components of those products are we responsible for?
- Critical dependencies of our components:
	- What do our components depend on?
	- What has dependencies on our components?

### Feature testing
- What testing is done while developing a feature?
	- which quality characteristics do you focus on?
	- what levels of the stack and/or which components are part of the test?
	- what testing is done as part of a pipeline (see below)?
- What testing have you decided **not** to do, i.e. is not in scope?

### Release testing
- What testing is performed on the release candidate?
	- which quality characteristics do you focus on?
	- what levels of the stack and/or which components are part of the test?
	- what testing is done as part of a pipeline (see below)?
- To what degree do you repeat your feature testing during release testing?
- What testing have you decided **not** to do, i.e. is not in scope?

### CI/CD pipeline(s)
- What is covered by the pipeline(s)?
	- code analysis
	- auto-tests
	- deployment
- When/how are they triggered?
	- schedule
	- commits, merge requests, ...
- Is there a dashboard?
- What happens if a pipeline goes red?

### Testing done by others
- What testing is done by others?
	- Examples: security testing by a 3rd party, beta-releases.

### Monitoring
- How do you monitor your production environment(s)?
	- Examples: server metrics, logs, user analytics, support tickets.

### Impediments
- What is slowing down your testing?
	- Examples: architecture, design, skills, tools, team capacity.