# version_control_blog - 01-03-2024 - 14:54
Final repository linked to my blog on using version control e.g. Git in your projects


## Latest Blog Edits


The purpose of this blog is to simulate the process of website/software development using version control. Part of the reason for this is because I so often work on my own and I'm not experienced in using Git to work in collaboration with others. I work with branches of course and try to introduce changes to code safely and iteratively but that's really it.  

I love working with Git to manage my work and as a backup source.  So on the 28th February I created a simple page that acts as a "development log" which represent stages of development of a project.  The "project" can be anything you like but in reality the repository  [LINK]is just this page.

Let's get started. (I'll show all my working out on the way)


Our starting point....



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link rel="stylesheet" type="text/css" href="style.css" />

    <title>Version Control Blog</title>
</head>

<body>
    

    <h1>A use case into the use of version control</h1>
    <hr />

    <table>
        <tr>
            <th>Version</th>
            <th>Details</th> 
        </tr>
        <tr>
            <td>1.0</td>
            <td>Sensors indicate no shuttle or other ships in this sector. Tractor beam released, sir.</td> 
        </tr>
        <tr>
            <td>1.2</td>
            <td>According to coordinates, we have travelled 7,000 light years and are located near the system J-25.</td>
        </tr>
        <tr>
            <td>1.3</td>
            <td>Without our shields, at this range it is probable a photon detonation could destroy the Enterprise.</td>
        </tr>
    </table>

    <div class="future-projects">

        <h2>Future Projects</h2>

        <ul>
            <li>Damage report? Sections 27, 28 and 29 on decks four, five and six destroyed.</li>
            <li>Radiation levels in our atmosphere have increased by 3,000 percent. </li>
            <li>We are going to Starbase Montgomery for Engineering consultations prompted by minor read-out anomalies.</li>
            <li>It indicates a synchronic distortion in the areas emanating triolic waves.</li>
        </ul>

    </div>

I also have a sass file with some basic styling applied. 

We'll add a new table row that represents the implementation of a new feature

```html
<tr>
    <td>1.4</td>
    <td>Damage report? Sections 27, 28 and 29 on decks four, five and six destroyed.</tr>
</tr>
```

Now that this is done, we need to add the change to the staging area and commit it.

```git add index.php```

```git commit -m "commit message goes here"```

This was done on the main branch, but in reality all development is done on separate branches leaving the main or the master branch ready for production code only.

### branching

Let's create a new branch where we can safely create changes to our code without affecting anything in the production branch

```git checkout -b new_feature```

we've now moved automatically to the new branch. But let's confirm anyway with the -a flag on git branch.

```git branch -a```

this will give us a list of all branches that exist in the local and remote repository. Now we're ready to implement our new feature. let's move to the new branch, using the checkout command.

```git checkout new_feature```

Can now implement the new changes 

```html
<table>
        <tr>
            <th>Version</th>
            <th>Details</th> 
        </tr>
        <tr>
            <td>1.0</td>
            <td>Sensors indicate no shuttle or other ships in this sector. Tractor beam released, sir.</td> 
        </tr>
        <tr>
            <td>1.2</td>
            <td>According to coordinates, we have travelled 7,000 light years and are located near the system J-25.</td>
        </tr>
        <tr>
            <td>1.3</td>
            <td>Without our shields, at this range it is probable a photon detonation could destroy the Enterprise.</td>
        </tr>
        <tr>
            <td>1.4</td>
            <td>Damage report? Sections 27, 28 and 29 on decks four, five and six destroyed.</td>
        </tr>
        <tr>
            <td>1.5</td>
            <td>Radiation levels in our atmosphere have increased by 3,000 percent.</td>
        </tr>
    </table>
```

```add index.php```

```git commit -m "add feature 1.5"```

now we have to make sure the new branch is available in the remote repository. 

```git push --set-upstream origin new_feature```- writing this command doing this will add the branch on github

use ```git checkout <branch_name>``` to switch between branches and compare versions. 

It's important to update and remove unndeded branches regularly. We can see that we can cleanly merge the changes in new_feature to the main branch.

```git checkout main```

```git merge new_feature```

With the branches succesfully merged we can remove the new feature branch from both the local and remote repository.

the git log shows all the branches used to create this new feature, but only while those bracnches exist.  Let's keep the branches clean by deleting them from the log and the list of existing branches


```git branch -d new_feature```


```git branch origin -d new_feature``` or ```git branch origin --delete new_feature```

### The Git Flow Strategy

Now we're up to log 1.5

We have since develped a new feature.  1.6.

Let's reflect this using the Git Flow strategy

git checkout -b develop
git checkout -b feature/feature_v1_6

We've created 2 new local branches. And they need to be linked to remote branches. 

git push -u origin feature/feature_b1.6
git push -u origin develop

We're now ready to develop changes and keep it up to date with the remote repository.

git branch -d feature/feature_v1.6 develop  

````git commit -m "first implementation of log 1.6"```

let's make sure the branches are up to date.
git push
git checkout feature/feature_v1.6
git merge develop


This will bring the changes from develop, into feature_v1.6

But there's been a bug reported in the system.

Let's go back to the develop branch and take a look.

```git checkout develop```

Let's represent our bug fix by changing the text content of the 1.6 log. 

"Force fields have been established on all turbo lifts and crawlways. Computer, run a level-two diagnostic on warp-drive systems."

```git add index.php```

```git commit -m "implement feature fix v1.6"```

We should merge this into the feature branch

```git checkout feature/feature_v1.6```

```git merge develop.```  

Now when I run git status the branch is ahead of the remote repository by 2 commits. Which we can fix by git push

The fix is now ready and can be safely merged to the main branch

git checkout main

git merge develop   

Now when you run git status it shows us that the branch is ahead - ahead by 2

git push


We can now delete the branches locally whuch  cam be achieved in one command

git branch -d develop feature/feature_v1.6

git push origin -d origin develop feature/feature_1.6

Hope this gives you can idea of what is involved in managing and developing projects using version control.

Link to Blog - Coming Soon

## Steps to Take

`git status` - verifies this is a functional Git repository.

`$ git remote get-url origin`
`https://github.com/jg-digital-media/version_control_blog` - verifies the url of the repository


```git add index.php``` - add files to staging area ready for commit

```git commit -m "commit message goes here"``` - commit changes to the current branch

```git checkout -b new_branch``` - Create a new branch and automatically switch to it

```git push --set-upstream origin new_branch``` or ```git push -u origin develop``` - Create a link to a branch in the remote repository

```git checkout main``` or ```git checkout new_branch``` - Switch between branches in local repository

```git merge new_branch```- merge changes from one branch into the current branch

```git branch -a```- list local and remote branches

```git branch -d new_branch``` - deleted named local branch

```git push origin --delete <branch_name>``` or ```git push origin -d new_branch``` or ```git branch push -d <branch_one> <branch_two>``` - deleted named remote branch

``````