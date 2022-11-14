# Index
[Automated Pull Request Template Usage](#automated-pull-request-template-usage)
<br>[Best Practices for PR](#best-practices-for-pr)
<br>[Java Spring Boot API Code Review Checklist](#java-spring-boot-api-code-review-checklist)
<br>[Git Repo Naming Conventions](#git-repo-naming-conventions)
<br>[Git PR Code Flow](#git-pr-code-flow)

# Automated Pull Request Template Usage

It is advisable to have a standard PR template for each pull request with proper description and info about the PR. Github has the option to include standard PR templates so that it not required to type PR descriptions each and every time.  

## Pre-requisites
1. Basic knowdledge of creating and working with MarkDown docs
2. Basic knowledge of GitHub PR
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
   - inside docs directiry (`docs/pull_request_template.md`) [or]
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
     <br> - Type the label name and wait for GitHub to show the `Create new label "<label_name">
     <br> ![image](https://user-images.githubusercontent.com/62734192/201746627-884d097b-0802-43e6-8625-3408999a24cc.png)
     <br> - Add a decription to the label and use common color codes for label. Use the Hex code option and do not use random colors. For example : dev (red) -> qa (yellow) -> prod (green)
     ![image](https://user-images.githubusercontent.com/62734192/201746857-2e0ed8a3-73f8-4f8d-8654-6da3c271261f.png)
     
 - Best practices:
   - Add User Story as labels
   - Add common labels across repos like : `dev` , `qa`, `prod`, `reverse-merge` & follow same color code
<br>[Back Top &uarr;](#index)

# Java Spring Boot API Code Review Checklist

Review Cateogry             |           Review Item
----------------------------|--------------------------
Clean Code                  | :heavy_check_mark: Leave a TODO whereever code needs to be added/modified & removed any other unwanted TODOs <br>:heavy_check_mark: Remove all TODOs while moving code from Dev to higher environments <br>:heavy_check_mark: Remove unorganized imports, unwanted comments
Coding                      | :heavy_check_mark: Make the controller thinner - make it thin so that each method only handles the request and returns the response. All other code logic should be moved to appropriate classes. <br>:heavy_check_mark: Reduce boilerplate code by making using of frameworks like [Lombok](https://projectlombok.org/features/GetterSetter)  <br>:heavy_check_mark: <b>DRY: Don’t Repeat Yourself</b> (Avoid Duplication) <i> Identify commonly used logic and extract them into re-usable functions</i> <br>:heavy_check_mark: <b>SRP : Single Responsibility Principle</b> (Do one Thing) <i>Make sure a function/method perform only one action - Limit the LOC for a function within 60</i> <br>:heavy_check_mark: Use Java Stream APIs and Lambda expressions to process collections of objects <br>:heavy_check_mark: Use Annotation based validation for bean/request validation <br>:heavy_check_mark: Use <b>'var'</b> keyword to declare new variables which improves readability
Coding Standards/Formatting | :heavy_check_mark: Make sure source code follows the same code format <i>(This makes source code indented and formatted uniformly in all classes and <b>enhances readability</b> for the all developers & reviewers)</i> <br>:heavy_check_mark: Make sure all class members & variables are named as per the standard naming convention (camelCase). Use Solution/Problem Domain Names <br>:heavy_check_mark: Make class member & variable names descriptive. Try to avoid abbreviations in class/method/variable names <br>:heavy_check_mark: Use Intention-Revealing Names for functions <i>(names should begin with a verb)</i> <br>:heavy_check_mark: Agree upon the standard package naming and grouping scheme i.e. <i>reversed domain application name ex. com.pc.motherboard.gpu & package groups like model for bean files and so on.</i> 
Coding Standards/Formatting | :heavy_check_mark: Avoid magic literals; use named constants (make sure constants follow the standard naming convention ie. <b>THIS_IS_A_CONSTANT</b> <br>:heavy_check_mark: Consider an enum or a class with static strings to define related constants/group of constants
Coding/Exception Handling   | :heavy_check_mark: Proper Exception Handling <i>(Do not just re-throw exceptions - log them properly)</i>
Coding/Methods              | :heavy_check_mark: Return empty arrays or collections, not nulls. <i>Null returns will enforce additional null checks at multiple locations making the code more prone to null pointer exceptions</i>
Coding/Null handling        | :heavy_check_mark: Make sure null/empty comparisons are null-safe <i>(use null-safe comparison methods or ensure that null is on the left side of the comparison operator)</i> <br>:heavy_check_mark: Make use of Optionals where the values are prone to be null <br>:heavy_check_mark: Prefer equals in place of `==` for object comparison <br>:heavy_check_mark: When comparing, ensure the object under comparison is always on the right hand side to avoid NPE i.e. `"CONSTANT".equalsIgnoreCase("StringUnderComparison")` instead of `"StringUnderComparison".equalsIgnoreCase("CONSTANT")`
Commenting                  | :heavy_check_mark: Explain yourself in code (add proper comments)
Documentation               | :heavy_check_mark: Consider including design artefacts OAS documents in the code check-in under `/docs`
Input Validation            | :heavy_check_mark: Validate inputs (for valid data, size, range, boundary conditions, etc)Make use of validators, utility classes & [annotations](https://reflectoring.io/bean-validation-with-spring-boot/) & [custom annotations](https://blog.clairvoyantsoft.com/spring-boot-creating-a-custom-annotation-for-validation-edafbf9a97a4)
Logging                     | :heavy_check_mark: Make use of logging statements instead of SOPs & avoid logging sensitive data. Nit : Using `@Slf4j` from Lombok is preferred

##### Code Review best practices references:

##### Reference Links:
<li> https://dev.to/smartyansh/code-review-checklist-for-java-beginners-181f 
<li> https://www.romexsoft.com/blog/improve-java-code-quality/
<li> https://dzone.com/articles/java-code-review-checklist 
<li> https://www.win.tue.nl/~wstomv/edu/sc-hse/downloads/Series_01/checklist.pdf 
<li> http://www.cs.toronto.edu/~sme/CSC444F/handouts/java_checklist.pdf 

##### Recommended Reading:	
    Effective Java by Joshua Bloch
[Back Top &uarr;](#index)

# Git Repo Naming Conventions

Type of Repo        |   Naming Convention	                              |       Examples
--------------------|-----------------------------------------------------|---------------------------------
Microservice/API    |   `{GEAR-ID}-{LOB:optional}-{APP-NAME}-REST-service` <br> `{GEAR-ID}-{LOB:optional}-{APP-NAME}-rest-service`  |   6091-investor-profiles-rest-service <br> 6091-rs-investor-profiles-REST-service[^1]
Microservice/API Flavour : Orchestration Flavour    |   `{GEAR-ID}-{LOB:optional}-{APP-NAME}-rest-service`  <br> `{GEAR-ID}-{LOB:optional}-{APP-NAME}-orchestration-rest-service` <br> `{GEAR-ID}-{LOB:optional}-{APP-NAME}-orchestrator-rest-service`  |   6091-rs-investor-profiles-orchestrator-rest-service
Microservice/API Flavour : Data Flavour | `{GEAR-ID}-{LOB:optional}-{APP-NAME}-data-rest-service` |  6091-rs-investor-profiles-data-rest-service
Microservice/API Flavour : Batch        |  `{GEAR-ID}-{LOB:optional}-{APP-NAME}-batch` | 6091-rs-investor-profiles-batch
Microservice/API Flavour : Listener     |   `{GEAR-ID}-{LOB:optional}-{APP-NAME}-listener` <br>`{GEAR-ID}-{LOB:optional}-{APP-NAME}-listener-service` | 6091-rs-investor-profiles-listener
Microservice/API Flavour : Shared Library   | `{GEAR-ID}-{LOB:optional}-{APP-GROUP:optional}-shared-lib` | 6091-rs-investor-profiles-shared-lib
Microservice/API Flavour : Build Orchestration[^2]  |   `{GEAR-ID}-{LOB:optional}-{APP-GROUP}-orchestration` | 6091-rs-investor-profiles-orchestration
Microsite       |   `{GEAR-ID}-{LOB:optional}-{APP-NAME}-site`  |   6091-rs-investor-profiles-site
Microsite/Controls Module       |   `{GEAR-ID}-{LOB:optional}-{APP-NAME}-controls-module`  |   6091-rs-investor-profiles-control-module

[^1]: `REST` and `rest` terms can be interchanged
[^2]: This is the build orchestration repo that handles the orchestration of app deployments not to be confused with orchestration flavour

 
# Git PR Code Flow
 1. Create feature branch from `dev`
 2. Feature branch naming conventions
    <br> `Feature-{UserStoryRef}-{FeatureDescription}-{mmddyy:optional}` <br> Ex: <i>Feature-USRSTRY04-copyPlans</i> or <i>Feature-USRSTRY04-copyPlans-111422</i>
    <br> Including the date in the branch name will help us to identify since when the feature is branched out.
    <br> `Feature-reverseMerge-dev-{mmddyy:optional}`
    <br> `Feature-patch-dev-{mmddyy:optional}`
 3. Work on the `feature` branch for the changes. Raise a PR from `feature to dev`. If one or more developers are working on different features, it is always advised to sync the changes with each other.
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
