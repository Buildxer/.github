# .github
# Developmental Workflow / Git Workflow
To enforce production stability and avoid unwanted production deployments, we need to set up a typical Git workflow based on branches.
  - **Master** [protected]
    The branch that has the current production software. It's protected (can only be updated through authorized PR). It needs to be always possible to deploy it in a safe state and 
    manually deployed it. Production is deployed manually, which means that CI/CD does all the dirty work, but you have to go to the CI pipeline to start the deployment manually.
    
  - **Staging** 
    The branch that has the current production software. It's protected (can only be updated through authorized MR). It needs to be always possible to deploy it in a safe state. It is
     manually deployed.
    
  - **Feature branches**
    The ones in which a feature is developed will be merged into the staging for testing. These should be named after the card number it was created from just for tracking.

  - **BugFix branches**
    The ones in which a bug  is to be fixed  and will be merged into the master for quick test testing. These should be named after the card number it was created from just for tracking.


# Sample Development Workflow 
We are going to create a sample example of the development process using bash cli below :

```bash

$ git clone <remote_url>

$ git checkout staging

# create a new branch based on what you want to do from  staging and
# It can be a feature/support e.t.c

$ git checkout -b '<action_type>/<feature_name>' staging  # add changes to the <action_type>/<feature_name>

$ git push


```

A general image description of the above is shown below 

![image](https://github.com/Buildxer/.github/assets/31941399/d7ac3a4e-dc4a-47d0-8eaf-b07b3d85555b)


# Contribution Guidelines

Please ensure your pull request adheres to the following guidelines:

- Follow ensure to read and understand the developmental workflow
- Make an individual pull request for each suggestion.
- Can suggest different categories as well.
- Start the Name with a capital.
- Check your spelling and grammar.
- Make sure your text editor is set to remove trailing whitespace.

Thank you for your suggestions!
