# Potential Ideas
- lxd nesting
  - Primarily about the integration env I use for mojo
  - I need a newer lxc for trusty to work with nesting.
  - Unprivileged means no mknod so I need to download the root FS as mentioned at https://www.stgraber.org/2014/01/17/lxc-1-0-unprivileged-containers/
  - The immutable infrastructure I was working on for Monasca CI could be talked about also, see notes below
- Talk about the immutable infrastruce CI environment I built for Monasca.
  - Make sure to pull from much of my philosophy on this found in the Readme for the monasca/ci repo.
  - Talk about velocity of code commits and help the CI environment needs to preserve this.
- Delivering consistent code quality
  - Something I am exploring but am not an expert at.
- Documentation driven development
- Balancing collaboration and engineering. Steering toward synergy without going to far either direction.
- Building packages. Various ways of doing debs, python packages, etc.
- git
  - workflow, lots of repos versus few, git subtree versus git submodules
- Explore journald and other aspects of systemd in depth.
  - this article intrigued me about journald, http://sysadvent.blogspot.com/2015/12/day-17-grokking-systemd-for-fun-and.html
- Docker
  - This is a good explanation of the container workflow that Docker enables that lxd doesn't
    aka 'Continuous Delivery' - http://thenewstack.io/containers-disrupting-devops-infographic/
    - I think the most important part is an easy way to share them not the focus on system containers
      but the focuse on system container tends to make you think of them a bit like pets not cattle and
      easy sharing is less of a focus.
    - I talked a bit about this in my Initial impressions ofLXD post.
  - Talk about the Monasca demo, kitematic, in general hiding implementation details.
  - Ansible + docker how I both build and deploy with Ansible.
    - Annoyances with docker, include that the service startups fail with the newer init replacements so my roles have to be modified.
    - The building of the container is split from the running so I find myself having to change roles so some things only happen when on startup. Not that
      this is unique to containers but has annoyed me.
  - Image deployment, why it works for Docker and why the industry moved away from it years ago for servers.
  - The ~/bin/docker-tips and ~/bin/docker-cleanup should be mentioned. Really just the mess it can become to manage many containers. Ansible
    really helps out here so mention that.
    - The arg '-d' to daemonize a running container is essential as foreground docker containers are a pain.
  - the docker orchestration toolkit, machine, swarm and compose.
- The next big challenge is the management of large amounts of containers.
  - Lots of contenders are entering this space perhaps do a review and comparison of them.
  - kubernetes, flocker, even things like apache mesos and to some extent juju fit into this.
- Something golang related.
- Markdown - use with github and readthedocs
  - I have a love hate relationship with markdown, I like it as text but am generally disappointed in rendering (My lists don't work and I need more empty
    lines in my text generally)

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
