# Generic SW project hand-over

## Hand-over requirements:

- Obviously - source code, deployment, domains and/or apps ids
- If external components in use - vendors licenses to be transferred, contacts and SLAs to be handed over.
- Deployment instruction: step by step instruction for DevOps engineer on how to install, update and maintain the software (https://en.wikipedia.org/wiki/Software_deployment)
- List of known defects and limitations and they details.
- Product backlog
- Front-end’s supported browsers with they versions (Chrome, Safari, IE / IE Edge, FireFox) and supported screen/window resolution (in pixels, horizontal/vertical, desktop / mobile)
- System and database architecture - must be up to date with actual system implementation
- Technology stack for both front-end and back-end: operating system requirements, programming language, database, up to tested and production ready major and minor versions - must be actual and supported by the vendors to avoid costly updates to match vendor supported versions
- CI/CD - what is an automated deployment process in place and how to roll it out
- External services requirements and they settings, configuration.
- Target hardware configuration details and the load it will handle.
- Capacity management: expected file system & database growth, CPU & memory requirements per 100 active users to plan HW specs for production.
- Complete git repository with git history (git clone, zipped/tared/etc.)
- Common issues and solution / work-arounds
- Build-in users, roles, passwords, if any
- Network configuration: ports and connectivity required (for firewall configuration)
- API documentation
- Code lint and quality reports (depends on the stack: eslint / phplint / pylint, DeepCode.ai code scan report)


## Optional / nice to have:

- Operating system & database backup procedures 
- Admin and User guide
- Are there any batch schedules or long running processes
- Is the system completely transactional and how is concurrency managed
- When are pent tests / security audits undertaken
- How unit and functional testing is executed, tests coverage
- Application level monitoring configuration (to enable app level monitoring alongside with database & OS level monitoring)

