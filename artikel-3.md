# How To: Maintain Structure In Projects

Sooner or later, as a web developer you will probably work together on projects. In this article I discuss tools that can help you maintain structure in these projects. I wrote this article based on my personal experience. Of course there are many other ways to keep structure.

### Version control with Git and Github

You can use Git to maintain structure in a project. “Git is a [free and open source](https://git-scm.com/about/free-and-open-source) distributed version control system designed to handle everything from small to very large projects with speed and efficiency.” (Git, n.d.). Version control helps to keep track of the work your team did and helps to easily explore the changes that are made by others. Git is very flexible, so people can and will work in many different ways. It is therefore very important to make clear agreements as soon as you work with several people within a repository.

**Git commit**
Once you have changed and saved your files, you need to **commit** them. By committing your files, the changes will be saved as a version of the repository. Each commit must be made with a message that describes the change(s) that are made over time. It’s best to be **detailed**. This will be helpful when reviewing the commits later on.

**Branches**
Branches are used to develop features isolated from each other. The master branch (or however you want to name it) is the "default" branch when you create a repository. It’s important to assume that the master branch is always ready to be deployed. Use separate branches for experimentations and changes and merge them back to the master branch upon once you're ready.

I prefer to always work from the `development` branch. From there I create new branches for every change I want to make. When I'm done, I merge that branche with the `development` branche. Once I'm really sure that everything on `development` is stable, I merge development with the `master` branch. It is important to give a branch a clear name. And to divide it into different categories.

What I use often is:

1. `feature/*feature-name` when I start working on a new feature.

You could also use create separate branches for fixing bugs or when you quickly want to change something small:

2. `bug/bug-name` for fixing bus.

3. `hotfix/hotfix-name` for a hotfix.

Inspired by this [article](https://gist.github.com/digitaljhelms/4287848) by Jeremy Helms.

**Protect the master branch**
In some cases it's important to protect your (master)branch(es). When you use git together with GitHub, you can customize branch protections in the repository and enforce certain workflows. (GitHub, n.d.). When you protect a branch, you can ensure that other collaborators on the repository cannot make irreversible changes to that branch, for example deleting the development branch (~~guilty~~). To merge changes with a protected branch, you create a pull request and let that pull request be reviewed (by multiple people.)

### **Useful Tools In Combination with Git**

**Fork**

Fork is an open-source git client for Mac and Windows. It allows you to quickly navigate trough different repositories and organize your workflow efficiently. Fork displays your commits and branches in a clear way.

[Fork - a fast and friendly git client for Mac and Windows](https://git-fork.com/)

**GitHub**

GitHub is a website that provides hosting for software development version control using Git. It offers all of Git's version control functionalities as well as some of its own features.

[GitHub - Build software better, together](https://github.com/)

### File structure

Another way to keep structure in your project is by organizing your folders and files in a logic way. Make agreements about this as soon as you start a project. Consider, for example, a naming convention for file and folder names. It takes much more time to add structure when you're already halfway trough a project than when you start with it right from the start.

The file structure really depends on what kind of project you work. That is why I mainly want to talk about CSS and JavaScript files.

**BEM Approach**
For large, but certainly also for small projects, the BEM Methodology is a very useful method to apply. BEM helps you to to create extendable and reusable components. Besides that, BEM helps you to keep an overview in your files and ensures that merge conflicts occur less. The BEM methodology has several approaches to organizing the project's file system. It doesn't matter much which method you or your team chooses, as long as you are consistent. What I like about the organizing the files in one of BEM's approaches is that you will always find files easily. I prefer my file structure to look like this:

```
    project
        common.blocks/
            input/            # Directory for the input block
                input.css     # CSS implementation of the input block
                input.js      # JavaScript implementation of the input block
            popup/            # Directory for the popup block
                popup.css     # CSS implementation of the popup block
                popup.js      # JavaScript implementation of the popup block
```

> Source: [https://en.bem.info/methodology/filestructure/](https://en.bem.info/methodology/filestructure/)

See: [https://en.bem.info/methodology/filestructure/](https://en.bem.info/methodology/filestructure/) for other approaches.

I like to give a separate class name to elements that I influence in javascript. If someone else want's to update an element or that class name, they notice that changing this class has an effect on something in the javascript file.

```html
<p class="paragraph js-paragraph">text</p>
```

### Communication

In addition to making these agreements at the start of the project, it is also important to keep communicating during. During a project you will come across things that affect certain things in your project. Discussing this is important.

### Sources

GIT. (n.d.). About - Git. Retrieved 18 December 2019, from [https://git-scm.com/about](https://git-scm.com/about)

GitHub. (n.d.). [GitHub.com](http://github.com/) Help Documentation - GitHub Help. Retrieved 23 November 2019, from [https://help.github.com/en/github](https://help.github.com/en/github)
