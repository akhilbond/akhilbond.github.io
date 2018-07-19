---
layout: page
title: Test-driven Development: The Big Picture
permalink: /Courses/TestDev/
---

# This course is a Pluralsight course taught by Jason Olson.

## What is Test Driven Development?

- TDD is a software development process designed to deliver high quality software that end customers need.
- There are many phases in developing software:
  - Analysis
  - Design
  - Development
  - Testing
  - Integration
  - Maintenance(Amounts to about 65% of software costs)

- Maintenance Challenges
  - Code Entropy - Code left over time becomes brittle over time and rigid over time
  - Isolated code ownership - Coders own various parts of code and there is a lack of team empowerment.
  - Infrequent Validation - This software is regression prone and has a high risk of code changes.

- A test is something that verifies that your code works as expected. This could entail verification of quality, performance, reliability, and even functionality. Tests are used to make sure code satisfies requirements, responds correctly to all inputs and has acceptable performance.

- Red-Green-Refactor
  - A cycle that is repeated during software development.
  - Red - Write a test that fails.
  - Green - Write the minimal code necessary to make the system pass the test.
  - Refactor - Clean up code so that it will pass so it is maintainable.

- Why practice TDD?
  - Business Benefits
    - Requirements verification
    - Regression catching
    - Lowering maintenance costs
  - Developer Benefits
    - Design-First mentality
    - Avoiding over-engineering
    - Increasing developer momentum
    - Gaining confidence and experience with code

- Code Kata
  - Kata - An individual training exercises for practitioners of karate and other martial arts

- Test Driven Coding also helps businesses keep focused on the customer.

## Different ways of Testing Applications

- Software is ultimately composed of units of computation. These can be functions, units, dependencies, etc.
- Unit testing tests that each unit works properly in isolation.
- Integration testing tests that units work together.
- Acceptance testing verifies the application at the user's point of view.
- Balanced Testing
  - Unit tests - Extremely fast to setup and test.
  - Integration tests - makes sure units work together and tend to be a bit slower.
  - Acceptance tests - features based testing at the user's point of view. This is the slowest test as it needs several units built before the test can be done.

- Testing Styles
  - Black box testing - The component being tested is in a black box where the tester does not know what is in the component under test.
    - The tests become less brittle.
    - There is a longer setup time, as all of the dependencies must be setup before the test can occur.
  - White box testing - The component being tested is out in the open and the tester can see the data flowing in the unit and can also inject test specific dependencies into the test.
    - Very powerful testing system.
    - The tests become more brittle.

  - Other testing types
    - Penetration testing
    - Boundary testing
    - Fuzz testing
    - Smoke testing
    - Stress testing
    - A/B testing

## Testing Frameworks and Tools

- xUnit family
  - Named after SUnit, the unit testing framework developed in Smalltalk.
  - JUnit is the descendent of SUnit which is widley popular in JVM.
  - NUnit, RUnit, CppUnit, EUnit, PerlUnit, PFPUnit, xUnit.net are spawns from JUnit.
  - Mocha, AVA, py.test, minitest, and FsTest are also all inspired by JUnit testing.

- User Interface Frameworks
  - Selenium
  - Watir
  - Visual Studio Coded UI Test
  - Test Studio
  - Silk Test

- System Frameworks
  - Simian Army
    - Chaos Monkey
    - Latency Monkey
    - Janitor Monkey
    - Doctor Monkey

## Testing Concepts

- Framework concepts
  - Test
  - Test Suites - several tests grouped together
  - BeforeEach hook - can be written before each test in a test suite. This is used to take care of any setup that needs to happen before the test.
  - AfterEach hook - can be written after each test in a test suite. This is used for any cleanup after tests.
  - There are also *Before* and *After* hooks for the entire test suite.

- Verification concepts
  - Assert - allows us to tell the test what values we expect and determines whether a test passes or not.
    - Types of Assertion
      - Boolean("IsTrue") - ```Assert.IsTrue(someBoolean);```
      - IsNull - ```Assert.IsNull(someValue);```
      - AreEqual - ```Assert.AreEqual(3, someValue);```
      - Contains - ```Assert.Contains(obj, someCollection);```
      - StartsWith - ```Assert.StartsWith("foo", someString);```
    - Fluent programming
      - Similar assertion statements, however, the statements flow more logically and are easier to read.
