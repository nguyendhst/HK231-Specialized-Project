# Methodology

---

- [Description of the development methodology employed](#development-methodology)
- [Overview of the technologies, tools, and frameworks used](#technologies-tools-and-frameworks)

---

## Development Methodology

- [Development Approach](#development-approach)
- [Task Management](#task-management)
- [Version Control](#version-control)

### Developement Approach

The project's development approach is based on the Agile methodology, but does not follow strictly to any existing framework. Some of the main principles of the Agile methodology that will be followed are:

- Each team member shares the same responsibilities and has the same authority.
- The team is self-organizing and self-managing.
- The team is cross-functional and has all the skills necessary to complete the project.
- The team is self-sufficient and does not rely on external resources.

The project will be divided into multiple iterations, which will have a duration of 1 week. Each iteration will have a set of tasks to be completed, and at the end of each iteration, the team will deliver a working product increment. The product increment will be reviewed and evaluated by the team and the advisors, and the feedback will be used to improve the product in the next iteration.

### Task Management

Task management is done using GitHub Projects. The project is divided into multiple iterations, each of which is represented by a GitHub Project board. Each iteration board is divided into 4 columns: `To do`, `In progress`, `Review`, and `Done`. Each task is represented by a GitHub Issue, which is then added to the corresponding column on the board. The team members will then move the tasks between the columns as they progress through the iteration.

![ProjectTimeline](/images/github-project-timeline.png)

### Project Planning and Scheduling

#### Project Timeline

The project begins from 11/09/2023 and is expect to lasts 15 weeks until 19/12/2023.

Two major milestones are set for the project:

- Prototype release: 08/10/2023

  - The prototype release is the first release showcasing key features of the project. The prototype release will include:
    - A web application that allows users to create and manage their projects.
    - Visual DnD Editor that allows users to visually model their projects.

- Version 0.1.0 release: 05/11/2023

  - The version 0.1.0 release is the first release of the project that can be evaluated by users. The version 0.1 release will include:
    - Fully functional visual DnD editor.
    - User authentication and authorization.

- MVP release: 11/12/2023
  - The MVP release is the final release of the project. The MVP release will include:
    - Fully functional visual DnD editor.
    - Workflow DnD Editor that allows users to visually model their workflows.

{{< mermaid >}}
gantt
dateFormat YYYY-MM-DD
title Project Timeline
axisFormat %m/%d
section Requirement Analysis
Requirement Analysis: 2023-08-28, 2023-09-11
section System Design
System Design: 2023-09-11, 2023-09-26
section Implementation
Implementation: 2023-09-26, 2023-12-10
Prototype Release: milestone, 2023-10-08, 0d
Version v0.1.0: milestone, 2023-11-05, 0d
MVP Release: milestone, 2023-12-11, 0d
section Documentation
Requirment Analysis: 2023-08-28, 2023-09-11
System Design: 2023-09-11, 2023-09-26
Technical Documentation: 2023-09-26, 2023-12-03
Concluding Report: 2023-12-03, 2023-12-10
{{< /mermaid >}}

#### Project Schedule

Table of weekly workload for each team member.

| Week  | Workload              | 2013924 | 2013914 | 2013873                                                |
| ----- | --------------------- | ------- | ------- | ------------------------------------------------------ |
| 1-3   | Project Research      | 3       | 3       | Research Promotion & Low-code Platform, Technology     |
| 4-5   | Prototype Development | 3       | 3       | Build Project Plan, Build Usecase and Usecase scenario |
| 6-7   | First Release         | 3       | 3       | Initialize Back-end Repository, Design Database Schema |
| 8-9   | First release         | 3       | 3       | Compile Puck to fit the platform                       |
| 10-11 | TBD                   | 3       | 3       | 4                                                      |
| 12-13 | TBD                   | 3       | 3       | 4                                                      |
| 14-15 | TBD                   | 3       | 3       | 4                                                      |

### Version Control

Version control of the project is done using Git and GitHub. The project repository is hosted on GitHub and is accessible at [link](https://github.com/users/nguyendhst/projects/1).

To work on the project, a Git branching model convention is used. The model is as follows:

{{< mermaid >}}
%%{init: { 'logLevel': 'debug', 'theme': 'base', 'gitGraph': {'showBranches': true, 'showCommitLabel':true,'mainBranchOrder': 1}} }%%
gitGraph LR:
commit
branch dev order: 1
branch feature/1 order: 2
commit
commit
checkout dev
merge feature/1
checkout main
branch feature/2 order: 3
commit
commit
merge feature/1
checkout dev
merge feature/2
checkout main
merge dev
branch hotfix order: 0
commit
commit
checkout main
merge hotfix
{{< /mermaid >}}

- **Main branch**: `main` - The main branch is the branch where the source code of HEAD always reflects a production-ready state.

- **Development branch**: `dev` - The development branch is the branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release. Some would call this the “integration branch”. This is where any automatic nightly builds are built from.

- **Feature branch**: `feature/1` - Feature branches (or sometimes called topic branches) are used to develop new features for the upcoming or a distant future release. When starting development of a feature, the target release in which this feature will be incorporated may well be unknown at that point. The essence of a feature branch is that it exists as long as the feature is in development, but will eventually be merged back into develop (to definitely add the new feature to the upcoming release) or discarded (in case of a disappointing experiment).

- **Hotfix branch**: `hotfix` - Hotfix branches are very much like release branches in that they are also meant to prepare for a new production release, albeit unplanned. They arise from the necessity to act immediately upon an undesired state of a live production version. When a critical bug in a production version must be resolved immediately, a hotfix branch may be branched off from the corresponding tag on the master branch that marks the production version.

## Technologies, Tools, and Frameworks
