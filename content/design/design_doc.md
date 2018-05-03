---
date: "2018-05-03T10:42:45-06:00"
title: "Design Docs Best Practices"
type: "post"
draft: true
tags:
  - Design
---

Each project deserves careful thought on the design and architecture of the solution. This is something that should be done at the start of projects and for each major revision. One tool for design and architecting is to write a design doc for each major revision. The audience for these docs includes the team that will do the implementation but also other technical developers and architects within the organization who can give feedback. Design docs brings these advantages to a project:

* The problem to be solved, implementation goals and design decisions with tradeoffs are understood by all involved parties not just the implementors. This also serves to align all interested parties on the primary goals of a project.
* Others can review the design and provide feedback. The is made possible because design docs enable talking about design decisions one step removed from the implementation details allowing for a wider audience to have time to understand and review the process.
* The design doc provides a historic reference on why things were done as they were which can be referenced in the future as the project evolves.
* The design doc provides an intro to a service that allows anyone who will begin working on implementation details an overview that helps them place implementation decisions in the right context and therefore to make the right tradeoff decisions.

### Key Sections
Design docs can vary in their scope and layout according to the project but there should be sections that address the why/what/how questions. The key sections that should be covered include:

* *Why* - Project Goals/Problem Description - This section lays out why this project is being worked on, what is the motivation for spending the time on it. As part of this section you may want to include specific use cases that give a concrete picture on how the project is intended to be used.
* *What* - Requirements and Implementation Goals - Define the requirements for this project and its constraints whether these are non-negotiable technology decisions (ie must integrate with X) or SLAs that we would like to meet. Sometimes it is quite helpful to detail out what is not in scope for this project to prevent unintentional scope creep.
* *How* - Design/Architecture - This is likely the largest section where the primary design decisions are detailed with the reasons for choosing one direction over others that were considered. Where possible include concrete data that led to these design decisions. Also try and cover all the major aspects to a service including the operational characteristics such as monitoring and security as well as the good architecture considerations and practices allow the project to be evolvable in the future.

### Examples
