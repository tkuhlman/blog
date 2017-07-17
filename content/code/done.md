---
date: "2017-07-17"
title: Done Criteria
type: post
tags: [checklist]
---
A checklist list of done criteria is helpful to avoid skipping any steps in code creation, this is the list I use for my projects.
Where possible automated tools should be used to help verify good practices are followed.
These tools are typically language specific so I skipped adding any here.
<!--more-->

## Ready for Review

- [ ] Committed with a good commit message to appropriate branches as determined by the teams source control practices.
- [ ]  The code works and shows that by being well covered with automated tests, some combination of unit and/or integration tests as appropriate.
- [ ] Quality, including:
  - [ ] The code has good style and has been lint checked.
  - [ ] Simplicity, the code is easy to read and maintain, avoids complexitiy and is focused on solving a single problem.
  - [ ] All errors are handled.
- [ ] Documented - design and implementations documented in or close to the code as needed.
- [ ] Metrics exposed, healthcheck exposed.

## Ready for Deployment

- [ ] Reviewed and merged.
- [ ] Tested in a staging environment.
- [ ] Demoed and approved by product owner.

## Done

- [ ] Dashboards for metrics created.
- [ ] Alerts in place.
- [ ] Runbook for alerts created
- [ ] Documented - All relevant user and administration documentation is in place.
- [ ] Live
