# Potential Ideas
- containers natively and how I haven't touched vagrant since going back to Linux on the desktop. I talked about this some in my post about docker for
  messy pets but could expand on how I have left vagrant behind and haven't minded.
- Markdown or Asciidoc - use with github and readthedocs
  - I have a love hate relationship with markdown, I like it as text but am generally disappointed in rendering (My lists don't work and I need more empty
    lines in my text generally)
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
- Talk about the immutable infrastruce CI environment I built for Monasca.
  - Make sure to pull from much of my philosophy on this found in the Readme for the monasca/ci repo.
  - Talk about velocity of code commits and help the CI environment needs to preserve this.
- Building packages. Various ways of doing debs, python packages, etc.
- git
  - workflow, lots of repos versus few, git subtree versus git submodules
- The ~/bin/docker-tips and ~/bin/docker-cleanup should be mentioned. Really just the mess it can become to manage many containers. Ansible really helps out here so mention that and how I can both build and deploy with Ansible.

## Ideas I can explore but for which others will have a better perspective
- Containers
  - Investigate the security aspect of docker containers on my system. How does it compare to lxd and
    rocket. Can I improve it without loosing functionality? Write as a follow up to docker for pets post.
  - This is a good explanation of the container workflow that Docker enables that lxd doesn't
    aka 'Continuous Delivery' - http://thenewstack.io/containers-disrupting-devops-infographic/
    - I think the most important part is an easy way to share them not the focus on system containers
      but the focuse on system container tends to make you think of them a bit like pets not cattle and
      easy sharing is less of a focus.
    - Another aspect/way to think of the conainer workflow is the shift from machine centered infrastructure to application centered
      as talked about at http://queue.acm.org/detail.cfm?id=2898444
      - ie standard utilization metrics collected per container, which is per application not per machine. Logging is done based on the
        container, aka the application not with concern to which machine. Both of those are done at the container level which has a standard
        interface and so can be easily done no matter the application.
    - I talked a bit about this in my Initial impressions of LXD post.
  - LXD
    - Is it more secure? It has in a lot of builtin security, that I like.
    - LXD is great for anything needing init, I think I said that in my initial rambling thoughts on it.
      There are times when this is needed and others when really I just want one app running, ie chrome.
    - LXD is a non-starter for my personal containers, unpriveleged bind mounts nobody in the container,
      you can use acls to make it viewable but still get issues for some things (like ssh) because
      permissions checks fail. Additionally the acls are specific to the running container and so very
      cumbersome to widely implement.
      - When you consider not only dot config files but also /dev/dri and other files needed for gui/sound
        I don't think there is much of an option of this working well until user<->user bind mounting
        exists.
    - LXD has recursive embedding of itself figured out. I don't think I will have much luck on that with
      Docker, though admitedly haven't tried.
    - Basically I really should think of lxd as a full VM like system and use docker for everything
      else including individual dev environments and apps.
  - Image deployment, why it works for Docker and why the industry moved away from it years ago for servers.
- The next big challenge is the management of large amounts of containers.
  - Lots of contenders are entering this space perhaps do a review and comparison of them.
  - kubernetes, flocker, even things like apache mesos and to some extent juju fit into this.
