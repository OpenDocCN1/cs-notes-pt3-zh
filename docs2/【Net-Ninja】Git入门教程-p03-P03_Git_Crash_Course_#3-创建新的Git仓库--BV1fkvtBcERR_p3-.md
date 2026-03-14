# 【Net-Ninja】Git入门教程-p03-P03_Git_Crash_Course_#3-创建新的Git仓库--BV1fkvtBcERR_p3-

Alright then G in this lesson， we're going actually start working with Git。

 dive into what a Git repository is and also look at how we can initialize our very first one and I've actually already got open the data project inside Vs code。

 which is what we're going to be working with for the majority of this course。 But anyway。

 what exactly is a Git repository。 Well you can think of a repository as a container around your project that tracks the complete history of everything inside that project and all the changes made within it and this repository tracks everything who made the changes when they made them and why they made them it's basically like having a massive diary for your project。

 but one that can bring back all versions of your files if you need them So if you made a change to your CSs file last week and you committed that change then Git will store that revision of your project it would be almost like taking a snapshot of your code at that moment in time and saving that snapshot。

 then if you changed some other files again a few days later and committed those changes as well。😊。



![](img/26c587382d28fd86da09c57ea36edc42_1.png)

Then Git will have both versions or both snapshots stored away safely and you can go back to the previous version if you ever needed to。

😊，by the way， you will hear me say the word commit or committed every so often this is a Git term and right now it basically means we're saving a version if you like but we're going to talk about commits a little bit later but anyway this is like having unlimited save slots in a video gimma guess where you can always go back to an ill point if you mess something up Now you might be thinking well if a Git repository stores every single committed version of a project on your computer is it not going to take up a huge amount of space and the answer is no because the way Git stores versions is really clever and instead of storing multiple versions of the entire project it only stores the differences between versions the part of the files that change so if we're winding back all Git needs to do is remove those changes。

😊，Anyway， if we want to start using Git within a project we need to make a new repository for that project and to do that we can use the git in command within the root of this project so make sure you're in the correct folder here when you run this and by default in the VS code terminal you should already be in the root directory of your project but remember if not you can change directory using the CD command that we've already seen。

So when we run this command， we're essentially telling it to start keeping track of everything that happens in this project and GiRes by creating a hidden dotgit folder inside the root of this project now I can demo that by using the LS command with the A flag to show all files including hidden ones and we should see that dotgit folder So。

This dot git folder is where Git stores all the history。

 all the different versions and all the metadata about the project。

 you never need to go inside that folder yourself， Git handles all of this forest。

 but it's good to know it's there because that's what makes a regular project into a Git repository。

😊，If you ever delete that Git folder， by the way， you're going to lose all of your version history。

 so try not to accidentally do that。😊，You'll probably also notice that when I initialized a git repo in this folder all the files and folders inside it turned green right this is a VS code feature which integrates well with Git and it automatically detect any untracked changes or new files added to a repo then highlights those files in the file tree in this case through all green because none of them are being tracked by Git yet So this is something important to understand even though we have those files in our repo Git isn't automatically tracking them to begin with we need to explicitly tell Git which files we want it to track and we'll learn how to do that later but for now let's just understand what we've done so far we've taken a regular project folder and transformed it into a git repository by running Git in it and by the way from now on you might hear me refer to a repo in fact I've already done that I think several times which is just short for repository and our ten switch between the two words anyway that repo now has the potential to track every change。

We make to our project Now the files we've created inside this repo are sitting in what Git calls the working directory and right now those files are on track which means Git knows they exist。

 but it's not paying much attention to them So the working directory is where you edit your files write your code and make your changes the repository itself that hitting dot git folder is where Git stores all the history and the versions of the project and then there's actually a third area in between called the staging area which we're going to talk about in the next lesson。



![](img/26c587382d28fd86da09c57ea36edc42_3.png)