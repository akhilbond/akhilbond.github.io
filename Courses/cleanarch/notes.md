---
layout: page
title: Clean Architecture: Patterns, Practices, and Principles
permalink: /Courses/cleanarch/
---

# This course is a Pluralsight course taught by Matthew Renze.

## Introduction

- What is bad architecture?
  - Complex
  - Incoherent
  - Rigid
  - Brittle
  - Untestable
  - Unmaintainable

- What is good architecture?
  - Simple
  - Understandable
  - Flexible
  - Emergent
  - Testable
  - Maintainable

- Clean architecture is architecture that is designed for the inhabitants of the architecture, not the architect or the machine.

- Why invest in clean Architecture?
  - Minimize costs
  - Maximize value
  - Maximize ROI(Return on Interest)

- Clean architecture focuses on
  - Focus on the essentials
  - Builds only what is necessary for business value
  - Optimizes for maintainability

## Domain-centric architecture

- Essential vs Details
  - Domain and use cases are essential
  - Presentation and Persistence is a detail

- Domain-centric architectures
  - Hexagonal architecture
    - The application/domain is at the center of the architecture
    - It is also a plug-in architecture that supports ports and adaptors
  - Onion architecture
    - Domain at center surrounded by application layer
    - No inner layer know about any outer layer
  - Clean architecture
    - The entities/domain are at the center surrounded by the application layer/use cases

- Pros
  - Focus is on the domain
  - Less coupling
  - Allows for Domain Driven Design
- Cons
  - Change is difficult
  - Requires more thought
  - Higher initial cost

- Aggregate root entities - The top most entities with persistent identity in a graph of dependent entities and value objects.

## Application Layer

- What are layers?
  - Levels of abstraction
  - Single-responsibility
  - Isolate roles and skills
  - Multiple implementations
  - Varying rates of change

- Application Layer
  - Implements use cases
  - High-level application knowledge
  - Knows about the domain
  - No knowledge of other layers
  - Contains interfaces

- Layer dependencies
  - Dependency inversion
  - Inversion of control
  - Independent deployability
  - Flexibility and maintainability

- Pros
  - Focus is on use cases
  - Easy to understand
  - Follows DIP

- Cons
  - Additional cost
  - Requires extra thought
  - IoC is counter-intuitive

## Commands and Queries

- Command
  - Does something
  - Should modify state
  - Should not return a value

- Query
  - Answers a question
  - Should not modify state
  - Always returns a value

- Single-database CQRS
  - Single database
  - Commands used domain
  - Queries use database

- Two database CQRS
  - Read and write databases
  - Commands use write DB
  - Queries use read DB
  - Eventual consistency
  - Orders of magnitude faster

- Event sourcing CQRS
  - Store events
  - Replay events
  - Modify entity
  - Store new event
  - Update read database

- Why use CQRS?
  - Pros
    - More efficient design
    - Simpler within each stack
    - Optimized performance

  - Cons
    - Inconsistent across stacks
    - Type 2 is more complex
    - Type 3 might be overkill

## Functional Organization

- Pros
  - Spatial locality
  - Easy to navigate
  - Avoid vendor lock-in

- Cons
  - Lose framework conventions
  - Lose automatic scaffolding
  - Categorical is easier at first

## Microservices

- Microservice architectures
  - Subdivide the system
  - Light-weight APIs
  - Small teams
  - Independent
  - Similar to SOA
  - Size matters

- Pros
  - Less cost for large domains
  - Smaller teams
  - Independence

- Cons
  - Only for large domains
  - Higher up-front cost
  - Distributed system costs
