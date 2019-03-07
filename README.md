# gitflow
Git flow best practices in common web development

# GitFlow & Protocols

## Goal
There are many GitFlow best practices are there over the internet we can see but keeping in mind, as a developer the simple web development life cycle process here is simplest and easy to manage branch model. 

**NOTE**: We are only going to Git process not commands and assumed basic git commands are known to developers.

### Workflow
We will be using three branches (**development**, **staging** and **master**) concepts and protocol in GIT. Initialize repository and branch off development and staging from master (default) branch 

1. Create new branch: git co -b BranchName
2. Commit and Push branch into server: git push origin BranchName
    * Add proper commit description what exactly is worked upon or fixed
3. Create a **Pull Request** (Choose related branch) against the feature/hotfix branch initialized from by developer. Select **Reviewers** from the right side options **Lead of project**.
4. Review **Pull Request** by **Reviewer** and approve or request changes until code or logic approved
5. Once **Pull Request** is approved, merged it
6. Delete the merged (feature/hotfix)  branch from the repository 
7. Merge back pull request in development branch if branch is hotfix created from **staging/master** ( Please refer examples by branches section)
8. Switch back to branch and pull latest content merged into branch before starting any new work
    * e.g, git pull origin **development**

### Branch Protections
We need to add some rules in order to protect branch from delete or unauthorized access for merge or changes.


1. Go to Repository -> Settings
2. Click on **Branches**
3. Under **Branch Protection Rule**, click upon **Add Rule** button
4. Write down your branches name, e.g, **master**
5. Check following sections and set settings as followings
    * ☑  Require pull request reviews before merging
      * Required approval limits:1
      * ☑  Dismiss stale pull request approvals when new commits are pushed
      * ☑  Require review from Code Owners
      * ☑ Restrict who can dismiss pull request reviews

    * Select people who can dismiss the pull request ( MUST BE Leads )
      *  ☑ Restrict who can push to matching branches         
         Select list of people who can push to matching branches. It **MUST BE ONLY LEAD** who is responsible code merging and review)


### Examples by environment/branches
1. development
    * To work on features branches
    * Convention: **feature**-[FeatureName]
        
        e.g, git checkout **feature**-[FeatureName]
    * Once feature is completed, push into server
    
        e.g, git push origin **feature**-[FeatureName]
    * Goto git, create a pull request against development branch ( change and select development branch as the default branch would be master )

2. staging
    * To merge all release related features from development branch 
    * To fix any bug found in staging
    * Convention: **staging**-[Issue Description]
        e.g, **staging**-[Issue Description]
    * merge back all fixes into development branch
    * Merge final code into master using Pull Request

3. master
    * Create pull request from staging to master for production ready work from staging
    * to fix hotfix found on LIVE.
    * Convention: **hotfix**-[IssueNumner]-[Issue Description]
    * Merge back hotfix into **development** and **staging** branch

# Best Practices
  * Always take **PULL** into current working branch ( **development**, **staging** or **master** ) branch before creating new branch
  * Mention branch origin e.g, git pull origin **development**
  * Create **PULL REQUEST** in order to code/logic review or collaborate with other developers
  * Review the **PULL REQUEST**
    * Add feedback and ask developer to fulfill required changes and re-submit pull request
    * Approved pull request with proper comments
  * Code commits MUST have proper descriptive commit for the fix or features completed
      * e.g, git commit -m "Rename login button text logins to login"

