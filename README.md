# Introduction to Git and GitHub

Welcome! Today's assignment will walk you through using Git, GitHub, RStudio to interact with both, and, along the way, practice using Quarto and RStudio. Cool!

## 1. Create your repository
The first step is to create the assignment repository in your personal GitHub account so that you can work on it. You will use the ds4eeb repository as a template.

To do that, click the green "Use this template" button in the upper right and select "Create in a new repository."  
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/usetemplate.jpg" width="400" />
</p>

Please start the name of your repository with "GitAndGitHub" so that we can identify it later, and choose Public for Visibility.

Admire your first repo! It should look a lot like the ds4eeb one you started with, but now it's in your own account. You can see that in the URL (web address) and in the upper left of the GitHub page, where it shows the repo name after your account name.
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/ownrepo.png" width="400" />
</p>

## 2. Set up RStudio to communicate with GitHub
### 2.1 Install packages
We're going to use a "package" called `usethis` to make it easy for RStudio and GitHub to work together. In R, a package bundles together reusable code to accomplish a particular purpose, along with data and documentation, and is easy to share with others. Packages are part of what makes R so powerful because anyone can improve or add to existing base R capabilities.

The traditional place to download packages is from CRAN, the Comprehensive R Archive Network, which is the same place you downloaded R. As Julie Lowndes has said, CRAN is like a grocery store or iTunes for vetted R packages.

Open RStudio on your computer and type this in the console:  
```
install.packages("usethis")
```

You should see R respond by saying it is trying and then downloaded the package. Now that you have the package, you shouldn't need to download this package again. 

Now you need to activate (or "attached") the package to your current session in R. You'll need to do this each time you want to use the package in a new R session. Type this in the console:  
```
library("usethis")
```

When `usethis` is successfully attached, you won’t get any feedback in the Console. So unless you get an error, this worked for you.

Now let’s do the same with the `here` package, which makes it easy to work with file paths in RStudio projects:
```
install.packages("here")
library("here")
```

`here` is a “chatty” package and, when attached, responds with the filepath we are working from.

### 2.2 Configure Git in RStudio
This next set up step is a one-time thing! You will only have to do this once per computer.

You will need to know your GitHub username, the email address you created your GitHub account with, and your GitHub password.

We will be using the use_git_config() function from the usethis package we just installed. Since we already installed and attached this package, type the following into your Console, but replace USERNAME with your GitHub username, and replace EMAIL with the same email you used to create your GitHub account:

```
use_git_config(user.name = "USERNAME", user.email = "EMAIL")
```

If you see `Error in use_git_config() : could not find function "use_git_config"`, please run `library("usethis")`

You can check that things worked and diagnose problems by typing this in the console:
```
# check by running a git situation-report: 
#   - your user.name and user.email should appear in global Git config 
git_sitrep()
```

### 2.3 Ensure that Git/GitHub/RStudio are communicating
We are going to go through a couple steps to make sure the Git/GitHub are communicating with RStudio.

First, create a new project by clicking on the drop-down menu in the upper right and selecting "New Project". Alternatively, you could also go to File > New Project…, or click the little white + in a green circle with the R box in the top left.
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/newproject1.png" width="600" />
</p>

Next, select Version Control:
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/newproject2.png" width="400" />
</p>

Then select Git (since we are using Git):
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/newproject3.png" width="400" />
</p>

Do you see this?
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/newproject4.png" width="400" />
</p>

If yes, hooray! If no, we will help you troubleshoot.

1. Double check that your GitHub username and email are correct
2. Troubleshooting, starting with [HappyGitWithR’s troubleshooting chapter](https://happygitwithr.com/troubleshooting.html)

* `which git` (Mac, Linux, or anything running a bash shell)
* `where git` (Windows, when not in a bash shell)
