---
layout: site
title: Development Process
body_class: process
---

Even before you tackle an issue, make sure to have the BVP (from the user), the Functional Spec (from the Business Analyst) and Technical Spec (from the Development Team). See [Project Documentation](project-documentation).

Understand your part in the project.

### Steps

The general process for development is:

**0. Determine MVP for the issue**

Before you start, make sure the issue is broken down to the minimum viable product. If it can be broken up into multiple issues, it should be. This allows better isolation of work, and better tracking for the project managers.

Issues should succinctly describe how to fix them. Vague descriptions make it hard to know when the issue is complete, and can make it harder for other people to get involved in the project.

Create a development plan in [Senwes Teamwork](https://teamwork.senwes.co.za//){:target="_blank"}.
* Project your are working on will be setup in Teamwork.
* Divide project in workable standalone units.
* Sub tasks can be created in categories:
    1. Planned
    2. In Progress
    3. QA
    4. UAT
    5. Implementation (Roll Out) - Please add items in this bucket throughout the development process to ensure complete rollout.
    <b>It is up to the developer to move items between buckets on time and schedule meetings for internal demos and PR's.</b>

* Create sub tasks for coding, internal demo before PR, PR and demo to user.
* Asign revelant developer per task and the reviewer, with due dates.


**1. Take the issue**

When working on an issue, make sure you’re not overlapping with existing work. This is typically handled by assigning the issue to yourself via [Senwes Teamwork](https://teamwork.senwes.co.za//){:target="_blank"}.

**2. Write the code!**

You’ve done the easy bits, now it’s time to actually do the work.

<b>This work needs to happen on a branch. Create a project branch from the master branch.</b> The pattern you should use is `{ESM_project_number}_{name_of_project}`. <br /> `(e.g. 123_OneAgriVendor)`.<br />Then create branches per featrure with this pattern `{Project_number}_{name_of_project}_{name_of_feature}`.<br />
Please read <a href="/topics/source-control">this</a> important information when working with branches.

**3. Push early, push often**

As soon as your code is in a usable state, you should push it up. This allows tracking the issue over time a little easier, and avoids cases where you disappear for a while to sort out an issue. It also allows others to watch and potentially correct a wrong assumption before you spend hours on it, and will trigger automated testing if set up for the repo.

You don’t need to push every commit, but be sensible.
* <b>Merge master into project branch before create a new feature branch</b> 
* <b>Always create a feature branch from project branch</b> 

**4. Iterate, complete, and submit a PR for review**

Keep working, and when ready, submit the PR for review, see the [reviews guide](code-reviews.html) for more info.

Pull requests should specifically mention the issues they close at the least. Ideally, have a sentence or two that describes how you solved the issue as well to provide context on the pull request.

**5. Merge and ship!**

Merging the branch is usually handled by the PR Author once approved by a peer. The branch will be automatically deleted after merging via GitHub’s branch policy.
* Always merge feature branches into project branch, never into master branch.
* While in development or testing phase, publish from project branch.
* When publish to PROD, merge master into project branch, then PR to master, publish from master.

### Deployable Main

The main branch of the repository should be deployable at any time. Deployment for projects is handled via GitHub Actions, where the production environment is essentially updated to the current commit (head) of main.

This means that features should only be merged into main when they’re ready to be deployed. Anything in main must go through code review before merging, and this is enforced via the GitHub repository settings.

For more complex projects with differing QA processes, additional workflow branches such as staging can be created. Features can then be merged into these branches before then merging those into main. This workflow only makes sense for more complex projects, and should be avoided if not necessary; keep it as simple as possible.

### Features in Isolation

With the asynchronous nature of how we work, it’s important that everyone is able to continue making movement without being blocked on anyone else. To ensure smooth flowing development, we create branches for new features or bug fixes. When these changes are ready, they then proceed into review and are merged.

Each branch should focus on a single issue with the goal of closing it out. Following the agile methodology, these issues should also be broken down as much as possible, so each branch should be a single focussed change to close out the issue.

Generally, these features should be entirely independent of each other. This allows engineers to grab an issue and work away on it without blocking. However, not all features are truly independent; a branch may provide underlying functionality required by other features. Merging these branches early helps.

### Incremental Improvement

Features should be shipped early in a minimal state, then improved further in future changes. The agile methodology is heavily focused on iterative improvement, encouraging constant improvement.

This means merging features when they’re ready in a minimal state, and continuing to build on top of this. This makes development much more parallelisable (it’s a word, trust me), as multiple engineers can work on different parts of the same feature once the base of it is in place. This is crucial for asynchronous work, with Senwes Applications having a distributed workforce.

### Governance feedback to be completed with roll-out for UAT and Production

Before publishing your new project or feature, for either testing or production, please complete the [Development Governance Checklist](https://form.jotform.com/232976282852568) as thoroughly as possible, where you see any shortcomings, please implement the correction before publishing.