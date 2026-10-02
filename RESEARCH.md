# Chapter 8 Software Testing: research notes

Study notes behind the slideshow. They follow the lesson slides (Western University, Software Engineering, instructor Roeun Mesa), which are based on Chapter 8 of Ian Sommerville's *Software Engineering* (10th edition). Material marked **added** goes beyond the lesson slides.

## 8. Introduction

- Testing has two goals:
  - **Verification**: the software conforms to its specification (functional and non-functional requirements). Boehm (1979): *"Are we building the product right?"*
  - **Validation**: the software does what the customer really requires. Boehm: *"Are we building the right product?"*
- The goal of V&V is **confidence that the system is fit for purpose**, not proof that it has no defects.
- **Added:** Sommerville lists three things that decide how much confidence is needed: the software's purpose (how critical it is), user expectations, and the marketing environment (time to market).
- **Added:** Dijkstra (1970): *"Program testing can be used to show the presence of bugs, but never to show their absence!"*
- **Inspections vs testing.** Inspections are static (the code isn't run) and can be applied to requirements, architecture, UML models, database schemas and programs. Testing is dynamic and applies to the program and prototypes. **Added:** advantages of inspections: one error can't mask another, incomplete versions can be inspected, and they also check standards, portability and maintainability. They can't check performance or usability, so they complement testing.
- **Input-output model.** Validation testing uses expected inputs to show the system works. Defect testing looks for the inputs (Iₑ) that cause outputs revealing defects (Oₑ).

## 8.1 Development testing

Done by the development team; mainly defect testing. Three levels:

| Level | What is tested | Key idea |
|---|---|---|
| Unit (8.1.1) | Functions, methods or object classes in isolation | Cover every operation, every attribute, every state |
| Component (8.1.3) | Several units behind one interface | Test the interface, assuming the units already passed |
| System (8.1.4) | All components integrated | Test the interactions between components |

- **Automated unit tests** have three parts: setup, call, assertion. Mock objects stand in for slow or unfinished dependencies (**added**).
- **Choosing unit test cases (8.1.2).** Two kinds: tests that show normal behaviour and tests that expose defects. Two strategies: partition testing and guideline-based testing.
- **Partition example (added, from Sommerville).** A program accepts 4 to 10 inputs, each a five-digit integer from 10000 to 99999. Test counts 3, 4, 7, 10, 11 and values 9999, 10000, 50000, 99999, 100000. Boundaries are where bugs cluster.
- **Guidelines (added, Whittaker 2009).** Force every error message; overflow input buffers; repeat inputs; force invalid outputs; force results too large or too small. For sequences: single value, different sizes, first/middle/last elements, zero length.
- **Interface types (added):** parameter, shared memory, procedural, message passing. **Interface errors:** misuse, misunderstanding, timing errors.
- **System testing (added):** use-case-based testing with sequence diagrams; emergent behaviour only appears once components run together.

## 8.2 Test-driven development

- Testing and code development are interleaved (Beck 2002; Jeffries and Melnik 2007).
- Process (Figure 8.9): identify new functionality, write a test, run it (it fails), implement and refactor, run again, and when it passes move to the next piece. Developers call this **red, green, refactor**.
- Benefits: code coverage, regression testing, simplified debugging, system documentation.
- **Added:** Sommerville notes TDD is most useful for new development and harder to apply to large legacy systems and multithreaded code.

## 8.3 Release testing

- The final testing stage before release. Goal: ready for deployment and meeting user requirements and performance standards.
- **Added:** differs from system testing because a separate team does it and its aim is validation (good enough to release), not finding bugs. Usually black-box.
- **Requirements-based testing (8.3.1):** derive tests for each requirement. Example: a banking transfer must complete in under 5 seconds.
- **Scenario testing (8.3.2):** walk a realistic end-to-end story. Example: upload a photo, tag friends, add a caption, share it.
- **Performance testing (8.3.3):** load (expected load), stress (beyond the design limit, to check failure behaviour) and scalability (growth). "Load" can mean users, transactions or data volume.

## 8.4 User testing

- Users or customers give input on system testing. Needed because the user's environment affects reliability, performance, usability and robustness.
- **Alpha:** users work with developers at the developer's site. **Beta:** an early release goes to users to experiment and report problems. **Acceptance:** the customer formally decides whether to accept (and pay for) the system.
- **Added:** six-stage acceptance process: define acceptance criteria, plan acceptance testing, derive acceptance tests, run acceptance tests, negotiate test results, accept or reject the system. In agile methods the customer is part of the team and acceptance tests are automated from user stories.

## Real-world case studies (added)

| Year | Failure | Impact | Link to the chapter |
|---|---|---|---|
| 1996 | Ariane 5 Flight 501: 64-bit float converted to a 16-bit integer in reused code | Rocket destroyed about 40 s after lift-off; over $370M | Boundary values, re-testing reused components |
| 1999 | Mars Climate Orbiter: pound-force seconds vs newton seconds between two modules | $327.6M probe lost | Interface misunderstanding |
| 2012 | Knight Capital: new code on 7 of 8 servers; old code reactivated | $440M lost in 45 minutes | Release and regression testing |
| 2024 | CrowdStrike Falcon update: 21 input fields where the code expected 20 | About 8.5 million Windows devices crashed | Invalid-input testing, staged rollout |

CISQ estimated the cost of poor software quality in the US at about **$2.41 trillion in 2022**.

## Small corrections to the original slides

- The 8.3.1 slide's last bullet ("the tester follows these exact steps… uploading, tagging, adding captions") describes the social media example, so the deck places it under scenario testing (8.3.2).
- "Regression testing: checks that new changes or additions to code" is completed as "…don't break existing code".
- "Agile and Develops" in the conclusion is corrected to "Agile and DevOps".

## Sources

1. Sommerville, I. (2016). *Software Engineering*, 10th ed., Chapter 8. Pearson.
2. Beck, K. (2002). *Test Driven Development: By Example*. Addison-Wesley.
3. Jeffries, R. and Melnik, G. (2007). TDD: The art of fearless programming. *IEEE Software* 24(3).
4. Whittaker, J. A. (2009). *Exploratory Software Testing*. Addison-Wesley.
5. Dijkstra, E. W. (1970). *Notes on Structured Programming* (EWD249).
6. CISQ (2022). [The Cost of Poor Software Quality in the US: A 2022 Report](https://www.it-cisq.org/the-cost-of-poor-quality-software-in-the-us-a-2022-report/).
7. ESA (1996). [Ariane 501: Presentation of Inquiry Board report](https://www.esa.int/Newsroom/Press_Releases/Ariane_501_-_Presentation_of_Inquiry_Board_report).
8. Congressional Research Service (2024). [IT Disruptions from CrowdStrike's Update: FAQ (R48135)](https://www.congress.gov/crs-product/R48135).
9. NASA (1999). Mars Climate Orbiter Mishap Investigation Board, Phase I Report.
10. U.S. SEC (2013). Order in the matter of Knight Capital Americas LLC.
