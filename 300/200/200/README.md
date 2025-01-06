# 200 - Synching DevRev with GitLab

See also [DevRev synced with GitLab](https://marketplace.devrev.ai/gitlab-pzy4ce0g) 

After having signed into DevRev visit the page at https://marketplace.devrev.ai/gitlab-pzy4ce0g and click the **Install** button.

On the [Snap-ins page](https://app.devrev.ai/agility-game/settings/snap-ins) you will see the snap-in being installed. When shown the button **Complete Installation** click it.

In the **Organization Settings**, set up the **Configuration** as follows:

- Create task for PR reviewers: **On**
> Creates a task for the assigned reviewer of a pull request.

- Enable magic commands: **On**
> Enables commands to associate issues and Gitlab PRs (/toward) and automatically close issues when PRs are merged (/devrev-close).

- Mention issues in PR body without magic commands: **On**
> Issues can be mentioned in PR body without using /toward or /devrev-close.

- Update issue stage on PR close: **On**
> Update issue stage when a PR is closed or merged without /devrev-close.

- Update autonomous issue with PR details: **On**
> Updates branch autonomous issue body and title with PR details.

- Link issues in PR body with autonomous issues: **On**
> Creates a dependency link between issues in PR body and autonomous issues tagged with branch/PR.

- Send reminders for inactive PRs: **On**
>Sends reminders for stale PRs.

- [Required] Days before sending PR reminders: **3**
> Posts reminders on issue discussion for stale PRs after specified days of inactivity.

- [Required] Default part for autonomous issues: **Default Product 1**
> Default part to assign autonomous issues to (if part cannot be inferred from repository).

- [Required] Automation stage for New Commit: **in_development**
> Specifies the default stage to assign issues when a new commit is made.

- [Required] Automation stage for New Branch: **in_development**
> Specifies the default stage to assign issues when a new branch is created.

- [Required] Automation stage for New PR Opened: **in_review**
> Specifies the default stage to assign issues when a new Pull Request is opened.

- [Required] Automation stage for PR Closed: **in_development**
> Specifies the default stage to assign issues when a Pull Request is closed.

Click **Save**.

In the **My Settings**, set up the **Configuration** as follows:

- [Required] Track autonomous work: **On Branch Creation**
> Creates an issue when a Branch/PR is created/opened without linked issues.

Click **Save**.

Now click **Install Snap-in**.

## Instructions

1. Create new webhook
  - Navigate to your Gitlab Settings > Webhooks and select Add new webhook
    
2. Add the following Payload URL
  - https://api.devrev.ai/hidden/dev-orgs/DEV-3H0ADarH00/event-source-webhooks/custom/7d9687f2-8b72-4f57-b469-0da4c915bbd8
    
3. Set Secret token
  - Add the following secret *************** (saved somewhere secure)
    
4. Select triggers
  - Push events -> All Branches
  - Merge request events
    
5. Finalize creation
  - Finalize the creation by clicking Add webhook in Gitlab
    
6. Profile Page
  - Navigate to the GitLab Edit Profile page, locate the User ID, and copy it.
    
7. Link GitLab ID
  - Go to the snap-in Discussions sidebar and execute /link-identity <gitlab_user_id>.
    
8. Verify
  - If the identity is shown as linked in the Discussions tab, you're all set.

## About GitLab for DevRev

Sync GitLab and DevRev so issue status is always real-time and driven by code.

## Overview

Connect GitLab with DevRev, and ensure your work stays in sync between the two systems, such that issues and statuses are always real-time and driven by code activity. GitLab for DevRev is a snap-in that has been used by several organizations, and ties DevRev issues closely with Git activities, eliminating the need for humans to manage issues.

Why should you un-manage your work? You should use this snap-in if you want to reduce work about work. Let machines manage issues, including creating and updating statuses, so developers can focus on work that matters. You’ll resonate with this, if you have ever:

- Delivered a hot-patch and realized you never had an issue to track it
- Wasted time just updating your team on the status of an issue
- Or just felt that creating and managing issues is a distraction

If your team’s best practice is to link your GitLab activity to an existing issue-ID during branch creation, commits and MRs, then this automation will honor that and enable a GitLab driven issue state, without auto creating issues. We can link your DevRev issue to GitLab activity, through mention of issue-ID in branches, commits, and PRs.

However, if you choose to work in GitLab and never created or linked an issue, you shouldn’t have to sweat it. This automation will automatically create issues that track all associated commits, branches and merge requests. The auto-created issue is enriched with MR description and related GitLab events. The status of these issues is driven by GitLab activity, and the issues will auto-transition stages, from In Development to In Review, and Closed. Your work is always accounted for and more importantly your team members have visibility and know what you’ve been up to, resulting in fewer interruptions.

## Features

This automation is powerful, and has several configurable features. As they say, the power is in the defaults! When you install this snap-in, DevRev configures defaults that are tried and tested. You always have the option to customize further.

### Automatic status updates
You can associate GitLab commits, branches and merge requests with the DevRev issue they correspond to. Doing so allows you to see GitLab activity in the corresponding DevRev issue and to act on those events, allowing you to automate away your manual tasks. Mention DevRev issues in GitLab, and route the relevant GitLab events to this issue. They can be mentioned either as display IDs (ISS-34) or object IDs (issue:34), case insensitively. A DevRev issue can be mentioned in branch names, commit messages, or MR titles.

### Autocreate issues from GitLab branch
If you do not explicitly associate your DevRev issue to GitLab branches, commits or MRs, then DevRev can autocreate your issues so you have an account of all your GitLab activity. This feature automatically creates an issue when a new branch is created, and tracks all associated commits and merge requests on this issue. The auto-created issues will move status based on Git activity, to in development based on branch and commit activity, and in review when MRs are created and merged. If desired, when MRs are merged, you can personalize the automation to move the issue to closed status. However, this template by default will keep the issue in an open state.

### Autocreate issues from GitLab MRs
You can choose to automatically create issues when a new MR is created, and it is not linked to an existing DevRev Issue. The behavior is similar to how issues are auto-created with new branches. The auto-created issues will move status based on Git activity, and events are posted on the DevRev issue timeline. If desired, when MRs are merged, you can personalize the automation to move the issue to closed status. However, this automation by default will keep the issue in an open state.

Issues autocreated from GitLab branches or MRs are called 'autonomous issues'. They have the tag autonomous.

### Attribute part to autonomous work
This automation will infer the part from a repository if possible. If not, the issue is created with a specified default part. You can configure the default part while setting up this snap-in. Every issue on DevRev must have a part attribution.

### Enrich autonomous work descriptions
Enrich autonomous issues with information derived from GitLab MR events. The title and description of an autocreated issue is enriched with the MR data. When a new GitLab MR is opened or edited, then the related autonomous issue description is updated with the latest MR description. If the user has removed the auto generated text, then the automation will no longer update the description from MRs. Similarly, autonomous work titles are updated with the MR title, if the user hasn’t already updated it.

### Link autonomous work with related issue
Create a related link between the work-items mentioned in the MR body and the autonomous issues tagged with the branch/MR. When a new GitLab MR is opened/edited, for all the autonomous tagged work items(by branch/MR), automatically mark the issues mentioned in the MR as related.

### Automatically close autonomous work
Autonomous work gets closed when its related MR is merged. However, if there is no MR activity on this work, then the autonomous work is closed after configurable period.

### Automatic MR tasks
When a merge request is requested or reopened, a DevRev task is created for you. In order for this automation to be triggered, you'll need to link your merge requests to DevRev issues. If your MR is removed, merged or closed, then the Task gets deleted. However, if you submit your MR review, then the task is closed.

### Automatic MR reminders
When a merge request is inactive for more than a specified number of days, then this automation will post a message in all related DevRev issues. You'll need to link your GitLab merge request to DevRev issue to enable these reminders. There are several ways to link your GitLab merge requests to DevRev issues. You can do so by mentioning the DevRev issue ID in the merge request title or body, or mention it in the branch name or commit message. Reminders are also posted for issues created autonomously.
