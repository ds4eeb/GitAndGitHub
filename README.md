# Introduction to Git and GitHub

Welcome! Today's assignment will walk you through using Git, GitHub, RStudio to interact with both, and, along the way, practice using Quarto and RStudio. Cool! The content has been adapted from a [workshop](https://rstudio-conf-2020.github.io/r-for-excel/github.html) that Openscapes developed.

Please work with a partner on one computer and take turns "driving" (touching the keyboard) vs. "navigating" (figuring out what to do). This is called pair programming and is common practice in industry and computer science.

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

## 3. Clone your repository using RStudio
Let’s clone your repo on GitHub to your local computer using RStudio. Unlike downloading, cloning keeps all the version control and user information bundled with the files.

### 3.1 Copy the repo address
First, copy the web address of the repository you want to clone. We will use HTTPS.

<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/gh_repo_clone1.png" width="600" />
</p>

### 3.2 Paste the repo address
Paste the repo address (which is still in your clipboard) into in the “Repository URL” field in RStudio, where you should still have the New Project wizard in progress. The “Project directory name” should autofill; if it does not press tab, or type it in. It is best practice to keep the “Project directory name” THE SAME as the repository name.

When cloned, this repository is going to become a folder on your computer.

At this point you can save this repo anywhere. There are different schools of thought, but we think it is useful to create a high-level folder for this class where you will keep your github repos to keep them organized. Press “Browse…” to navigate to a folder and you have the option of creating a new folder.

Finally, click Create Project.

<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/gh_repo_clone2.png" width="600" />
</p>

### 3.3 Admire your local repo
If everything went well, the repository will show up in RStudio!

<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/gh_repo_clone3.png" width="600" />
</p>

The repository is also saved to the location you specified, and you can navigate to it as you normally would in Finder or Windows Explorer:
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/gh_repo_clone4.png" width="600" />
</p>

Hooray!

### 3.4 Inspect your local repo
Let’s notice a few things:

First, our working directory is set to the location of the repo and the Project (they are both in the same place), and GitAndGitHub is also named in the top right hand corner.

Second, we have a Git tab in the top right pane! Let’s click on it.
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/gh_repo_clone5.png" width="600" />
</p>

Our Git tab has one item, an `.Rproj` file.

This has been added to our repo by RStudio — we can also see it in the File pane in the bottom right of RStudio. This is a helper file that RStudio has added to streamline our workflow with GitHub and R. Note that this files begins with a period (`.`), which means they are hidden files: they show up in the Files pane of RStudio but won’t show up in your Finder or Windows Explorer.

Going back to the Git tab, both these files have little yellow icons with question marks `?`. This is GitHub’s way of saying: “I am responsible for tracking everything that happens in this repo, but I’m not sure what is going on with these files yet. Do you want me to track them too?”

We will handle this in a moment; first let’s look at the README.md file.

## 4. Edit the README file
The `README.md` file (which you have been following as instructions, by the way) is a GitHub-flavored Markdown file, which is very similar to Quarto. It’s like a Quarto file without the abilities to run R code. It does, however, have the super-power of being displayed easily on GitHub, which made these instructions easy to read.

We will edit the file and illustrate how GitHub tracks files that have been modified (to complement seeing how it tracks files that have been added).

README files are common in programming; they are the first place that someone will look to see why code exists and how to run it.

Open the README by making sure the Files pane is selected in the lower right, then clicking the README.md file. It will open in the Scripts pane (upper left).
<p align="center">
<img src="https://github.com/ds4eeb/GitAndGitHub/blob/main/edit1.png" width="600" />
</p>

In your README, find the Header. It should begin with a hastag `#`.

Please edit it to include your name and your partner's name. Make sure you keep the `#` so that it still displays as a header! Something like:

`# Malin's GitAndGitHub repo`

Save this file (Cmd/Ctrl-S or File -> Save) and notice how it shows up in your Git tab. It now has a blue “M”: GitHub is already tracking this file line-by-line, so it knows that something is different: it’s Modified with an M.

Great! You just made your first edits to a Git repository. Now let’s sync these changes back to GitHub.


