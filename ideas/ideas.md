# Drafts
- design/design_doc.md is a draft still

- I should at some point link in my medium posts https://medium.com/@tim_20708

# Potential Ideas
- Operational Hygiene
- Expand on the reasons I like Go, github.com/tkuhlman/golang-sig/various/beginners.txt
- Markdown or Asciidoc - use with github and readthedocs
  - I have a love hate relationship with markdown, I like it as text but am generally disappointed in rendering (My lists don't work and I need more empty
    lines in my text generally)
  - Make sure to mention the slidy plugin for asciidoc, it is great.
  - I like asciidoc but haven't been able to escape markdown it is too common for shared projects. Given that I'm just not fully utilizing asciidoc.
- Documentation driven development
  - Any other ideas related to code quality following up on my post about Dev best practices for
    sysadmins.
- Balancing collaboration and engineering. Steering toward synergy without going to far either direction.
- Explore journald and other aspects of systemd in depth.
  - this article intrigued me about journald, http://sysadvent.blogspot.com/2015/12/day-17-grokking-systemd-for-fun-and.html
- Something golang related.

## Non-technical ideas
- The importance of running the service you work on.
  - It proves the product.
  - It bring fast feedback loops that help you to improve the product, as you get immediate clarity on bugs, needed features and annoyances.
  - Reveals scale and operational issues that are difficult to discover any other way.
  - It helps developers truly understand the use cases.
  - Coupled with ci/cd you improve development speed and quality through smaller more automated deploys
  - Increases developer satisfaction through allowing a developer to work hard on something, deploy it and immediately see it used in
    a real installation.
  - Leverages the motivation that naturally comes from being on call and responsible.
- Architects who don't know details are impediments to progress rather than enablers.
- The importance of Velocity in the software industry.
  - Faster to market, faster to fix issues, faster to respond to customers with new features.
  - One key thing you can't sacrifice quality for speed. The speed should be a way to attain quality faster as you recognize nothing goes perfect.
- Teams and tasks should be vertical slices not component/tech based.
  - A team is best with one set of goals but multiple sets of expertise. Ie make product X is the goal, the skills include back end code, ops, ui,
    testing, etc.
  - When breaking down team tasks epics should be vertical slices crossing across components not focused on a component. A focus on a component
    tends to me tunnel vision, missing the big picture, etc. Vertical slices promote cross-pollination of skills, better collaboration, allow
    decentralizing the day to day management tasks.

## Old ideas
- Investigate the security aspect of docker containers. How does it compare to the competition?
  Can I improve it without loosing functionality?
- Talk about the immutable infrastruce CI environment I built for Monasca.
  - Make sure to pull from much of my philosophy on this found in the Readme for the monasca/ci repo.
  - Talk about velocity of code commits and help the CI environment needs to preserve this.
- Building packages. Various ways of doing debs, python packages, etc.
- git
  - workflow, lots of repos versus few, git subtree versus git submodules
- The ~/bin/docker-tips and ~/bin/docker-cleanup should be mentioned. Really just the mess it can become to manage many containers. Ansible really helps out here so mention that and how I can both build and deploy with Ansible.
