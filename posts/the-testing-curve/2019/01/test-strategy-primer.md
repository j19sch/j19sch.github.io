<html><body><p class="has-small-font-size"><em>I originally wrote this primer to share with people at work. The first section is intended to be generally applicable; the second not necessarily so. The main influences on this primer are:<br>- Rapid Software Testing's </em><a href="https://www.satisfice.com/tools/htsm.pdf"><em>Heuristic Test Strategy Model</em></a><em><br>- James Lyndsay's </em><a href="http://www.workroom-productions.com/papers/Exploration%20and%20Strategy.pdf"><em>Why Exploration has a place in any Strategy</em></a><em><br>- Rikard Edgren's </em><a href="http://www.thetesteye.com/papers/TheLittleBlackBookOnTestDesign.pdf"><em>Little Black Book on Test Design</em></a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>This document contains two sections:</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><em>Why have a test strategy?</em> - what is a test strategy and what’s its purpose</li><li><em>Test strategy checklist</em> - checklist for describing your test strategy</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>Why have a test strategy?</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The purpose of a test strategy is to answer the question: <em>“How do we know that what we are building, is good enough?”</em> As such, every team has a test strategy, even if it’s only implicitly defined through the actions of the team members.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The value of documenting your test strategy is to create an explicit shared understanding of your strategy among your stakeholders (that includes you as team members) . So your test strategy document should be a living document, a tool that helps you deliver software better.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>A good test strategy is characterized by diverse half-measures: diversity is often more important than depth.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>“How do we know that what we are building, is good enough?”</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><strong>“what we are building”</strong><br>You can look at what we are building from different perspectives:<br>- a piece of code<br>- one or more components<br>- a feature<br>- a capability<br>- a product</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>“good</strong>”<br>A good way to approach this is to split up “good” in different quality attributes such as capability, security, maintainability. Two good checklists with quality attributes are:<br>- The Test Eye's <a href="http://thetesteye.com/posters/TheTestEye_SoftwareQualityCharacteristics.pdf">Software Quality Characteristics</a><br>- The Heuristic Test Strategy Model's <a href="https://www.satisfice.com/tools/htsm.pdf">Quality Criteria Categories</a> (page 5)<a rel="noreferrer noopener" target="_blank" href="https://www.satisfice.com/tools/htsm.pdf"></a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>“good enough”</strong><br>Something is good enough when it provides sufficient value at low enough risk. Exactly where to draw that line, is a decision for the team’s stakeholders.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Evaluating value starts from our expectations, e.g. acceptance criteria. It’s about showing that something works, that it provides the value we want it to provide. Scripted approaches, i.e. the test is largely or completely defined beforehand, work well in this area - especially when you can define these in code instead of manual instructions.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Evaluating risk starts from the thing we are building. It’s about looking for problems, that what we’re building is not doing things we don’t want it to do. Exploratory approaches work well in this area, because you don’t know beforehand what exactly you are looking for.<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>A few important things to note:<br>- The two approaches (scripted versus exploratory) exist in a continuum. When testing, you move within this continuum.<br>- Both approaches can be applied to any level or across levels of your stack.<br>- Both approaches benefit greatly from using different kinds of tools.<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>“how do we know”</strong><br>What are the things we do?<br>- static testing (code does not need to run), examples: code review, code analysis.<br>- dynamic testing (code needs to run), examples: unit testing, system testing, performance testing.<br>- monitoring (product is used by customers), examples: log alerts, server monitoring, support tickets dashboard.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Test strategy checklist</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>Products &amp; components</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What product(s) do we contribute to?</li><li>Why would our company want to have these products?</li><li>What components of those products are we responsible for?</li><li>Critical dependencies of our components:<ul><li>What do our components depend on?</li><li>What has dependencies on our components?</li></ul></li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Feature testing</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What testing is done while developing a feature?<ul><li>which quality characteristics do you focus on?</li><li>what levels of the stack and/or which components are part of the test?</li><li>what testing is done as part of a pipeline (see below)?</li></ul></li><li>What testing have you decided <strong>not</strong> to do, i.e. is not in scope?</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Release testing</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What testing is performed on the release candidate?<ul><li>which quality characteristics do you focus on?</li><li>what levels of the stack and/or which components are part of the test?</li><li>what testing is done as part of a pipeline (see below)?</li></ul></li><li>To what degree do you repeat your feature testing during release testing?</li><li>What testing have you decided <strong>not</strong> to do, i.e. is not in scope?</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>CI/CD pipeline(s)</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What is covered by the pipeline(s)?<ul><li>code analysis</li><li>auto-tests</li><li>deployment</li></ul></li><li>When/how are they triggered?<ul><li>schedule</li><li>commits, merge requests, …</li></ul></li><li>Is there a dashboard?</li><li>What happens if a pipeline goes red?</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Testing done by others</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What testing is done by others?<ul><li>Examples: security testing by a 3rd party, beta-releases.</li></ul></li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Monitoring</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>How do you monitor your production environment(s)?<ul><li>Examples: server metrics, logs, user analytics, support tickets.</li></ul></li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Impediments</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>What is slowing down your testing?<ul><li>Examples: architecture, design, skills, tools, team capacity.</li></ul></li></ul>
<!-- /wp:list --></body></html>