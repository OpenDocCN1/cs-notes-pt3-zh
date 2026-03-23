# 【阿尔伯塔大学】问题解决Python编程和电子游戏 ｜ Problem Solving, Python Programming, and Video Games p29 04_04_01_regression-testing-and-deleting-obsolete-tests -BV1N5rLBWE1c_p29-

![](img/a919552f2e3d6cd8b04f4534b2ae88a0_0.png)

Okay， you finished your second version description。If you look at the game creation diagram。

 you'll see that making a functional test plan is next。

Updating our test plan allows us to keep track of the progress of our game as we add functionality。

However， when we add a feature， we should retest all of the functionality implemented in the previous version that is still relevant in the current version。

This is called regression testing。We do regression testing since it is easy to unintentionally break existing code when we add new code。

For example， let's say I'm developing a phone app that allows me to edit pictures， sort them。

 and upload them to social media。In the first version。

 I create the functionality that allows me to edit the pictures。

 I test this feature in my first version test plan。In version 2， I upload pictures to social media。

 but I do not retest my picture editor。For version 3， I add the sort feature。

 I only test the sort feature。Unfortunately， when someone uses my app， the editor doesn't work。

Since I did not retest the editor after creating version 2 or3。

 I don't know which versions code broke the editor。To localize and fix the error。

 I need to check both the version 2 and version 3 code instead of only the code for a single version。

I discover that the upload feature in version 2 broke the editor。

If I had retested the version 1 editor feature in my version 2 test plan。

 it would have been easier to localize and fix the error。

I had converted the pictures to a new image format to make them easier to upload。

 but did not change the editor to handle this format。

Although I did not actually change the editor code。

 I caused an error to occur in that code when I added the upload code。To support regression testing。

 the functional tests from the previous version are already loaded into the function Test plan builder。

The first thing you must do when altering your test plan to accommodate the features of a new version is to eliminate any unnecessary tests。

 This is like deleting unnecessary concepts from a description。

For any version that requires you to permanently delete elements from a description。

 test plan or algorithm， you will complete a multiple choice activity that asks you to determine which elements to delete。

For a functional test plan， this includes tests that are no longer relevant。

 as well as tests that must be modified。Since all of the questions for your test plan are grouped into single blocks。

 any question block that does not contain exactly the right questions is considered incorrect and needs to be deleted。

For example， the current tests for the header do not contain any questions that relate to the color or the window position of the text。

However， the other tests， such as does the game display the header and does it indicate debug mode are still correct and needed。

Since you cannot delete individual questions， add missing questions or modify questions in a question block。

 this entire block needs to be deleted so that it is not shown in the questions panel of the builder。

 This is different than dragging a concept out of an assembly panel in a builder。

 dragging a concept out of the assembly panel， Re it to the left panel， rather than deleting it。

When you delete any concept in a multiple choice activity。

 it will not even appear in the respective builder。It is not relevant to the version of the game。

So you will not be able to use it during assembly。In the next two activities。

 you will delete the irrelevant question blocks and use the builder to create the second test plan。

Remember that you must test the new aspects of the window， including how it opens， clears and closes。

 and the new locations and visuals of the text in the window。



![](img/a919552f2e3d6cd8b04f4534b2ae88a0_2.png)