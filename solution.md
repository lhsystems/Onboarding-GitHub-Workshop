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
            uses: actions/checkout@v4
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

1. Simply create an index.md file with the content of your choice

## Task 5: Create a static web page

1. Add the following lines to your created `.md` file:

        ---
        title: My First Page
        layout: default
        ---
    You can modify the title and layout if you want
2. Create a `Gemfile` with the following content:

        # Gemfile
        source 'https://rubygems.org'
        gem 'jekyll', '~> 4.2'
3. Browse to your Repository Settings and Select 'Pages'
4. At 'Build and Deployment' select the Source 'GitHub Actions'
5. Create a workflow based on the recommendation
6. Create a Pull Request and merge the changes

## Task 6

1. After a successful run of the previously created workflow
go to the "Settings" Tab
2. Select "Pages"
3. At "Source" select Branch: `gh-pages` and Save.
4. After the now triggered Actions workflow the page will be available at the shown
link

## Task 7

1. Create another workflow file in your `.github/workflows` directory
2. add the following content:

        name: Build and zip Jekyll and publish it to GitHub packages

        on:
        push:
            tags:
            - '*'

        jobs:
        publish-zip:
            runs-on: ubuntu-latest
            steps:
            - name: Ckechout git repo
                uses: actions/checkout@v4
            - name: Build
                uses: jerryjvl/jekyll-build-action@v1
            - name: Create .zip File
                uses: TheDoctor0/zip-release@0.7.1
                with:
                path: './_site/*'
            - name: Upload Artifact
                uses: ncipollo/release-action@v1
                with:
                artifacts: "release.zip"
                token: ${{ secrets.GITHUB_TOKEN }}

3. Create a tag using the following commands:

        git tag -a v1.0
        git push origin v1.0

## Bonus Task

1. Add the Account-Key provided by us as an Action-Secret in GitHub
2. Expand the `lint.yml` workflow with an additional job with the following content:

          Deploy-Azure:
            needs: Markdown-Linter
            runs-on: ubuntu-latest
            steps:
            - name: Check out code
            uses: actions/checkout@v4
            - name: Build
            uses: jerryjvl/jekyll-build-action@v1
            - name: Upload to blob storage
            uses: azure/CLI@v1
            with:
                inlineScript: |
                az storage blob upload-batch --account-name <STORAGE ACCOUNT>
                --auth-mode key --account-key ${{ secrets.AZURE_BLOB_SECRET }}
                -d '$web' -s ./_site

3. Create a Pull Request
