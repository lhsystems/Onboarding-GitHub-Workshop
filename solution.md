# Example Solution

In this file you will find an example solution to the tasks.
There might be other solutions as well

## Task 1: Create a Repository

1. Click on your profile picture on the top-left corner
2. Select "Your repositories"
3. Click on "New" and give a name to the repository.
Make sure to create a public repository.

## Task 2: Add a branch protection rule

1. Browse to your repository
2. Go to the "Settings" Tab
3. Select "Branches"
4. In the Section "Branch protection rules" click "Add rule"
5. In the "Branch name pattern" add `main` and select
"Require a pull request before merging" but not
"Require approvals"

## Task 3: Set up a linter

1. Create a new branch
2. Create a folder `.github/workflows`
3. Create a .yml with a name of your choice
4. paste the following content:
        name: Demo Workflow
        on:
        pull_request

        jobs: 
        Markdown-Linter:
            runs-on: ubuntu-latest
            steps:
            - name: Check out code
            uses: actions/checkout@v2
            - name: markdownlint-cli
            uses: avto-dev/markdown-lint@v1
            with:
                args: '.'
                config: '.markdownlint.yml'
5. paste the file `.markdownlint.yml` into your main folder
6. go to your newly created Branch protection rule and edit it
7. Select "Require status checks to pass before merging" and search
for the job name

## Task 4: Create a markdown file

1. Simply create a .md file with the content of your choice
