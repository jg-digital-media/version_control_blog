# version_control_blog - 28-02-2024 - 16:38
Final repository linked to my blog on using version control e.g. Git in your projects


## Latest Blog Edits

```
The purpose of this blog is to simulate the process of website/software development using version control. Part of the reason for this is because I so often work on my own and I'm not experienced in using Git to work in collaboration with others. I work with branches of course and try to introduce changes to code safely and iteratively but that's really it.  

I love working with Git to manage my work and as a backup source.  So on the 28th February I created a simple page that acts as a "development log" which represent stages of development of a project.  The "project" can be anything you like but in reality the repository  [LINK]is just this page.

Let's get started.  (I'll show all my working out on the way)
```

our starting point....



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

```
I also have a sass file with some basic styling applied. 
```

### git add 

```

<tr>
    <td>1.4</td>
    <td>Damage report? Sections 27, 28 and 29 on decks four, five and six destroyed.</tr>
</tr>
```

```git add index.php```

```git commit -m "commit message goes here"```

### branching

```git checkout -b new_feature```

we've now moved automatically to the new branch. But let's confirm anyway with the -a flag on git branch.

```git branch -a```

now we're ready to implement our new feature. let's move to the new branch, using the checkout command

```git checkout new_feature```

Can now implement the new changes 

```
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

add index.php

git commit -m "add feature 1.5"

now we have to make sure the new branch is available in the remote repository. 

git push --set-upstream origin new_feature  - doing this will add the branch on github

use git checkout branch> to switch between branches and compare versions. 

It's important to update and remove unndeded branches regularly.  We can see that we can cleanly merge the changes in new_feature to the main branch.

git checkout main

git merge new_feature

With the branches succesfully merged we can remove the new feature branch from both the local and remote repository.


the git log shows all the branches used to create this new feature, but only while those bracnches exist.



git branch -d new_feature


git branch origin -d new_feature or git branch origin --delete new_feature

Now we're up to log 1.5




## Steps to Take

`git status` - verifies this is a functional Git repository.

`$ git remote get-url origin`
`https://github.com/jg-digital-media/version_control_blog` - verifies the url of the repository


```git add index.php```

```git commit -m "commit message goes here"```

```git checkout -b new_branch```

```git push --set-upstream origin new_branch```

```git checkout main - git checkout new_branch```

```git merge new_branch``` - merge changes to main/master branch

```git branch -a```- list local and remote branches

```git branch -d new_branch``` - deleted named local branch

```git branch origin -d new_branch``` - deleted named remote branch

``````