---
layout: post
title:  "The 5 minute blog tutorial..."
date:   2020-10-11 
---
So, you want to create a blog and express your ideas with the world.. and you don't know how to begin. Read how to make a quick 5-minute blog, from free hosting and domain to a free SSL certificate for a lifetime, here!

If you're lazy, like me, or you don't like to code, but would like to have your own blog that has exceptionally fast loading speeds and is easy to setup, you're reading the most easiest blog setup tutorial you'll ever see. Now now, I don't technically hate services like wordpress.com or one of those site builders such as wix, but I have found in general usage that I just don't like having a lot of URLs for things I use, and I rather prefer a static site generator such as Jekyll/Hugo or Gatsby because I prefer my sites FAST.

I'll not explain what static site generator is in this post, but this blogpost is basically a quick start guide to running your own blog as fast as humanely possible. So let's get started, shall we?

- #### Step 1 : Get a GitHub Account :
    If you don't already have a GitHub account, sign up for one [here](https://www.github.com/)
- #### Step 2 : Set up the developer environment
    - We will be using Jekyll SSG for this tutorial. Follow the developer environment setup guide [here](https://jekyllrb.com/docs/installation/)
    - Download Git [here](https://git-scm.com/)
- #### Step 3 : Download the quick-start repository :
    Now, if you want to create your blog like mine, with a Minima-Dark theme and everything, download the repository [here](https://github.com/netizener/thelocalhost). Otherwise, if you'd like to use the default Jekyll blog, with Minima light theme, open up a terminal and paste the following code : 
    ```bash
    gem install jekyll bundler
    jekyll new myblog
    cd myblog
    bundle exec jekyll serve
    ```
- #### Step 4 : Viewing the blogsite :
    Open up your favorite web browser and follow the link `http://localhost:4000/` to watch the website in action
- #### Step 5 : Adding/Removing new posts :
    All your posts and stored in the `_posts` directory. Use the format `YYYY-MM-DD-TITLE.md` to create new posts.
- #### Step 6 : Customizing the blogsite :
    Your blogsite can be customized from the `_config.yml` file. If you downloaded [my quick start repository](https://github.com/netizener/thelocalhost), you can read how to customize the blogsite by reading the [customization guide](https://github.com/netizener/thelocalhost/tree/main#customizing-the-blog-)
- #### Step 7 : Deploying the blogsite :
    - Delete the `.git` folder inside the repository
    - Create a new repository on GitHub with `yourusername.github.io` where `yourusername` is your GitHub username
    - Fire up a terminal in the current project directory and follow the following commands (make sure you have Git installed):
        ```bash
        git 
        git init
        git add .
        git commit -m "first commit"
        git branch -M main
        git remote add origin git@github.com:yourusername/yourusername.github.io.git
        git push -u origin main
        ```
    - Let the upload finish. Meanwhile open up your repository's settings and change `Source` under `GitHub Pages` to `master`. Wait for 5-10 minutes for the first publish of the blogsite to finish, and then visit your blogsite at `yourusername.github.io`

#### Happy Blogging!
