# ci-cd-in-node
In this tutorial, we see how you can use GitHub Actions to set up a CI/CD pipeline to your project
To use this tutorial, you will need the following:

- Node installed
- Basic knowledge of Node.js and Express
- Good knowledge of Git
- Jest and Heroku will be used, but it’s not compulsory to follow along

# Setting up GitHub Actions
Create a repository on GitHub, or you can use an existing repository. In the repository, click on the `Actions` tab. You will see this screen. A simple workflow with the minimum necessary structure is already suggested, and you have the option to set up a workflow yourself.
![image](https://github.com/user-attachments/assets/bd168ebd-53d5-4a8a-aa7d-989f06fa84cb).
Then use this code for blank.yml
```
# This is a basic workflow to help you get started with Actions

name: CI

# Controls when the workflow will run
on:
  # Triggers the workflow on push or pull request events but only for the "main" branch
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js
        uses: actions/setup-node@v2
        with: 
          node-version: "14.x"
  
      - name: Install dependencies
        run: npm install
  
      - name: Run test
        run: npm test
```
At this point, if we push this to our main branch, we will see this action run like this:
![image](https://github.com/user-attachments/assets/ede68528-ee3c-486d-a99c-dee208872222)
