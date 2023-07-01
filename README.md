# .github











# Developmental Workflow / Git Workflow
To enforce production stability and avoid unwanted production deployments, we need to set up a typical Git workflow based on branches.
  - **Master** [protected]
    The branch that has the current production software. It's protected (can only be updated through authorized PR). Needs to be always possible to deploy it in a safe state. 

    Manually deployed. Production is deployed manually, which means that CI/CD does all the dirty work, but you have to go to the CI pipeline to start manually the deployment.
    
  - **Sandbox** [protected]
    Public testing branch. The branch is auto-deployed to a sandbox environment and it's the one in which features are pushed for pre-production testing and acceptance.
    
  - **Staging** 
    The branch that has the current production software. It's protected (can only be updated through authorized MR). Needs to be always possible to deploy it in a safe state. It is
     
    manually deployed.
    
  - **Release**
    This branch is where we need to merge everything which will be released in the next production release. It will go from here to the sandbox usually.
    
  - **Feature branches**
    The ones in which a feature is developed. These should be named after the Trello card number it was created from just for tracking.

# Release Workflow
We are going to push changes in releases to production, so we need to create a stable branch for each release. The branches are going to start with releases/ on their name.

```bash
$ git checkout master

$ git fetch

$ git reset --hard origin/master

$ git checkout -b releases/<release_name>
```

Then, each feature is developed and a merge request is made to merge it to the release branch.

Also, when the release is over and we want to deploy it, the release is merged into the master.

# Feature development workflow
Create a branch from the master (or the release branch, if you need a previous change).

```bash
$ git checkout master

$ git fetch

$ git reset --hard origin/master

$ git checkout -b features/<feature_name>
```

Develop your changes in `features/<feature_name>` 

Merge changes to staging for internal testing:

```bash
$ git checkout staging

$ git fetch

$ git reset --hard origin/staging

$ git merge features/<feature_name>

$ git push
```

When the feature is ready from our side, create a merge request from the feature branch to the release branch, getting changes from that branch first to your branch.

```bash
$ git checkout release

$ git fetch

$ git reset --hard origin/release

$ git checkout features/<feature_name>

$ git merge release

$ git push
```

And then create the Merge Request on GitLab from features/<feature_name> to release.

If this needs to be tested by clients first, we need to merge it into the sandbox:

```bash
$ git checkout sandbox

$ git fetch

$ git reset --hard origin/sandbox

$ git merge releases/<release_name>

$ git push
```

And please, remember to test the changes in the sandbox  if it needs to be tested.

Once a release is ok to be released, it will be merged into sandbox and sandbox into master.


# Contribution Guidelines

Please ensure your pull request adheres to the following guidelines:

- Follow ensure to read an understand the developmental process of
- Make an individual pull request for each suggestion.
- Can suggest different categories as well.
- Start the Name with a capital.
- Check your spelling and grammar.
- Make sure your text editor is set to remove trailing whitespace.

Thank you for your suggestions!
