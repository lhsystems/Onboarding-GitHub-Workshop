# Lufthansa Systems ITCS Hamburg Workshop

This repository shows an example solutions to the tasks of the 
Lufthansa Systems Workshop at the ITCS Hamburg

## Tasks :rocket:

1. Create a **public** GitHub repository. You can simply use your
existing GitHub account or you can create a new one for free
[here](https://github.com/signup). </p>
Make sure it is a **public** repository in order to make sure we
have all needed features available</p>
2. Create a **rule** in your repository that prevents anybody from
pushing directly to the main branch. Use seperate development
branches instead.</p>
3. Create a **GitHub Actions Workflow** in your repository.
It should be triggered everytime there is a change to a
**Pull Request** and run a linter to check the **Markdown** Code.
You can find a default config
[here](https://github.com/DavidAnson/markdownlint/blob/main/schema/.markdownlint.yaml) \
Edit the branch protection to only allow merges when
the lint has been successful.</p>
4. Create a simple document using **Markdown**. A short
introduction to Markdown can be found
[here](https://www.markdownguide.org/basic-syntax/).
If you want you can also create multiple files and subfolder.
Just be creative :).</p>
6. In the your **Workflow**, use
**[Jekyll](https://jekyllrb.com/docs/continuous-integration/github-actions/)**
to create a static web page using your Markdown-Files everytime
there is a push on the main branch.</p>
7. Publish the generated website to **GitHub Pages**</p>
8. Package your website in a **.zip** and publish it to
**GitHub Packages** so that other users can download the .zip.
This should be done automatically everytime you create a new
**Tag** in your repository</p>
    ### **Bonus Task :top:\:**
    Configure your **Workflow** to deploy an **INT**-Version of your
    webpage to the **Azure Blob Store** every time a pull request is
    opened. *Please contact us on how to use the Azure Blob Store*

## Contact :phone:

This Workshop is held by\:

* [Steffen Wagner](https://github.com/wagnst)
* [Benedikt Funke](https://github.com/benfu99/)

&nbsp;  
&nbsp;  

[![lhsystems](/img/lh_lufthansa_systems_1lin_blue_RGB.png)](https://www.lhsystems.com/)
