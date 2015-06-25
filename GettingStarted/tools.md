Here is the list of basic tools we need for Feel++ :
##GITHUB
GitHub is a web-based Git repository hosting service, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features.

At the heart of GitHub is Git, an open source project started by Linux creator [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds). Matthew McCullough, a trainer at GitHub, explains that Git, like other version control systems, manages and stores revisions of projects. Although it’s mostly used for code, McCullough says Git could be used to manage any other type of file, such as Word documents or Final Cut projects. Think of it as a filing system for every draft of a document.

GitHub offers free public [repositories](https://www.atlassian.com/git/tutorials/setting-up-a-repository) and collaborations for open-source software creation and charges small and large businesses for private repositories and collaboration. From a social perspective, GitHub allows users to change, adapt and improve software — each project is called a ["fork"](https://help.github.com/articles/fork-a-repo/) — in its public repositories. Users can work together in teams or alone. Public users create profiles which display repositories and public activity and help programmers find projects.

GitHub has become the industry-standard version control and publishing platform for web developers, but it's great for designers too.Some people have referred to GitHub as a publishing tool. While others might refer to it as a version control system and still other people might describe it as a collaboration platform. Well, actually GitHub is all of those things in one form or another.

If you are new to github,these are the basic things you need to know to get started with GitHub:
   
 -  CREATING A PERSONAL ACCOUNT   
 The first step to using GitHub is to set up a personal [GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/).If you already have an account, visit [github.com](thub.com) and sign in.
 
 - GItHub DOCUMENTATION

 Like most hosted services, GitHub has a wealth of online documentation, that can help you get set up and it can serve as a great reference for you as you're learning. You'll notice, for example, that the first time you come to GitHub after setting up an account, you've got these four information blocks right in front of you, front and center, and they're designed to help you set up Git. Create repositories, so, where you'll work on your projects. For existing repositories, so you can work on some other people's projects. And show off some of the social tools that are baked into GitHub as well. For quick refferences visit [GitHub guides](https://guides.github.com/). This will give you the basic knowledge to get started into GitHub.   
 - CREATING A REPO

Once Git is installed, using it is just a matter of navigating to the directory that you want to manage, and then initializing it. And this process is called [creating a Repository](https://help.github.com/articles/create-a-repo/) or repo for short. A single installation of Git, can track as many repos as you'd like. So, once it's installed you can just start using it.
    
- ADDING collaborators

I want to talk about collaborating with GitHub. GitHub has some amazingly powerful collaboration tools and you can use them in a variety of interesting ways and workflows. To learn more about how collaborating works on GitHub, click [here](https://help.github.com/categories/collaborating/)
 
- ADDING files

Now that we have a Git repo up and running, we need to add some files for it to track. Now remember, git doesn't just automatically track every file in the directory as soon as you put it there. It only tracks the files that you tell it to, a file can be either tracked or untracked. Now untracked files or a file that have been added since the last commit. Now since we don't have a commit as soon as we add some files to this folder automatically they are going to come in as untracked files. To add files to a repo, in the command line type:

   ``` git add file_Name  ```   
   
   - MAKING A COMMIT

After we have added some files to our empty Git repo,(we used the Git add Cmd to then stage those files). So, of course, the next step that once you have all the files staged that you want for your next commit, the next step is to go ahead, and do the commit itself. And that's taking that sort of snapshot of the project. At that moment in time.To add a commit message, in the command line, write:

``` git commit -m "write the commit message" ```

NOTE: A commit must be made each time a file is modified or updated.

- Checking differences

Most of the time you're going to want to automatically add all of your modified files for your next commit. But there are times when you might want to check to see what's been changed before you make your commit. For example maybe you're working with a team member and you're not exactly sure what has changed. Or maybe you've been working for a couple of days and you're not sure whether you made a change to a file or not. Well to do that,in terminal write:

``` git diff ```


Inside the index file, it'll show you the changes in two ways.

- Fetching and Pulling from Your Remotes

To get data from your remote projects, you can run:

```
git fetch [remote-name]
```
The command goes out to that remote project and pulls down all the data from that remote project that you don’t have yet. After you do this, you should have references to all the [branches](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches) from that remote, which you can merge in or inspect at any time.

If you [clone](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-init) a repository, the command automatically adds that remote repository under the name “origin”. So, git fetch origin fetches any new work that has been pushed to that server since you cloned (or last fetched from) it. It’s important to note that the git fetch command pulls the data to your local repository – it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.

If you have a branch set up to track a remote branch, you can use the ```git pull``` command to automatically fetch and then merge a remote branch into your current branch. This may be an easier or more comfortable workflow for you; and by default, the git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called) on the server you cloned from. Running git pull generally fetches data from the server you originally cloned from and automatically tries to merge it into the code you’re currently working on.

- Pushing to Your Remotes

When you have your project at a point that you want to share, you have to push it upstream. The command for this is simple: 
```git push [remote-name] [branch-name ```. 
      
If you want to push your master branch to your origin server (again, cloning generally sets up both of those names for you automatically), then you can run this to push any commits you’ve done back up to the server:

``` git push origin master```

This command works only if you cloned from a server to which you have write access and if nobody has pushed in the meantime. If you and someone else clone at the same time and they push upstream and then you push upstream, your push will rightly be rejected. You’ll have to pull down their work first and incorporate it into yours before you’ll be allowed to push.

NOTE: ```git remote rename file_name``` and ```git remote rm file_name``` will rename and remove the given file respectively from a repo.

- GIT PULL REQUEST

[Pull requests](https://www.atlassian.com/git/tutorials/making-a-pull-request/) let you tell others about changes you've pushed to a repository on GitHub. Once a pull request is sent, interested parties can review the set of changes, discuss potential modifications, and even push follow-up commits if necessary.The request, printed to the standard output, summarizes the changes and indicates from where they can be pulled.  

      FORK AND PULL
   
The fork & pull model lets anyone fork an existing repository and push changes to their personal fork without requiring access be granted to the source repository. The changes must then be pulled into the source repository by the project maintainer. This model reduces the amount of friction for new contributors and is popular with open source projects because it allows people to work independently without upfront coordination.

Pull requests are especially useful in the fork & pull model because they provide a way to notify project maintainers about changes in your fork. However, they're also useful in the shared repository model where they're used to initiate code review and general discussion about a set of changes before being merged into a mainline branch.
```git request-pull' [-p] <start> <url> [<end>]```

Generate a request asking your upstream project to pull changes into their tree. The request, printed to the standard output, summarizes the changes and indicates from where they can be pulled.

The upstream project is expected to have the commit named by ```<start>``` and the output asks it to integrate the changes you made since that commit, up to the commit named by ```<end>```, by visiting the repository named by ```<url>```.

OPTIONS

```-p``` nclude patch text in the output.

``` <start> ```
Commit to start at. This names a commit that is already in the upstream history.

``` <url> ``` The repository URL to be pulled from.

 ```<end> ```

- ISSUES

Issues are a great way to keep track of tasks, enhancements, and bugs for your projects. They’re kind of like email—except they can be shared and discussed with the rest of your team. Most software projects have a bug tracker of some kind. GitHub’s tracker is called Issues, and has its own section in every repository.See how to create an issue [here](https://help.github.com/articles/creating-an-issue/).
A title and description describe what the issue is all about.

- Notifications

Notifications are GitHub’s way to keep up to date with your Issues. You can use them to find out about new issues on repositories, or just to know when someone needs your input to move forward on an issue.

There are two ways to receive notifications: via email, and via the web. You can [configure](https://help.github.com/articles/configuring-notification-emails/) how you receive notifications in your settings. If you plan on receiving a lot of notifications, we like to recommend that you receive web + email notifications for Participating and web notifications for Watching.

- MILESTONES

Milestones are used to track the progress of similar issues and pull requests as they're opened and closed over time. At a glance, you can easily see the progress of work in a milestone's lifetime. Once you’ve collected a lot of issues, you may find it hard to find the ones you care about. [Milestones, labels, and assignees](https://guides.github.com/features/issues/) are great features to filter and categorize issues.

##DOXYGEN
Doxygen is a tool for auto-generating API documentation, though you can also use it to generate documentation separate from an API.It can generate documentation from annotated C++ sources, but it also supports other popular programming languages such as C, Objective-C, C#, PHP, Java, Python, IDL (Corba, Microsoft, and UNO/OpenOffice flavors), Fortran, VHDL, Tcl, and to some extent D.The main advantage of Doxygen is that you can write documentation directly within the comments of your source code. Doxygen searches for source code in your tree and generates API documentation for it.   
 - It can generate an on-line documentation browser (in HTML) and/or an off-line reference manual in LaTeX  from a set of documented source files. There is also support for generating output in RTF (MS-Word), PostScript, hyperlinked PDF, compressed HTML, and Unix man pages. The documentation is extracted directly from the sources, which makes it much easier to keep the documentation consistent with the source code.   
 - You can configure doxygen to extract the code structure from undocumented source files. This is very useful to quickly find your way in large source distributions.Doxygen can also visualize the relations between the various elements by means of include dependency graphs, inheritance diagrams, and collaboration diagrams, which are all generated automatically.   
 - You can also use doxygen for creating normal documentation.

*NOTE*: 

Doxygen is developed under Mac OS X and Linux, but is set-up to be highly portable. As a result, it runs on most other Unix flavors as well. Furthermore, executables for Windows are available.For more informations about downloading and installing Doxygen, click [here](http://www.stack.nl/~dimitri/doxygen/manual/install.html)

So, what's the value to Doxygen?

Some of Doxygen's output is extracted from the semantics of the source programs. Other parts are from special comments you embed in your code. The entire process requires a special configuration file that specifies exactly what you want to do. Just as your development directory usually has a *makefile* that controls the build process, you also have a *Doxyfile* that contains the options used by Doxygen. This is simply a free-form text file that has options variables and their values. Doxygen automatically generates an example Doxyfile for you on request.

The source comments can use any of three formats:   
 - Special comments can mimic a Javadoc comment by using an extra asterisk in a multiline comment
 
 ```(/** A special comment */)```.
 - You can also use an exclamation point instead of the second asterisk 
  
 ``` (/*! Another special comment */)```.
 - Two or more single line comments ```(//)``` that have at least one extra slash or exclamation point following the comment marker also form a special comment.
 
Tags:

Special comments can contain Doxygen tags that let you specify particulars about your program. By default, comments refer to the next lexical element, for example:
```sh
   /***
     *@brief, which provides a brief description of the function.
     *@param, which identifies a single parameter to the function (you may have more than one param tag).
     *@return, which describes the function's return value.
     *@date, which describes the date of documentation
     *@todo
     */
```
For detailed informations about doxygen, please consult [the online doxygen documentation](http://www.stack.nl/~dimitri/doxygen/manual/index.html)


##MAKEFILES
Compiling your source code files can be tedious, especially when you want to include several source files and have to type the compiling command everytime you want to do it.Makefiles are special format files that together with the make utility will help you to auto-magically build and manage your projects.

It is recommended to create a new directory and place all the files in there before applying the make commands.

Creating a Makefile

A Makefile typically starts with some variable definitions which are then followed by a set of target entries for building specific targets (typically .o & executable files in C and C++, and .class files in Java) or executing a set of command associated with a target label.
The following is the generic target entry form :
```sh   
# comment
# (note: the <tab> in the command line is necessary for make to work) 
target:  dependency1 dependency2 ...
      <tab> command

for example:
#
# target entry to build program executable from program and mylib 
# object files 
#
program: program.o mylib.o
	gcc -o program program.o mylib.o
	```

Below is an example of a simple Makefile in c++ from the files named code.cpp,operation.cpp,main.cpp and operation.h :
```sh
all: operation code
operation: main.o operation.o
	g++ main.o operation.o -o operation 

main.o: main.cpp
	g++ -c main.cpp

operation.o: operation.cpp
	g++ -c operation.cpp

code: code.cpp
	g++ code.cpp -o code

clean:
	rm *o operation code
```

####The make utility

######If you run
```sh
   make
```

this program will look for a file named makefile in your directory, and then execute it.

If you have several makefiles, then you can execute them with the command:

```sh
make -f MyMakefile
```

There are several other switches to the make utility. For more info, ``` man make ```.
Visit [GNU make](http://www.gnu.org/software/make/manual/make.html)  
for more informations about makefile


