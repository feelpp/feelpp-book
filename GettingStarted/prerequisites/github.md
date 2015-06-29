##GITHUB
GitHub is a web-based Git repository hosting service, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features.
GitHub has become the industry-standard version control and publishing platform for web developers, but it's great for designers to

If you are new to github, these are the basic things you need to know to get started with GitHub:
   
 -  CREATING A PERSONAL ACCOUNT   
 The first step to using GitHub is to set up a personal [GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/).If you already have an account, visit [github.com](thub.com) and sign in.
 
 - CREATING A REPO   
Once Git is installed, using it is just a matter of navigating to the directory that you want to manage, and then initializing it. And this process is called [creating a Repository](https://help.github.com/articles/create-a-repo/) or repo for short. A single installation of Git, can track as many repos as you'd like. This can be done in the terminal as follows.   

```sh
$ mkdir ~/stage
# Creates a directory for your project called "stage" in your user directory   
 
$ cd ~/stage
# Changes the current working directory to your newly created directory

$ git init
# Sets up the necessary Git files
# Initialized empty Git repository in /Users/you/stage/.git/


$ git remote add origin https://github.com/username/Hello-World.git
#Creates a remote named "origin" pointing at your GitHub repository

$ git push origin master
# Sends your commits in the "master" branch to GitHub
```

- ADDING files   
Now that we have a Git repo up and running, we need to add some files for it to track. Now remember, git doesn't just automatically track every file in the directory as soon as you put it there. It only tracks the files that you tell it to, a file can be either tracked or untracked. Now since we don't have a commit as soon as we add some files to this folder automatically they are going to come in as untracked files. To add files to a repo, in the command line type:  
   ``` git add file_Name  ```   
   
- MAKING A COMMIT   
After we have added some files to our empty Git repo,(we used the Git add Cmd to then stage those files). So, the next step is to go ahead, and do the commit itself. To add a commit message, in the command line, write:   
```sh  
git commit -m "write the commit message"
```   
***NOTE***: *A commit must be made each time a file is modified or updated*.

- Checking differences   
Most of the time you're going to want to automatically add all of your modified files for your next commit. But there are times when you might want to check to see what's been changed before you make your commit:   
``` git diff ```   
Inside the index file, it'll show you the changes in two ways.

  If you have a branch set up to track a remote branch, you can use the   
```git pull```   
command to automatically fetch and then merge a remote branch into your current branch. 

- Pushing to Your Remotes   
When you have your project at a point that you want to share, you have to push it upstream. The command for this is simple:   
 ```git push [remote-name] [branch-name] ```.    
If you want to push your master branch to your origin server, then you can run this to push any commits you’ve done back up to the server:   
``` git push origin master```   
This command works only if you cloned from a server to which you have write access and if nobody has pushed in the meantime. If you and someone else clone at the same time and they push upstream and then you push upstream, your push will rightly be rejected. You’ll have to pull down their work first and incorporate it into yours before you’ll be allowed to push.   
*NOTE: ```git remote rename file_name``` and ```git remote rm file_name``` will rename and remove the given file respectively from a repo.*

- GIT PULL REQUEST   
[Pull requests](https://www.atlassian.com/git/tutorials/making-a-pull-request/) let you tell others about changes you've pushed to a repository on GitHub.The request, printed to the standard output, summarizes the changes and indicates from where they can be pulled.   
```git request-pull' [-p] <start> <url> [<end>]```   
  The upstream project is expected to have the commit named by ```<start>``` and the output asks it to integrate the changes you made since that commit, up to the commit named by ```<end>```, by visiting the repository named by ```<url>```.   
 - OPTIONS   
```-p``` nclude patch text in the output.   
``` <start> ```
Commit to start at. This names a commit that is already in the upstream history.   
``` <url> ``` The repository URL to be pulled from   
```<end> ```

- ISSUES   
Issues are a great way to keep track of tasks, enhancements, and bugs for your projects. They’re kind of like email—except they can be shared and discussed with the rest of your team. Most software projects have a bug tracker of some kind. GitHub’s tracker is called Issues, and has its own section in every repository.See how to create an issue [here](https://help.github.com/articles/creating-an-issue/).
A title and description describe what the issue is all about.   

- Notifications   
 Notifications are GitHub’s way to keep up to date with your Issues. You can use them to find out about new issues on repositories, or just to know when someone needs your input to move forward on an issue.
There are two ways to receive notifications: via email, and via the web. You can [configure](https://help.github.com/articles/configuring-notification-emails/) how you receive notifications in your settings. If you plan on receiving a lot of notifications, we like to recommend that you receive web + email notifications for Participating and web notifications for Watching.

- MILESTONES   
Milestones are used to track the progress of similar issues and pull requests as they're opened and closed over time. At a glance, you can easily see the progress of work in a milestone's lifetime. Once you’ve collected a lot of issues, you may find it hard to find the ones you care about. [Milestones, labels, and assignees](https://guides.github.com/features/issues/) are great features to filter and categorize issues.

For quick refferences visit [GitHub guides](https://guides.github.com/). This will give you the basic knowledge to get started into GitHub.