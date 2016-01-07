---
title: "Going live with Github Pages"
slug: github-pages
---     

#What is Github Pages - a quick recap
You probably already know Github, which is a web-based Git repository hosting service. It is great for version control and if you have a free account, it allows you to show off your code through public repositories. If you pay for Github, you can also have private repositories. [Github Pages](https://pages.github.com/) is basically Github and a website hosting service rolled into one. It allows you to have a normal repository and as soon as you push any changes to your repo, they will be published live. That is the perfect setup for our little portfolio site.

We need to create a repo now and name it your_github_username.github.io, which will automatically make it accessible through the URL *your_github_username.github.io*. So let's go ahead and do this together.

#Creating a Github repo
Go to [Github](https://github.com) and login if you have an account. If you don't have an account, sign up for Github. It is a very useful account to have. 

Once you're logged in, we will create a new repository.

> [action]
> Click on the green "New repository" button. 
>  
> ![Create new repo](./1-new-repo.png "Create new repo")

<!-- Comment to break actionable boxes. -->

> [action]
> Name the repository *your_github_username.github.io*. Give it a meaningful description and click the "Create repository" button. **It's important to use your Github username and add the github.io, otherwise it won't work!**
> 
> ![Name new repo](./2-name-repo.png "Name new repo")

Now that we have created a new repository, we need to pull this repository down onto our local machine.

> [action]
> Open your terminal and navigate to the directory where you already have your portfolio folder. Type the following command:
> 
> `git clone https://github.com/your_github_username/your_github_username.github.io.git`
> 
> Hit enter and the repository will download. 

<!-- Comment to break actionable boxes. -->

> [info]
> **Git clone doesn't work**
> 
> If you have never used git before, you might need to [download it first](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and install it.

Go to the directory that contains your new repo and the portfolio folder in **Finder**. 

> [action]
> Move your portfolio folder inside the new repo folder.

#Pushing to Github
Go back to your terminal and navigate to your new repo. You can change directories by using the `cd your_repo_name` command. Commit all your files by doing the following steps:
>
> - `git status` - this will show you all files that are new or changed
> - `git add .` - this will add all the files
> - `git commit -m 'initial commit'` - this will create the first commit and give it a meaningful message, that you can refer to later
> - `git push origin HEAD` - this pushes all of the code in your commit up to Github

When you hit enter on the last command, you will be prompted to enter your Github username and Github password before the files will be pushed up.

Now that we have all of our files up on Github, all we need to do is go to our URL **your_github_username.github.io** and look at our brand new portfolio website! We are almost done now but we still need to activate the Formspree service. 

> [action]
> Go to our form on the **Contact Me** page and submit your first email. Once you have clicked "Send", you need to go to your email account where you should have received an email from Formspree asking you to confirm that you want in fact receive emails from this form. 

![Formspree confirmation email](./3-confirm-email.png "Formspree confirmation email")

Once you have accepted the email, you are all set! 

![Formspree confirmation in browser](./4-confirmed.png "Formspree confirmation in browser")

Well done for creating your own portfolio using HTML, CSS3 and JavaScript. You've pushed your website live and it is now accessible with its own URL, which you can share with anyone you'd like or put it on your CV for prospective employers.
