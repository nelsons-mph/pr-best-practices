# Index
[Automated Pull Request Template Usage](#automated-pull-request-template-usage)
<br>[Best Practices for PR](#best-practices-for-pr)
<br>[Git Repo Naming Conventions](#git-repo-naming-conventions)
<br>[Git PR Code Flow](#git-pr-code-flow)
<br>[Git Repo Directory Structure](#git-repo-directory-structure)

# Automated Pull Request Template Usage

It is advisable to have a standard PR template for each pull request with proper description and info about the PR. Github has the option to include standard PR templates so that it is not required to type PR descriptions each and every time.  

## Pre-requisites
1. Basic knowdledge of creating and working with MarkDown docs
2. Basic knowledge of GitHub & PR
3. An IDE with an appropriate exension to work on markdown files

## Steps to create an automated PR template
1. Create a markdown file under the name `pull_request_template.md`
2. Add the required contents. Below is a sample template but can be extended or modified based on one's creative imagination
<br><b> ----- Sample Readme.md contents below (use copy option to copy and paste it in your readme.md file) ----- </b>
```
> #### PR Details:
Purpose   | Merge Dev code files into Non Prod (integration)
----------|-----------
JIRA Story Reference(s) | [<Link Description goes here without the angle brackets>](<Link description goes here without the angle brackets>)
Test Case(s) passed | :white_check_mark:
Merge if approved | **Yes**
Delete if merged | **No**
 <br/>

> #### Deployment Type:
<!--- What types of changes does your code introduce? Put an `x` in all the boxes that apply: -->
- [ ] :rocket: Feature to Dev Merge / Dev Deployment
- [x] :rocket: Dev to Integration Merge / **UAT Deployment**
- [ ] :rocket: Integration to Master Merge / **Prod Deployment**
- [ ] :bug: Issue/Bug Fix (non-breaking change which fixes an issue)
- [ ] :sparkles: New feature (non-breaking change which adds functionality)
- [ ] :boom: Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] :ambulance: Hotfix
- [ ] :zap: Performance improvement
<br/>

>  #### Internal Changes:
- [ ] :construction_worker_man: Updating project setup (continuous integration, build system, package dependencies)
- [ ] :recycle: Code Refactor
- [ ] :heavy_check_mark: Updating tests
- [ ] :ok_hand: Updating code due to code review changes

>  #### Commit Checklist
- [ ] :blue_book: Does the source code follow the coding standards and format as agreed upon?
- [ ] :speech_balloon: Are proper comments added in code to make it more descriptive?
- [ ] :speech_balloon: Does each class meet the minium code comment density?
- [ ] :put_litter_in_its_place: Is the code clean of Sysout statements/SOPs?
- [ ] :put_litter_in_its_place: Is the code clean of unwanted `TODO` & obsolete comments?
- [ ] :put_litter_in_its_place: Have the imports been organized in all the classes? Use `Ctrl+Shift+O` keybinding in Eclipse/STS IDE to remove unwanted imports. This needs to be used in each class individually.
- [ ] :triangular_flag_on_post:  Has the code been scanned statically in local using a scanner (CheckStyle, PMD, FindBugs)?
- [ ] :checkered_flag: Are all test cases passing?
- [ ] :battery: Do we have the minimum code coverage in local? Use [EclEmma plugin](https://www.eclemma.org/installation.html) to find local coverage.
- [ ] :memo: Has the readme.md been updated for the change log? (optional)

<br/>

>##### TODO:
<!--- Additional things to-do / technical debts -->
- [ ] N/A
```
4. To preview the markdown PR template, we can either 
   1. use the readme.md file which will be added to a GitHub repo by default in most cases. If the readme is empty, try     editing it online in the browser and viewing the changes [OR]
   2. Use an IDE with the appropriate plugin. Visual Studio Code with `Markdown All in One` extension  is what I use.
   <br> <b>Preview of the above PR template content</b>
   ![image](https://user-images.githubusercontent.com/62734192/201743732-7d4feaa2-a7f1-4201-83f2-4a2288ef71a3.png)

6. Place this file either in 
   - repository's root diectory [or]
   - inside docs directory (`docs/pull_request_template.md`) [or]
   - hide it inside .github directory (`.github/pull_request_template.md`)
 7. If you are adding this PR template in a feature branch, raise a PR to  the 'default` branch so that the template reflects for each PR that will raised going forward. You can directly add the PR template to the 'default' branch of the repo either by a commit or by adding the file directly in GitHub on the browser.
 8. There can be multiple PR templates for each environment such as the one below which I use for Prod code push. it is not necesasry to include everything but a more descrptive PR can serve as an all-in-one place for reference.
 ```
 > #### PR Details:
Purpose  | Prod Deployment (integration to master merge)
----------|-----------
PTB       |  [<Permit to Build Description goes here without the angular brackets>](<PTB link goes here without the angular brackets>)
PTO       | [<Permit to Operate Description goes here without the angular brackets>](<Permit to Operate Link goes here without the angular brackets>)
Change Request(s)       |  [<Change Request Description goes here without the angular brackets>](<Change Request link goes here without the angular brackets>)
Run Book                      | [<Runbook description goes here without the angular brackets>](<Runbook link goes here without the angular brackets>)
Planned Prod Release Date       |   **Q1 - 02/20/2021** 
DRT Request(s)             | N/A
Archer Scan(s) |  N/A
JIRA Story Reference(s) | [<JIRA User Story description goes here without the angular brackets>](<JIRA User Story link goes here without the angular brackets>)
Test Case(s) passed | :white_check_mark:
Merge if approved | **Yes**
Delete if merged | **No**
 <br/>

> #### Deployment Type:
<!--- What types of changes does your code introduce? Put an `x` in all the boxes that apply: -->
- [ ] :rocket: Feature to Dev Merge / Dev Deployment
- [ ] :rocket: Dev to Integration Merge / **UAT Deployment**
- [x] :rocket: Integration to Master Merge / **Prod Deployment**
- [x] :bug: Issue/Bug Fix (non-breaking change which fixes an issue)
- [x] :sparkles: New feature (non-breaking change which adds functionality)
- [ ] :boom: Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] :ambulance: Hotfix
- [ ] :zap: Performance improvement
<br/>

>  #### Internal Changes:
- [x] :construction_worker_man: Updating project setup (continuous integration, build system, package dependencies)
- [x] :recycle: Code Refactor
- [x] :heavy_check_mark: Updating tests
- [ ] :ok_hand: Updating code due to code review changes
<br/>
 ```
References:
- [GitHub Docs | Creating a PR template](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
- [Markdown | Syntax Guide](https://www.markdownguide.org/extended-syntax/)
<br>[Back Top &uarr;](#index)

# Best Practices for PR
1. Give a proper commit message label that is self-descriptive of the code change/commit
2. Advisable to include a detailed message of the the commit - code change details make use of PR templates, JIRA story references
3. Include Design Artifacts (Design Documents, OAS, Postman collections etc) for a code review. Either attach them to the PR or provide links/references to the documents.
4. Add Reviewer(s)
5. Add Assignees or add yourself
6. Add labels [see Using Labels Section below](#using-labels)
![image](https://user-images.githubusercontent.com/62734192/201747465-26e3e054-5be5-4169-8063-b42a69529c8f.png)

<br> Nit : 
 - Update `README.MD` with Project information so that it serves as AIO document for the service.
 - Add Gitmojis to code commit labels to make them look uber cool ;)

# Using Labels
 - Why to use? - Labels are cool, colorful but most importantly they act like indexes to filter our PRs easily.
 - How to use? - Create a new label from the `Labels` section when you raise a PR. Once created, this label will be available for the subsequent PRs.
   By default, GitHub will suggest labels but creating custom labels helps us much more. To create a label:
     <br> - Type the label name and wait for GitHub to show the `Create new label <label_name>`
     <br> ![image](https://user-images.githubusercontent.com/62734192/201746627-884d097b-0802-43e6-8625-3408999a24cc.png)
     <br> - Add a decription to the label and use common color codes for label. Use the Hex code option to use a single color code and do not use random colors. For example : dev (red) -> qa (yellow) -> prod (green)
     ![image](https://user-images.githubusercontent.com/62734192/201746857-2e0ed8a3-73f8-4f8d-8654-6da3c271261f.png)
     
 - Best practices:
   - Add User Story as labels
   - Add common labels across repos like : `dev` , `qa`, `prod`, `reverse-merge`
   - Follow single color code for common projects, user stories
<br>[Back Top &uarr;](#index)

# Git Repo Naming Conventions

Type of Repo        |   Naming Convention	                              |       Examples
--------------------|-----------------------------------------------------|---------------------------------
Microservice/API    |   `{APP-NAME}-REST-service` <br> `{APP-NAME}-rest-service`  |   investor-profiles-rest-service <br> rs-investor-profiles-REST-service[^1]
Microservice/API Flavour : Orchestration Flavour    |   `{APP-NAME}-rest-service`  <br> `{APP-NAME}-orchestration-rest-service` <br> `{APP-NAME}-orchestrator-rest-service`  |   rs-investor-profiles-orchestrator-rest-service
Microservice/API Flavour : Data Flavour | `{APP-NAME}-data-rest-service` |  rs-investor-profiles-data-rest-service
Microservice/API Flavour : Batch        |  `{APP-NAME}-batch` | rs-investor-profiles-batch
Microservice/API Flavour : Listener     |   `{APP-NAME}-listener` <br>`{APP-NAME}-listener-service` | rs-investor-profiles-listener
Microservice/API Flavour : Shared Library   | `{APP-GROUP:optional}-shared-lib` | rs-investor-profiles-shared-lib
Microservice/API Flavour : Build Orchestration[^2]  |   `{APP-GROUP}-orchestration` | rs-investor-profiles-orchestration
Microsite       |   `{APP-NAME}-site`  |  rs-investor-profiles-site
Microsite/Controls Module       |   `{APP-NAME}-controls-module`  |  rs-investor-profiles-control-module

[^1]: `REST` and `rest` terms can be interchanged
[^2]: This is the build orchestration repo that handles the orchestration of app deployments not to be confused with orchestration flavour

 
# Git PR Code Flow
 1. Create feature branch from `dev`
 2. Feature branch naming conventions
    <br> `Feature-{UserStoryRef}-{FeatureDescription}-{mmddyy:optional}` <br> Ex: <i>Feature-USRSTRY04-copyPlans</i> or <i>Feature-USRSTRY04-copyPlans-111422</i>
    <br> Including the date in the branch name will help us to identify since when the feature is branched out.
    <br> `Feature-reverseMerge-dev-{mmddyy:optional}`
    <br> `Feature-patch-dev-{mmddyy:optional}`
 3. Work on the `feature` branch for the changes. Raise a PR from `feature to dev`. If one or more developers are working on different features, it is always advised to sync the changes with each other. This syncing is done by reverse merging the changes from dev into the developers' own feature branches
 4. Once PR is raised, get it reviewed and merged to dev.
 5. Raise PR from `dev to qa` post successful dev deployment.
 ![image](https://user-images.githubusercontent.com/62734192/201771742-64612840-5ca2-4eeb-bf63-2f1cfebfbbd4.png)
[Back Top &uarr;](#index)

<details> 
<summary> Branch naming conventions recommended by GitHub  </summary>
<br>
Well there aren't any conventions specified by Git and GitHub, it is always good to follow some rules and conventions to create a new branch, its flow etc. In general, Git branches fall into two different categories:
        1. Regular/Evergreen branches
        2. Temporary branches

<br>
<b> Regular Git branches </b>

<br>
These branches will be available in your repository on permanent bases. Their naming convention is simple and straightforward.

<br>
<li> Development (dev) is the main development branch. The dev branch’s idea is to make changes in it and restrict the developers from making any changes in the master branch directly. Changes in the dev branch undergo reviews and, after testing, get merged with the master branch.


<li> Main (main, yes main and not <strike> master</strike>)  is the default branch available in the Git repository. It should be stable all the time and won’t allow any direct check-in. You can only merge it after code review. All team members are responsible for keeping this stable and up-to-date.


<li> QA (QA), or test branch, contains all the code for QA testing and automation testing of all changes implemented. Before any change goes to the production environment, it must undergo the QA testing to get a stable codebase.
<br>

<br>
<b> Temporary Git branches </b> 

<br>
As the name indicates, these are the branches that can be created and deleted when needed. They can be as follows:
    <li> Bug Fix
    <li> Hot Fix
    <li> Feature Branches
    <li> Experimental Branches
    <li> WIP branches
</details>
<br>

Template repositories with an automation template that includes:
 <li> 1. Tags
 <li> 2. Recommended Branches
 <li> 3. Access settings
 <li> 4. Review settings
 <li> 5. Team settings
  
[Back Top &uarr;](#index)
  
# Git Repo Directory Structure

Simple REST API Service
![image](https://user-images.githubusercontent.com/111540956/206884096-7c7db902-a97d-49f4-a0d9-3df24bebd9ed.png)

[Back Top &uarr;](#index)
